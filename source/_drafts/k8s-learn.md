---
title: 【標題】題目
categories: 學習紀錄
tags:
---

<style>
  section.compact {
    font-size: 150%  
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
</style>

![](https://nijialin.com/images/2021/)

# 前言

```puml
@startuml
User->Chatbot: 發送訊息
Chatbot->Mac: Webhook 通知主機
Mac->Docker: 進入容器服務
Docker->k3d: 轉打到 k3d 叢集

k3d->forward.yml: 將請求交給 proxy
forward.yml->bot_service.yml: Proxy 轉交請求給 Bot
bot_service.yml->API: 進入 API 環節
note over k3d, API #FFAAAA: 叢集(Cluster)

API-->User: 完成請求並逐步回應
@enduml
```

- Kubernetes’ default NodePort range is **30000-32767**.
  - [Reference](https://k3d.io/usage/guides/exposing_services/)

範例專案：[louis70109/kubernetes-line-echo-bot](https://github.com/louis70109/kubernetes-line-echo-bot)

<!-- more -->

# 建立容器

首先要先進入 [echo-bot-python](https://github.com/louis70109/kubernetes-line-echo-bot/tree/master/echo-bot-python) 資料夾中，在建立前可以先測試這個範例是否正常運作，這隻機器人只是一隻基本回話的 Chatbot：

```bash
cd echo-bot-python/
pip install -r requirements.txt
cp .env.example .env # 加入 LINE_CHANNEL_SECRET, LINE_CHANNEL_ACCESS_TOKEN 兩把鑰匙
python api.py
```

> - 請至 [LINE Developer Console](https://developers.line.biz/console/) 建立 Chatbot
> - LINE Chatbot 建立流程參考於 [Chatbot Taichung 工作坊的文章](https://nijialin.com/2020/08/27/chatbot-taichung-08/#Massaging-API)

為求方便與練習，這邊使用 Docker Hub 作為 Kubernetes 的容器使用平台，接著請先至 [Docker Hub](https://hub.docker.com/) 註冊帳號並下載 [Docker](https://docs.docker.com/get-docker/)。

```bash
docker login # 登入
docker build . -t="帳號/line-echo-bot-python"  # 將中文改成你 Docker Hub 的帳號
docker push  # 推上 Docker Hub
```

第二段意思是在**當前位置**建立一個 `帳號/line-echo-bot-python` 的標籤，因為在上半部測試 Chatbot 時已經在 **echo-bot-python/** 資料夾下，若不知道位置可使用 `pwd` 來查當前位置。

若建立上還是有問題，可以使用我已經有建立好了的 [Echo-Bot-Container](https://hub.docker.com/repository/docker/louis70109/line-echo-bot-python)。

> 補充: Docker 是 Container 的一個解決方案，Container 不等於 Docker

<iframe width="560" height="315" src="https://www.youtube.com/embed/nc3mBN3LzvM" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# 練習開始

日常工作中，上半部的工作可能會更加複雜，而若只是練習許多人會直接使用 [Nginx](https://hub.docker.com/_/nginx) 來測試也是沒問題的，那麼接下來就開始使用 [k3d](https://k3d.io/) 來練習囉！

k3d 是什麼呢？它是將 [k3s](https://github.com/k3s-io/k3s) 這個輕量化(Lightweight) Kubernetes 打包成 Docker Image，讓不同平台的 Docker 用戶可以在 Docker 上操作 Kubernetes，當然也有很多不同的服務可以支援，這邊就不贅述。

## 1. 安裝 k3d ([其他安裝方式](https://k3d.io/#installation)) 與 kubectl ([其他](https://kubernetes.io/docs/tasks/tools/install-kubectl/)) 於 Mac

```
brew install k3d
brew install kubectl

kubectl version --client
```

> kubectl 是 kubernetes 操作叢集(cluster)的的指令集

## 2. 建立叢集(cluster)，將 **mycluster** 改成你想要的名字

```
k3d cluster create mycluster --agents 1 -p '8082:30080@agent[0]'
```

-p 的意思是將本機(Mac)的 8082 port 轉到 Docker 裡的 Kubernetes 環境中的 30080 port

> 按造過往經驗， Mac 在這裡會是代表像是 Linux 中的 iptable(防火牆)，也就是最後一到對外關卡，因此才需要挖通道讓 Mac 與 Docker 中的 kubernetes 互通。

## 3. 將 chatbot(bot_service.yml) 部署到 cluster 中

修改以 clone 下來的[專案](https://github.com/louis70109/kubernetes-line-echo-bot/blob/master/bot_service.yml)，開啟 **bot_service.yml** 後先把上述建立好並推上 DockerHub 的容器貼在 **image** 欄位，並將剛剛建立的 LINE Chatbot key **env 參數**中:

- 容器對外是 8000 port
- 每個像這樣會被部署的服務皆會稱為 Deployment

```yaml
containers:
  - name: bot-service
    image: 帳號/line-echo-bot-python:latest
    ports:
      - containerPort: 8000
    env:
      - name: LINE_CHANNEL_SECRET
        value: '剛剛設定的 SECRET'
      - name: LINE_CHANNEL_ACCESS_TOKEN
        value: '剛剛設定的 TOKEN'
```

將 bot_service.yml 部署上 kubernetes(k3d)

```
kubectl apply -f bot_service.yml
```

## 4. 進入 [forward.yml](https://github.com/louis70109/kubernetes-line-echo-bot) 介接 kubernetes(k3d) 與 Deployment(chatbot) 的 port

做到這邊狀態現在整體狀態應該會如下：

```puml
@startuml
Mac->k3d: 8082 port 對應 30080 port
Deployment<-Chatbot: 將 8000 port 對外
note over k3d, Deployment #FFAAAA: 缺少 middleware 幫忙介接
@enduml
```

看到檔案 - [forward.yml](https://github.com/louis70109/kubernetes-line-echo-bot) 中的以下欄位：

```yaml
ports:
  - name: 'bot-svc'
    nodePort: 30080
    port: 8000
    protocol: TCP
    targetPort: 8000
```

- [文件上](https://k3d.io/usage/guides/exposing_services/#2-via-nodeport)有提到 Kubernetes 預設的 NodePort 範圍為**30000-32767**，因此上述則被設定在 **30080**(範圍中)
- port 與 targetPort 則是 Deployment(chatbot) 的對外 port

知道動作後，接著就把它放上 kubernetes 吧！

```bash
kebectl apply -f forward.yml
```

如此一來就用 forward.yml 這個 deployment 介接完成啦！

```puml
@startuml
Mac->k3d: Request OOO
k3d->forward.yml: 幫我告訴它我要的 OOO
forward.yml->Deployment: k3d 說要 OOO
Deployment->Chatbot: 請給我 OOO
Chatbot-> Deployment: 好了這是它要的 OOO
forward.yml<-Deployment: 這是 k3d 要的 OOO
forward.yml->k3d: 給你 OOO
k3d->Mac: Response OOO
note over Mac, k3d #FFAAAA: 8082 port 對應 30080 port
note over Deployment, Chatbot #FFAAAA: 將 8000 port 對外
@enduml
```

## 5. 測試

我有做一個 root 路由是來測試用的，直接在瀏覽器上輸入 `localhost:8082/` 看有沒有出現 World 的字串，若有出現代表待會測試 chatbot 理論上也是會成功的。

## 6. 測試 Chatbot 有沒有 Echo

由於我是在 Mac 上執行，為求方便我使用 ngrok 來建立暫時含有 SSL 的網址，並把網址複製到剛剛於 [LINE Developer Console](https://developers.line.biz/console/) 建立的 Chatbot 當中的 endpoint 欄位，接著就到剛剛的 Chatbot 上開始跟它聊天吧！

# 結論
