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

大家好，我是 LINE Taiwan 的 Tech Evangelist - NiJia Lin。這次很開心受到 chatbot 社群的邀請，，參加了 "[Chatbot meetup 聊天機器人小小聚 28 @ Onramp Studio](https://events.chatbot.tw/events/27)" 的聚會活動，過了一個農曆年，相信很多人也很期待三月 LINE Platform API 的新功能，並且分享 LINE API 更新與個人開發的心得。在此也跟各位分享本次參與的心得，並且也希望透過社群分享的力量能夠讓聊天機器人的開發動能更加的盛大。

- 社群 Chatbots Meetup： [https://www.facebook.com/groups/chatbot.tw](https://www.facebook.com/groups/chatbot.tw)
- 本次活動網頁: [活動網址](https://events.chatbot.tw/events/27)

由於 Chatbots Meetup 本身屬於社群自主性的活動，裡面也有許多社群朋友所贊助的閃電秀。裡面的所有內容也是相當的難得與有趣。也希望能夠透過本篇文章讓大家稍微了解 Chatbots Meetup 社群閃電秀的魅力。

這次就由我用文章帶大家了解一下近期有什麼有趣的更新內容吧！

<!-- more -->

# 介紹

過往在做 Chatbot 時我們時常會依賴於 Rich menu 來幫助用戶更快速的使用我們所建立服務。如下圖所示，Chatbot 會提供許多功能讓用戶透過快速點擊觸發我們希望用戶所達到的行為。

<script async class="speakerdeck-embed" data-slide="3" data-id="fc4da12ffb4c4f779be22900e3268f67" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

但以上功能是基於用戶與 Chatbot 是一對一互動狀態才能使用 Rich menu，如今天第二位講者聖佑所提到的讀書會小幫手，讀書會群組基本上都是以**一個群組(Group)**為單位，若在群組中 Chatbot 則無法使用 Rich menu，會讓一些原本優秀的功能瞬間失去，因此這時候使用 Image map 或者 Quick Reply 來幫忙處理群組相關訊息。以下有些案例提供讀者們參考：

<script async class="speakerdeck-embed" data-slide="10" data-id="fc4da12ffb4c4f779be22900e3268f67" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

在應用許多 Chatbot 功能之後，相信開發者們都會漸漸的開始嘗試使用 [LIFF](https://developers.line.biz/en/docs/liff/overview/) 去做更多變化的組合應用，但以往在群組中要開啟 Chatbot 的 LIFF 是需要讓 Chatbot 多回應一則訊息，在對話中就會多了一則訊息是為了讓用戶可以點選並觸發相關事件。

然後現在可以透過在群組中使用 Quick Reply 來減少多餘的訊息，讓 Chatbot 可以輸出相關選項讓使用者可以在下方選擇後開啟對應的 LIFF 功能，達到快速觸發的功能，

<script async class="speakerdeck-embed" data-slide="12" data-id="fc4da12ffb4c4f779be22900e3268f67" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

- 讀書會的庶務

每週報名通知
發會議室網址
發每週筆記」

Email 的貧頸
不夠即時
因此使用 IM 系統

# 結論

# 活動小結

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：@line_tw_dev
![](https://www.evanlin.com/images/2020/line-tw-dev-qr.png)

# 關於「LINE 開發社群計畫」

LINE 今年年初在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來察看最新的狀況。詳情請看:

- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)
- [LINE Taiwan Developer Relations 2020 回顧與 2020 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2020)
- [2021 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2021-line-tw-devrel/)
