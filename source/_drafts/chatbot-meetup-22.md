---
title: 【Chatbot】第 22 場社群活動紀錄分享
categories: 研討會
tags:
---

![chatbot everyone](https://nijialin.com/images/2020/chatbot-22-total.jpg)

# 前言

大家好，我是 LINE Taiwan 技術推廣工程師 - NiJia，本次於 [Chatbot 第 22 場小聚](https://chatbots.kktix.cc/events/meetup-022)擔任講者分享與 LINE 相關的內容，感謝大家在外面下著大雨的平日晚上還是這麼熱情來參加，以下我就分享參加的活動紀錄。 😊

- Chatbot 社群：https://www.facebook.com/groups/chatbot.tw
- KKTIX 報名頁面：https://chatbots.kktix.cc/events/meetup-022
<!-- more -->

# LINE platform API update August

![chatbot nijia](https://nijialin.com/images/2020/chatbot-22-nijia.jpg)

這個月的小聚由我來帶大家了解一下這個月 LINE API 更新了什麼內容 🎁

## Unsend event

<script async class="speakerdeck-embed" data-slide="4" data-id="2ebf41de520842e8a557951cdd85583d" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這功能是能在 webhook 收到當 Group(群組)/Room(聊天室) 中的使用者若有`收回`訊息時，Bot 會收到一個來自 webhook 的 unsend event，實際回傳回來的 JSON 如簡報中所示：

## Video play complete Event

<script async class="speakerdeck-embed" data-slide="6" data-id="2ebf41de520842e8a557951cdd85583d" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這個部分一樣會是來自於 webhook 的 Event，當 Bot 發送一個含有 `Tracking id` 的影片給用戶(Reply/Push)，當用戶看完這個影片時會收到一個`影片播完`的 Event，如簡報的右邊的 JSON 所示， Tracking Id 會對應 Bot 剛剛送出的 Id，因此在設計時這部分需要特別注意喔！

<script async class="speakerdeck-embed" data-slide="9" data-id="2ebf41de520842e8a557951cdd85583d" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這部分的更新改動 `audiences` 為 `Option` 選項，讓使用者可以有更多的彈性空間可以使用。

<script async class="speakerdeck-embed" data-slide="12" data-id="2ebf41de520842e8a557951cdd85583d" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

過往在建立 Audience 群眾時只能上傳 IFAs 的清單檔案，而在這次的更新中以可以建立 Audience 群眾時放入 User Id 囉！

> User Id 如何取得可參考投影片左下角的部分。

<script async class="speakerdeck-embed" data-slide="15" data-id="2ebf41de520842e8a557951cdd85583d" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

若有在使用以下三個 API 的朋友需要注意：

- [Get Content](https://developers.line.biz/en/reference/messaging-api/#get-content)
- [Upload rich menu image](https://developers.line.biz/en/reference/messaging-api/#upload-rich-menu-image)
- [Download rich menu image](https://developers.line.biz/en/reference/messaging-api/#download-rich-menu-image)

Domain 已經從 api.line.me 改成 api-`data`.line.me，若有在使用相關功能請將網址置換掉避免問題產生。

#[《LINE API 與 UX 入門課程分享》Chatbot User Experience Design](http://profwen.com/uxchatbot) - 溫明輝

> 簡報連結： http://profwen.com/uxchatbot
> https://medium.com/@nijia.lin/20190917-chatbot-meetup-12-65999085f029

# 結論

# 活動小結

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：@line_tw_dev
![](https://i.imgur.com/gxHgAzB.png)

# 關於「LINE 開發社群計畫」

LINE 今年年初在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來察看最新的狀況。詳情請看:

- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
