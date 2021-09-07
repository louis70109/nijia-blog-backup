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

![](https://nijialin.com/images/2021/line-chatbot-workshop/1.png)

# 前言

<!-- more -->

# 介紹


## 訊息格式

<script async class="speakerdeck-embed" data-slide="6" data-id="0ec99040fbed4ad592fcf1c40dfa1f4e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

大家日常在 LINE 上會與許多官方帳號互動，互動時是不是會覺得許多官方帳號都會發送各式各樣的訊息格式，以下為各位介紹一下並帶上一些說明：

### [Text message](https://developers.line.biz/en/docs/messaging-api/message-types/#text-messages)

在一開始與聊天機器人串接時，最先使用的一定是文字訊息，而文字訊息好處就是易用、易讀且是結構化資料，大多用戶也都會透過文字來互動(查資料、註冊...)，往後若以串結人工智慧的技術，也可以針對意圖去了解用戶需求。

<script async class="speakerdeck-embed" data-slide="10" data-id="0ec99040fbed4ad592fcf1c40dfa1f4e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

而身為每個聊天機器人背後小編們(就是你跟我)，我們時常需要把文字弄的票票亮亮，讓文字更吸睛，因此這裡就會加上 Emoji 來美化我們每一則回應的訊息，更多清單可以[參考官方網站](https://developers.line.biz/en/docs/messaging-api/emoji-list/#line-emoji-definitions)。

### [Sticker message](https://developers.line.biz/en/docs/messaging-api/message-types/#sticker-messages)

相信大家每天都買貼圖互相~攻擊~傳話，在一個對話的過程中，使用貼圖都可以讓整的對話的溫度上升，而在前一陣子的更新中貼圖也新增的 Keywords (關鍵字)的欄位，讓每個機器人可以在收到訊息知道用戶使用貼圖時的含義，必藉此做更多的回應與應用操作，

<script async class="speakerdeck-embed" data-slide="9" data-id="0ec99040fbed4ad592fcf1c40dfa1f4e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

> 貼圖清單：https://developers.line.biz/en/docs/messaging-api/sticker-list/
### [Image message](https://developers.line.biz/en/docs/messaging-api/message-types/#image-messages)
### [Video message](https://developers.line.biz/en/docs/messaging-api/message-types/#video-messages)
### [Audio message](https://developers.line.biz/en/docs/messaging-api/message-types/#audio-messages)
### [Location message](https://developers.line.biz/en/docs/messaging-api/message-types/#location-messages)
### [Imagemap message](https://developers.line.biz/en/docs/messaging-api/message-types/#imagemap-messages)
### [Template message](https://developers.line.biz/en/docs/messaging-api/message-types/#template-messages)
### [Flex Message](https://developers.line.biz/en/docs/messaging-api/message-types/#flex-messages)

更多每個項目的格式可以參考 [Message type](https://developers.line.biz/en/docs/messaging-api/message-types/#template-messages)

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
