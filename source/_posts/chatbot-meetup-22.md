---
title: "LINE 開發社群計畫: Chatbot Taiwan 第 22 場社群活動紀錄分享"
tags:
  - LINE
  - DevRel
categories: 研討會
date: 2020-08-28 13:00:22
---

![chatbot everyone](https://nijialin.com/images/2020/chatbot-22-total.jpg)

# 前言

大家好，我是 LINE Taiwan 技術推廣工程師 - NiJia，本次於 [Chatbot 第 22 場小聚](https://chatbots.kktix.cc/events/meetup-022)擔任講者分享與 LINE 相關的內容，感謝大家在外面下著大雨的平日晚上還是這麼熱情來參加，以下我就分享參加的活動紀錄。 😊

- Chatbot 社群：https://www.facebook.com/groups/chatbot.tw
- KKTIX 報名頁面：https://chatbots.kktix.cc/events/meetup-022
<!-- more -->

# LINE platform API update August

![chatbot nijia](https://nijialin.com/images/2020/chatbot-22/nijia-1.jpg)

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

#[《LINE API 與 UX 入門課程分享》Chatbot User Experience Design](http://profwen.com/uxchatbot)

> 簡報連結： http://profwen.com/uxchatbot

接著到另一位講者也是新上任的 LINE API Expert - 溫明輝 教授為大家帶來分享，這次的分享中主要圍繞以下三個項目：

1. Chatbot 的基本認識
2. Chatbot 的設計流程
3. Chatbot 的經驗法則

一開始先敘述一下我們日常所說的「聊天機器人」應該被更正為「對話機器人」，且它應該是個「對話式人機介面」
(Conversational User Interface)，因為一隻機器人要是被定會在聊天的話，那他應該會擁有大量的人工智慧功能在裡面，只是一般 Chatbot 開發者在實作時都是以一個對話的形式下去開發而非聊天，因此開頭也直接說明一下 Chatbot 的用詞遣字問題。

![don1](https://nijialin.com/images/2020/chatbot-22/don-1.png)

接著從微股力的 LINE 官方平台的經營數據中談到對話式人機介面設計，用簡單的範例帶大家了解一下在設計介面時應該注意的哪些部分。

> 平常在寫 chatbot 時需要多考量一下設計對話流程上的盲點，否則很容易使用傳統的設計思維來處理對話。

![don2](https://nijialin.com/images/2020/chatbot-22/don-2.png)

接著就帶了許多相關的 UI 介面元素讓大家知道一下要如何選取適合的元件放入對應的對話內容中。

![don3](https://nijialin.com/images/2020/chatbot-22/don-3.png)
![don4](https://nijialin.com/images/2020/chatbot-22/don-4.png)

接下來到了第二部分就說明在什麼情況下屬於金字塔的何種位置，主要是需要知道目前大家的鋼需是什麼，即便當前的介面不是那麼美觀，但若能先解決掉目標族群需求的話這隻 chatbot 就是好的開始。

> 這邊教授也建議大家有時別太執著於 80-90 的路，先把底層做好可以解決很多事

![don5](https://nijialin.com/images/2020/chatbot-22/don-5.png)

了解需求 ➡️ 定位需求 ➡️ 設計需求 ➡️ 開發需求

![don6](https://nijialin.com/images/2020/chatbot-22/don-6.png)

接著就從 OOTD 穿搭機器人告訴大家他們當初在設計專案時的整個脈絡思維，以及評估競爭對手、到功能資訊架構等等...帶大家了解要設計一隻機器人其實複雜度也是很高的，如何讓目標族群正確收到想要的內容也是需要經過很縝密的思考才能獲得到。
![don7](https://nijialin.com/images/2020/chatbot-22/don-7.png)

最後第三部分的 13 種設計原則可以參考 [Chatbot meetup 12 的心得](https://nijialin.com/2019/09/12/Chatbot-meetup-12/)，這部分很值得大家參考在設計 chatbot 時的一些核心原則。

# 閃電秀

![chatbot jarsgin](https://nijialin.com/images/2020/chatbot-22/jarsing1.jpg)

<iframe src="//www.slideshare.net/slideshow/embed_code/key/uAHL6LynBfL8Ce" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/jarsing/lightning-talk-linebizcard20200827" title="用liff.shareTargetPicker分享我的名片（電話及網址可點擊）" target="_blank">用liff.shareTargetPicker分享我的名片（電話及網址可點擊）</a> </strong> from <strong><a href="https://www.slideshare.net/jarsing" target="_blank">佳新 陳</a></strong> </div>

閃電秀就由一樣剛上任的佳新來展示一下他是如何使用 liff.shareTargetPicker 來發送自己的名片，透過簡單的步驟讓大家可以快速使用使用 LIFF 的新功能將名片分享給其他朋友。
![jarsing2](https://nijialin.com/images/chatbot-22/jarsing2.png)

# 活動小結

在每個月的 Chatbot meetup 與大家交流也讓我從中學到不少知識，希望透過 LINE API update 讓大家更快速的了解我們增加與改變的內容，進而讓大家的 Developer Experience(DX) 可以獲得提升 😊

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：@line_tw_dev
![](https://i.imgur.com/gxHgAzB.png)

# 關於「LINE 開發社群計畫」

LINE 今年年初在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來察看最新的狀況。詳情請看:

- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
