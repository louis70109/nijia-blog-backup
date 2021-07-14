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
大家好，我是 LINE Taiwan DevRel 團隊的 NiJia Lin。

社團頁面：https://www.facebook.com/groups/chatbot.tw
活動報名頁面：https://chatbots.kktix.cc/events/chatbots-meetup-in-central-taiwan-016
活動簡報：https://speakerdeck.com/line_developers_tw/line-api-platform-update-202011

<!-- more -->

# LINE Bot 入門介紹與 Platform API 更新資訊

<script async class="speakerdeck-embed" data-slide="6" data-id="d06175338bb24488b51bbd7bfcd0e32a" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

我們的服務要怎麼收到來自用戶的訊息呢？用戶會在 LINE 通訊軟體中輸入訊息，會打到 LINE Platform 中，接著再透過 Webhook 的方式打到你的服務(Server)上，而當中各位的所建立的 Channel 則是在 Platform 與 Server 之間，更多內容可以參考近期釋出的三篇指南：

- [LINE Bot 開發者指南詳解 1. 關於 LINE Bot](https://engineering.linecorp.com/zh-hant/blog/line-bot-guideline-1/)
- [LINE Bot 開發者指南詳解 – 2. 使用 Webhook URL 接收請求時的注意事項](https://engineering.linecorp.com/zh-hant/blog/line-bot-guideline-2/)
- [LINE Bot 開發者指南詳解 – 3 發送 API 請求時的注意事項](https://engineering.linecorp.com/zh-hant/blog/line-bot-guideline-3/)

<script async class="speakerdeck-embed" data-slide="9" data-id="d06175338bb24488b51bbd7bfcd0e32a" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

Provider 是各位需要注意的部分，它代表的是個人、公司或是一個組織，這部分大家在建立是要非常注意這個部分([Policy 參考](https://line.me/en/terms/policy/))，各位所建立的 Channel(可能是一隻 Bot、LINE Login...)是不能切換 Provider，因為在建立 Channel 時是當中有說明 Channel 是與當前 Provider 綁定相關資訊保護大家當中 Channel 的資訊，因此大家要建立時要再三注意當前 Provider 是誰喔！

<script async class="speakerdeck-embed" data-slide="13" data-id="d06175338bb24488b51bbd7bfcd0e32a" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這部分的內容介紹了引用內容 [NYCU Glocal Digital Service & Innovation Competition 黑客松活動紀錄](https://engineering.linecorp.com/zh-hant/blog/nycu-glocal-digital-innovation-competition-2021/#line-bot-apis-introduction-and-demonstration)

- [取得使用者資訊](https://developers.line.biz/en/reference/messaging-api/#get-profile)
- [取得貼圖關鍵字範例](https://github.com/louis70109/MIT_flask-line-bot-demo/blob/master/reply_message/sticker_keywords.py)
- [更換 LINE Bot 頭像](https://developers.line.biz/en/docs/messaging-api/icon-nickname-switch/#specifying-icon-and-display-name) 讓使用者快速辨認當前身份
- 讓使用者在手機介面上快速回答的功能 – [Quick Reply](https://github.com/louis70109/MIT_flask-line-bot-demo/blob/master/reply_message/quick_reply_echo_bot.py)
- 強大而樸實無華，讓你可以建立選單給使用者滿滿的視覺饗宴 – [Rich Menu](https://developers.line.biz/en/docs/messaging-api/using-rich-menus/)
  - [建立步驟程式碼](https://github.com/louis70109/MIT_flask-line-bot-demo/tree/master/richmenu)

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
