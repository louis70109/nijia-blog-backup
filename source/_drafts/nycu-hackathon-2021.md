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

大家好我是技術推廣工程師 Nijia Lin，本次很開心可以與陽明交通大學 - 國際事務處 一同合辦 「NYCU Glocal Digital Service & Innovation Competition」，本次的活動內容為三天的黑客松，期間包括了演講、工作坊、競賽 三個環節，讓同學們可以在這三天的時間內與來自不同國家的同學一同發揮創意打造產品。

活動網頁: https://event.oia.nycu.edu.tw
活動日期: 7/1(四)-7/3(六)

## TL;DR

第一天則由 Evan Lin、我(Nijia Lin) 以及 API Expert - Richard Lee 以演講的方式帶大家了解 LINE 的 Ecosystem 下能做到的各式創意內容。
第二天則由其他 Expert - 戴均民、Wolke、卡米哥、Caesar Chi、陳佳新 讓大家可以在線上預約時間詢問專家們開發與設計上的意見。
最後一天則由 Evan 與另 Expert - CL Sung 為大家講評並頒獎給獲獎同學，更多細節歡迎大家繼續往下看囉！

<!-- more -->

# 第一天 - 演講

## Introducing LINE ecosystem

![](https://nijialin.com/images/2021/nycu-hackathon/2021.7.1_210703.jpg)


第一天下午 LINE 的時段開場由資深技術推廣工程師 - Evan Lin 為大家介紹 LINE 的 Ecosystem，逐步讓各位了解每個服務以及 Chatbot 能帶來更多的應用與契機。

<script async class="speakerdeck-embed" data-slide="6" data-id="f36fefb084774a8e904c3593ddc55fe0" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

首先在 LINE 中我們擁有了許多各式各樣的服務，讓大家可以即時在 LINE 上解決需求，但在使用這些服務時總是會有官方帳號，會在特定時間內將你想看到的內容推送給你，且你也可以透過問答的方式找到自己想要的東西，這也是接下來要介紹的 LINE Bot。

<script async class="speakerdeck-embed" data-slide="12" data-id="f36fefb084774a8e904c3593ddc55fe0" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

相信大家看到這一頁應該不陌生，LINE Bot 在發送訊息時其實可以客製化許多內容，其中此部分介紹的為「Flex Message」，設計時也都會以 [Flex Message Simulator](https://developers.line.biz/flex-simulator) 做開發，更多細節請參考下方文章。

- [藉由 Flex Message Simulator 實現並發送測試用 Flex Message](https://engineering.linecorp.com/zh-hant/blog/how-to-send-flex-message-on-simulator/)

<script async class="speakerdeck-embed" data-slide="18" data-id="f36fefb084774a8e904c3593ddc55fe0" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

相信大家不管有在電商網站、手遊都會有使用過 Single Sign On(SSO)，讓使用者可以快速地透過點擊登入按鈕即可登入平台之中，且服務端也不用管理使用者的密碼(同時也增加安全性)，而此功能在 LINE 這即稱為 [LINE Login](https://developers.line.biz/zh-hant/docs/line-login/getting-started/)，只要使用者平常有在使用 LINE，都可以透過快速登入的方式使用。

- [LINE Bot 開發者指南詳解 – 4. LINE Login](https://engineering.linecorp.com/zh-hant/blog/line-bot-guideline-4/)

> 更多的內容歡迎參考[官方文件](https://developers.line.biz/zh-hant/docs/line-login/getting-started/)

<script async class="speakerdeck-embed" data-slide="21" data-id="f36fefb084774a8e904c3593ddc55fe0" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

另一個由 LINE 開發的網頁前端框架 LIFF([LINE Frontend Framework](https://developers.line.biz/en/docs/liff/overview/))，它是整合 LINE Login 又更上一層樓的強大功能，可以讓使用者在 LINE 中打開 LIFF 頁面時，會自動辨認是否為 LINE 的使用者，讓整體使用體驗大幅提升。

## LINE Bot APIs introduction and demonstration

![](https://nijialin.com/images/2021/nycu-hackathon/2021_0.7.1_210703.jpg)


<script async class="speakerdeck-embed" data-slide="5" data-id="7ae54be5df744f079c10e5c7348dadd5" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

接著輪到我為各位更詳細介紹 LINE Bot API 與提供範例給大家參考。首先就先帶大家了解 LINE Bot 的運作流程(在 LINE 上面打字 -> LINE 轉發至你的服務中)，並說明 LINE Bot 主要的兩個功能 Repl 與 Push Event 個別的使用情境，讓同學們在開發時可以依照自己的創意點子來使用(如下圖所示)。

<script async class="speakerdeck-embed" data-slide="12" data-id="7ae54be5df744f079c10e5c7348dadd5" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>


<script async class="speakerdeck-embed" data-slide="13" data-id="7ae54be5df744f079c10e5c7348dadd5" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

接著此部分則詳述每則訊息可涵蓋的訊息格式為哪些，不論是純文字、貼圖、圖片、影片、聲音、位置、以及客製化訊息內容(Flex Message)皆可使用，更詳細的說明大家請參考[官方文件](https://developers.line.biz/en/docs/messaging-api/sending-messages/#methods-of-sending-message)。


下一個環節則是帶大家手把手從程式碼中一步一步頗析在演講中的功能究竟如何實現，透過 [MIT_flask-line-bot-demo](https://github.com/louis70109/MIT_flask-line-bot-demo) 可以讓各位實際演練從最基本的 Echo bot(所見即所得)、各式[回應訊息](https://github.com/louis70109/MIT_flask-line-bot-demo/blob/master/reply_message/reply_event_bot.py)的練習、到 Rich Menu 的建立，全部都在 [MIT_flask-line-bot-demo](https://github.com/louis70109/MIT_flask-line-bot-demo) 這個專案中，大家可以 Fork 去試玩看看。

- [取得使用者資訊](https://developers.line.biz/en/reference/messaging-api/#get-profile)
- [取得貼圖關鍵字範例](https://github.com/louis70109/MIT_flask-line-bot-demo/blob/master/reply_message/sticker_keywords.py)
- [更換 LINE Bot 頭像](https://developers.line.biz/en/docs/messaging-api/icon-nickname-switch/#specifying-icon-and-display-name) 讓使用者快速辨認當前身份
- 讓使用者在手機介面上快速回答的功能 - [Quick Reply](https://github.com/louis70109/MIT_flask-line-bot-demo/blob/master/reply_message/quick_reply_echo_bot.py)
- 強大而樸實無華，讓你可以建立選單給使用者滿滿的視覺饗宴 - [Rich Menu](https://developers.line.biz/en/docs/messaging-api/using-rich-menus/)
  - [建立步驟程式碼](https://github.com/louis70109/MIT_flask-line-bot-demo/tree/master/richmenu)

<script async class="speakerdeck-embed" data-slide="31" data-id="7ae54be5df744f079c10e5c7348dadd5" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>



## Advanced UX patterns with LINE Bot APIs

![](https://nijialin.com/images/2021/nycu-hackathon/cd3f91f975efca3489160ca15c1c72a7b_29947608_210703_2.jpg)

第一天的尾聲則由 API Expert - Richard Lee 來為大家介紹如何在 LINE Bot API 上增進使用者體驗，透過先前的議程分享後在此部分讓同學們可以在開發的過程中，設計出一個良好互動體驗的 LINE Bot，除了讓同學們在作品呈現上可以更有效的展示，也在短短的時間內帶大家認識在業界開發上時常會需要注意的部分。

> 其他參考內容： TECHPULSE 2020 - [LIFF SDK 的開發者體驗與實用秘訣](https://youtu.be/TkSkaCP3gAY?t=1722)

# 第二天 - API Expert Mentor 預約問答時間

同學們從演講完後即開始緊鑼密鼓的開始撰寫程式，當然在過程中難免會遇到些開發上的問題，這裡我們邀請了業界的 LINE Bot 專家來為每一位學生解惑，同學們都非常踴躍與積極地把握每個可以詢問的時間來請教這些大師。

![](https://nijialin.com/images/2021/nycu-hackathon/2021_0.7.1_210703.jpg)

早上時段由 Caesar Chi 與 佳新 為同學們解答，一早就看到同學們這麼有活力且詢問了許多點子發想上實作的問題。

![](https://nijialin.com/images/2021/nycu-hackathon/cd3f91f975efca3489160ca15c1c72a7b_29947608_210703_1.jpg)

下午時段由 均民 與 Wolke 與各位同學在線上解答，下午的部分除了同學們把先前討論的問題提出外，再請教實作問題的同時 均民 也大方分享了他在開發上有遇到的狀況，提醒同學們在實作時需要注意哪些環節，讓整個發想的流程可以更順利地被完成！


![](https://nijialin.com/images/2021/nycu-hackathon/cd3f91f975efca3489160ca15c1c72a7b_29947608_210703.jpg)

晚上的部分則由 卡米哥 與 均民 輪流與各位同學最後的問題加催，同學們都已逐漸有些架構來詢問晚上的 Mentor，透過經驗分享也讓同學們了解當中所需要整理與修改的部分為哪些，把握最後的時間把創意點子實現出來，也讓第三天 Demo 時可以更加順利！

# 第三天 - 評分與講評

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
