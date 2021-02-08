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

- Kubernetes’ default NodePort range is **30000-32767**.
  - [Reference](https://k3d.io/usage/guides/exposing_services/)

```
k3d cluster create mycluster --agents 1 -p '8082:30080@agent[0]'
```

```yaml
apiVersion: v1
kind: Service
metadata:
  labels:
    app: nginx-aaa
  name: nginx-svc
spec:
  ports:
    - name: 80-80
      nodePort: 30080
      port: 80
      protocol: TCP
      targetPort: 80
  selector:
    app: nginx-aaa
  type: NodePort
```

官方 nginx sample: kubectl apply -f https://raw.githubusercontent.com/kubernetes/website/master/content/en/examples/controllers/nginx-deployment.yaml
load file: kubectl apply -f https://raw.githubusercontent.com/minghsu0107/kubernetes-note/main/k8s-basic/pod/node-port-svc.yaml\?token\=AL6FFRHIPZ7ZIUT2SWHN56LAE3N5U

<!-- more -->

# 介紹

# 結論

# 活動小結

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：@line_tw_dev
![](https://www.evanlin.com/images/2020/line-tw-dev-qr.png)

# 關於「LINE 開發社群計畫」

LINE 今年年初在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來察看最新的狀況。詳情請看:

- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
- [2021 年 LINE 開發社群計畫活動時程表 (持續更新)](https://engineering.linecorp.com/zh-hant/blog/2021-line-tw-devrel/)
