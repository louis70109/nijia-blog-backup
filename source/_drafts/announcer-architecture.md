---
title:
  "[object Object]": null
categories: 學習紀錄
tags:
---

![](https://i.imgur.com/0QAGPDc.png)

# 前言

<!-- more -->

# 流程

```puml
@startuml
User -> Bot: Type any text to trigger
Bot -> User: Reply templates
User -> Bot: Click template url
Bot -> LIFF: Open Browser to start LIFF
LIFF -> Vue: Redirect endpoint url with liff.state
Vue -> LIFF: Init LIFF
LIFF -> LINE: Access and identify user
LINE -> Vue: Save information on localstorage
User -> Vue: Input some information
Vue -> LIFF: Use LIFF API - ShareTargetPicker
LIFF -> LINE: Access user's friend list
LINE -> User: Return friend list page
User -> LINE: Select Friend/Group/Room
LIFF -> LINE: Send messages by ShareTargetPicker
@enduml
```

# 初期規劃

- Backend:
  - Bot: admin interface to select template
  - API: catch browser request and use EJS to response frontend for browser
  - EJS: use LIFF to send Flex Message

使用 Express + EJS 來簡易使用 LIFF 發送 FlexMessage，完成第一版

由於 template 增加開始需要一些渲染的作業，寫純 JS 除了 code 會變很多以外也在重複造輪子，由於框架已經幫忙做好很多這類的事情，因此就將它轉至框架上

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
