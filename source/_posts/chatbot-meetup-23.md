---
title: "LINE 開發社群計畫: 2020 九月 LINE 平台更新整理與 LIFF ShareTargetPicker 案例分享"
category:
  - 研討會
tags: ["Chatbot", "DevRel", "LINE"]
---

![](https://nijialin.com/images/chatbot.png)

# 前言

大家好，我是 LINE Taiwan 的 Tech Evangelist - NiJia Lin。這次很開心受到 chatbot 社群的邀請，參加了【[Chatbot meetup 聊天機器人小小聚 23 @Onramp Studio](https://events.chatbot.tw/events/10)】的聚會活動，前往且分享 LINE API 更新與個人 LINE Bot 開發心得，透過持續開發增加技術的敏銳度。在此也跟各位分享本次參與的心得，並且也希望透過社群分享的力量能夠讓聊天機器人的開發動能更加的盛大。

- 本次活動網頁: [活動網址](https://events.chatbot.tw/events/10)
- 本次活動的共筆紀錄： [https://hackmd.io/@chatbot-tw/meetups-023](https://hackmd.io/@chatbot-tw/meetups-023)

由於 Chatbots Meetup 本身屬於社群自主性的活動，裡面擁有許多社群朋友所贊助的閃電秀，所有內容也是相當的有趣。也希望能夠透過本篇文章讓大家稍微了解 Chatbots Meetup 社群閃電秀的魅力。

# LINE Platform 平台 2020 九月更新

![](https://nijialin.com/images/2020/chatbot-23/nijia-1.JPG)

### [投影片](https://speakerdeck.com/line_developers_tw/line-platform-update-202009)

<script async class="speakerdeck-embed" data-id="9d808139a16c46ac970b59e34180f812" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

## [Certificate authority that can be used in the Webhook URL added](https://developers.line.biz/en/news/2020/08/26/ca-list-update/)

## [LIFF v2.4.0 released](https://developers.line.biz/en/news/2020/08/31/release-liff-2-4-0/)

## [Messaging API update for September 2020](https://developers.line.biz/en/news/2020/09/01/messaging-api-update-september-2020/)

## [Redelivery object has been added to the criteria for narrowing down the narrowcast message target](https://developers.line.biz/en/news/2020/09/15/messaging-api-narrowcast-requestId/)

Narrowcast 的功能再度進化！這次 API 釋出了 Redelivery 的功能，讓已經發送過的訊息可以在加上條件並重新發送，針對鐵粉們更精準的行銷
![](https://nijialin.com/images/2020/chatbot-23/narrowcast-1.png)

![](https://nijialin.com/images/2020/chatbot-23/narrowcast-flow.png)

> 歡迎大家來一起貢獻 SDK - https://github.com/line

## Side project - Announcer

加入 Announcer 好友:
![](https://nijialin.com/images/2020/chatbot-23/announcer-qr.png)

- Frontend: https://github.com/louis70109/announcer-vue
- Backend: https://github.com/louis70109/Announcer

> 相關介紹文章 - [在 Vue3 中引入 LIFF 的 ShareTargetPicker 分享 FlexMessage 訊息給 LINE 好友](https://engineering.linecorp.com/zh-hant/blog/how-to-use-liff-in-vue3/)

![](https://nijialin.com/images/2020/chatbot-23/an-interface.png)

Announcer 是近期我為了在公司大群裡宣傳內部活動做的一個 Side project，Chatbot 當作管理介面讓管理者可以選擇自己想要發送訊息的樣板，點選之後會到前端頁面中，填寫對應欄位並使用 LIFF 的 [ShareTargetPicker 的 API](https://developers.line.biz/en/reference/liff/#share-target-picker) 來將功能發送出去，如下圖所示：

![](https://nijialin.com/images/2020/chatbot-23/an-sample.png)

由於 LIFF 本身屬於 LINE Login 的服務，因此在第一次登入時必須登入才能使用此相關功能
![](https://nijialin.com/images/2020/vue-use-liff/login-page.png)

登入之後依照對應欄位輸入完資料送出之後，就會到以下的選擇畫面來挑選欲發送 Template 的對象
![](https://nijialin.com/images/2020/vue-use-liff/liff-share-info.png)

如下圖範例所示，我就發送很特別 Flex Message 給公司內部的 Hackathon 決賽隊伍們～

![](https://nijialin.com/images/2020/vue-use-liff/picker-result.png)

# 閃電秀

鄭鈞瀚 專案分享 ：看財狗
![](https://nijialin.com/images/2020/chatbot-23/light-0.jpg)

Yukai 用 Liff 和 Line API 實作即時投票 / 彈幕系統
![](https://nijialin.com/images/2020/chatbot-23/light-1.jpg)

# 活動小結

社群分享永遠是讓創意激盪的最佳方式，而 Chatbots Meetup 是一個很熱情與充滿創造力的社群組織。也希望有更多有創意的開發者願意加入 LINE Chatbot 的開發行列，更希望能熱情的參與社群的活動與一起來分享。

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：[@line_tw_dev](https://lin.ee/s5RsZHo)

![](https://www.evanlin.com/images/2020/line-tw-dev-qr.png)

# 關於「LINE 開發社群計畫」

LINE 今年年初在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來察看最新的狀況。詳情請看:

- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
