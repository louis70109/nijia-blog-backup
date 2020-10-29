---
title: 'LINE 開發社群計畫: 2020 LINE 平台九、十月更新整理'
categories: 學習紀錄
date: 2020-10-29 21:45:59
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

![](https://nijialin.com/images/1.png)

# 前言

大家好，我是 LINE Taiwan 的 Tech Evangelist - Evan Lin。這次很開心受到 chatbot 社群的邀請，參加了 "[Chatbot meetup 聊天機器人新手小聚 24 @ Gandi](https://chatbots.kktix.cc/events/meetup-024)" 的聚會活動，並且分享 LINE API 更新與個人開發的心得。在此也跟各位分享本次參與的心得，並且也希望透過社群分享的力量能夠讓聊天機器人的開發動能更加的盛大。

- 社群 Chatbots Meetup： [https://chatbots.kktix.cc/](https://chatbots.kktix.cc/)
- 本次活動網頁: [活動網址](https://chatbots.kktix.cc/events/meetup-024)
- 本次活動的共筆紀錄： [https://hackmd.io/@chatbot-tw/meetups-024](https://hackmd.io/@chatbot-tw/meetups-024)

由於 Chatbots Meetup 本身屬於社群自主性的活動，所有內容也是相當的難得與有趣。也希望能夠透過本篇文章讓大家稍微了解 Chatbots Meetup 社群的魅力，讓更多朋友了解到打造自己的聊天機器人是如此讓人開心的事情。

<!-- more -->

### 整場影片分享

<iframe width="560" height="315" src="https://www.youtube.com/embed/n5LZlcQosGw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# LINE Platform Update 2020/10

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZFPN5inMtM8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

在九月與十月這兩個月中釋出了許多資訊，以下就一一帶大家了解一下究竟釋出了什麼新的強大 API 吧！

## LIFF 釋出 v.2.4.1

### Open another LIFF page would be checked at LIFF

### fix called twice

## 管理 LINE Bot 相關資訊

開發者們在建立 LINE bot 時大多都是從 [LINE Developer Console](https://developers.line.biz/zh-hant/) 裡去設定相關參數，使用情境大多像是開發者在開發 Chatbot 時都會使用 ngrok 之類的服務建立一個暫時性 Domain，抑或是版本升級需要改網域(址)名稱，不管是哪種用途，最終需要都確認的 Bot 資訊、更改 Webhook 網址、測試 Webhook 網址是否有效，這次的更新一次釋出許多相關資訊的 API，詳細請參考下方。

### Get bot info

<script async class="speakerdeck-embed" data-slide="7" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

若開發者因為開發不同環境的 Chatbot 時需要管理前，一定需要取得相關資訊在 UI 上才有辦法管控，大家可使用[此 API](https://developers.line.biz/en/reference/messaging-api/#get-bot-info) 取得相關資訊。

### Webhook Settings

這個 API 是許多開發者敲碗許久的功能，大家請參考以下說明：

<script async class="speakerdeck-embed" data-slide="8" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

- [GET Webhook URL](https://developers.line.biz/en/reference/messaging-api/#get-webhook-endpoint-information)
  - 取得當前 Webhook 的網址，可得知當前 Chatbot 所設定之 URL。
- [Set Webhook URL](https://developers.line.biz/en/reference/messaging-api/#set-webhook-endpoint-url)
  - 透過此 API 可以使用 `PUT` 來更新 Chatbot 的 Webhook URL，可透過前一個 API 先取得網址確認後再使用此 API 來更新。
- [Verify(Test) URL](https://developers.line.biz/en/reference/messaging-api/#test-webhook-endpoint)
  - 不管 `GET` 或 `PUT`，都需要確認當前的 URL 是否真的可行，透過此 API 即可 Verify 你的 Webhook URL。

三個 API 皆是基於 `CHANNEL_ACCESS_TOKEN` 做相關使用，大家再使用時務必確認是否有使用到對應的 Token 喔！

## TLS migration

<script async class="speakerdeck-embed" data-slide="18" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

在接下來的日子裡，LINE 將會開始支援 `TLS1.3`，並且開始停止支援 `TLS1.1` 以及 `TLS1.0`。HTTP 版本的部分也會開始支援 `HTTP/2`，讓開發者們的服務可以建構在更快、更安全的協定上。

這邊就會有個問題產生，那我該如何測試才知道我的主機有沒有支援到呢？答案就是使用 Webhook 的 [Verify(Test) API](https://developers.line.biz/en/reference/messaging-api/#test-webhook-endpoint) 即可得知當前服務是否支援協定，而只要收到 Http 狀態碼(status code) 是 `200` 即是成功，而 Body 內容則如下方投影片所示。

<script async class="speakerdeck-embed" data-slide="20" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

> 轉換時間 2020/10~2021/01，有使用到 LINE 服務的大家要注意時間，記得 migration！

## Flex Message Update 2

### Carousel count 10 -> 12

### flex box

<script async class="speakerdeck-embed" data-slide="24" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

既然使用 `flex` 這個名詞，勢必得加入更多支援讓 Flex Message 更像瀏覽器上的 Flexbox，
`justifyContent`
`alignItems`

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
