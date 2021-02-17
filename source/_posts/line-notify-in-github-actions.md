---
title: 於 GitHub Actions 市集中建立 LINE Notify 套件
tags:
  - LINE
  - LINE Notify
  - GitHub
  - GitHub Actions
categories: GitHub
date: 2021-02-17 17:51:55
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

![](https://nijialin.com/images/2021/action/action.png)

# 前言

在上一篇[【Python】在 GitHub Actions 上建立自動測試並打包至 PyPi](https://nijialin.com/2021/02/11/how-to-use-github-action/) 最後提到要串接通知型服務，畢竟在任何使用情境下執行完畢(自動測試、部署、上版...)，都一定要藉由通知服務來了解專案 CI 執行狀態。

在台灣訊息入口首選一定是使用大家都有的 LINE，而若只是單純要接收訊息的話，則使用單向型推播型服務的 LINE Notify，它提供了 **文字**、**貼圖**、**圖片**(包含網址與檔案) 的訊息推送方式，常用情境 **天氣通知**、**服務健康狀態**、**GitHub Event** 等等(可[參考官網](https://notify-bot.line.me/zh_TW/))，既然當中提到應用於 GitHub Event，那本篇當然也要將 LINE Notify 的應用情境整合進為 GitHub Actions，讓讀者們的專案執行完的狀態透過 LINE Notify 通知！

<!-- more -->

## 取得 LINE Notify 的 access_token

1. 使用筆者過往寫過的專案 - [louis70109/flask-line-notify](https://github.com/louis70109/flask-line-notify) 當中文件的**一鍵部署**，將專案直接部署於 Heroku 上，當然讀者們也可以參考說明文件將之於本地端建立。

2. 接著將 LINE Notify 當中申請的三個參數放入環境變數中才能讓服務執行

```
LINE_NOTIFY_CLIENT_ID
LINE_NOTIFY_CLIENT_SECRET
LINE_NOTIFY_REDIRECT_URI
```

3. 進入剛剛部署完的 Heroku 網址(https://YOUR_HEROKU_URL/)，透過點選畫面上的按鈕即可綁定 LINE Notify，結果如附圖，並將 **access_token** 複製起來。

![](https://nijialin.com/images/2021/line-notify-github-actions/1.png)

4. 將 **access_token** 貼至*第三個紅箭頭處*，並將變數名稱命名為 **LINE_NOTIFY_TOKEN**。

![](https://nijialin.com/images/2021/action/env1.png)

# GitHub Actions 套件運作流程

可以使用[三種模式](https://docs.github.com/en/actions/creating-actions/about-actions#types-of-actions)建立，分別為 Docker、JavaScript、Composite run steps(把 Bash 寫在 yaml 裡)，本篇則使用 Docker 做範例。

既然是第一次使用，就參考[官方文件](https://docs.github.com/en/actions/creating-actions/creating-a-docker-container-action#creating-a-dockerfile)開始整個建立流程(Action)，依照文件上的敘述，我們需要 **Dockerfile**、**entrypoint.sh** 以及 **action.yml** 三個檔案。

## Dockerfile

<script src="https://gist.github.com/louis70109/b37ac87d91ed033769bfa8c18c5827b0.js"></script>

- 引入 Python3.7 映像檔
- 將相依套件的 requirements.txt 複製進去容器內並執行安裝
- 將入口檔案 entrypoint.sh 以及主要執行 LINE Notify 的檔案 line_notify.py 複製進去容器內
- 設定 entrypoint.sh 為 ENTRYPOINT

## line_notify.py

<script src="https://gist.github.com/louis70109/b1f59762d4cc6378351f2daf393838ea.js"></script>

在 **9~14** 行中主要是設定在終端機(Command Line)上執行的參數名稱，接著的運作部分則是使用過往筆者寫的套件 - [lotify](https://github.com/louis70109/lotify) 來執行。

> 註：image_file 需要給指定路徑才會幫忙開檔案。

## entrypoint.sh

<script src="https://gist.github.com/louis70109/2e20d6172a31376fb82f0fb5f45a196e.js"></script>

GitHub Actions 中預設會將輸入的參數加上 **INPUT\_** 的前綴(prefix)符號，因此在上述的參數中將 Actions 環境參數轉譯成 line_notify.py 看得懂的參數。

> 可以查看這頁最下面的 [Actions example](https://docs.github.com/en/actions/creating-actions/creating-a-docker-container-action)，在 Docker 環境中會使用 -e INPUT_xxx 來放入參數。

## action.yml

<script src="https://gist.github.com/louis70109/3145a52355236017d5510e0c1fd7a509.js"></script>

- name: 在 Marketplace 上搜尋的名稱
- input: 所有會使用到的參數
- runs: 三種模式選一種執行，這邊我選擇使用 Docker。

# 如何上 Marketplace

參考[line-notify-action](https://github.com/louis70109/line-notify-action)，在建立上述必要的檔案後，需要下 Release Note 才後就會被自動上架到 GitHub Actions Marketplace(市集)，若不清楚怎麼手動加入可以參考[這個環節](https://nijialin.com/2021/02/11/how-to-use-github-action/#Testing)，抑或是透過 [Command Line 的方式](https://git-scm.com/book/en/v2/Git-Basics-Tagging)也行。

# 如何使用在 GitHub 專案上

<script src="https://gist.github.com/louis70109/05edb76a3556e0ea7d67a5f2057251f5.js"></script>

若你第一次使用 Actions，可以參考上方 Gist，在 **.github/workflow/** 資料夾下建立一個 **ci.yml** 並放入之。

在 Gist 中設定是 Git push 時觸發，要測試時可先修改 README 來觸發看看。

可參考 [line-notify-action 的範例 yaml](https://github.com/louis70109/line-notify-action/blob/master/.github/workflows/ci.yml)

> 讀者可能會注意到範例 yaml 當中是使用 **uses: ./** 的方式，是因為在自身專案底下僅需使用 ./ 即可引入。

若已經使用過，在 Marketplace 上[看到此專案](https://github.com/marketplace/actions/line-notify-actions)旁按鈕後按下後會告知如何引入。

![](https://nijialin.com/images/2021/line-notify-github-actions/2.png)

## 行前說明

- \$\{\{ \}\} 為 GitHub Actions 取得參數的用法
  - **secrets.ＯＯＯ** 為分頁(tab) Setting ➡️ Secrets 裡所設定的參數(ＯＯＯ為參數名稱)
  - **github.** 為預設的環境變數，相關參數使用請[參考官方文件](https://docs.github.com/en/actions/reference/environment-variables#default-environment-variables)
- 需設定 **LINE_NOTIFY_TOKEN** 於 Secrets

## 僅送純文字

```yaml
- name: LINE Notify Message
  uses: louis70109/line-notify-action@master
  with:
    token: ${{ secrets.LINE_NOTIFY_TOKEN }}
    message: 'LINE Notify test message'
```

## 文字+貼圖

```yaml
- name: LINE Notify Message
  uses: louis70109/line-notify-action@master
  with:
    token: ${{ secrets.LINE_NOTIFY_TOKEN }}
    sticker_id: 1
    package_id: 1
```

## 文字+圖片(透過網址方式)

```yaml
- name: send image url message
  uses: louis70109/line-notify-action@master
  with:
    token: ${{ secrets.LINE_NOTIFY_TOKEN }}
    message: |
      ${{github.repository}} send image test.
    image_url: 'https://raw.githubusercontent.com/louis70109/line-notify-action/master/tests/image1.png'
```

## 文字+圖片(本地端路徑)

```yaml
- name: send image file message
  uses: louis70109/line-notify-action@master
  with:
    token: ${{ secrets.LINE_NOTIFY_TOKEN }}
    message: |
      ${{github.repository}} send image file.
    image_file: tests/sally.png
```

- image_file 為路徑，以[本專案](https://github.com/louis70109/line-notify-action)為例則是在 **tests 資料夾**下的 **sally.png** 圖片。

# 結論

在過年前寫了[【Python】在 GitHub Actions 上建立自動測試並打包至 PyPi](https://nijialin.com/2021/02/11/how-to-use-github-action/)，讓我自己寫的專案可以自動化推上 PyPi(成就感十足)，並設定了此篇為過年期間的寒假作業，讓自己對於 GitHub Actions 的操作與流程更加熟悉，希望透過[上一篇](https://nijialin.com/2021/02/11/how-to-use-github-action/)與此篇可以讓讀者們可以更加熟悉 GitHub Actions 這套工具，透過熟悉它也能讓讀者們未來在使用其他工具時更加快上手喔！

- 使用上也要注意自己的使用狀態，雖然是免費的服務但也別超過人家提供的上限喔！([參考網址](https://docs.github.com/en/actions/reference/usage-limits-billing-and-administration#usage-limits))
  ![](https://nijialin.com/images/2021/line-notify-github-actions/limit.png)

- 或許會需要定期執行**部署**或**測試**，可以參考[GitHub 排程頁面](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#scheduled-events)
