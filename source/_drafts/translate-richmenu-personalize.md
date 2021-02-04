---
title: 如何以個性化方式在 LINE 中顯示 Rich Menu 以匹配用戶的機器語言
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

![](https://nijialin.com/images/2021/richmenu-personalize)

在過去的一年中，Rich Menu 上的文章非常受歡迎。對於擁有 LINE 正式帳戶或 LINE Chatbot 的用戶而言，它的優點是使用戶易於入門。通過在聊天頁面上顯示重要菜單並可以選擇各種操作。加上創建步驟 可以由兩個老百姓共同完成 包括具有編程技能的人 豐富菜單是每個帳戶今天必須具備的基本功能也就不足為奇了。
對於本文 我將邀請所有人開發一個 Rich Menu，以便能夠顯示每個用戶機器的語言。我們首先必須知道的主要因素是 “該人中的用戶計算機使用哪種語言？” 我們可以通過哪種方式獲取用戶機器的語言 這並不難，因為 LINE 已 language 在用戶的個人資料信息中添加了一個命名屬性。早期我們可以做的`userId`，`displayName`，`pictureUrl`和。`statusMessage`

到目前為止，我們已經準備好了成本和想法。因此，讓我們看一下開發它的步驟。

1. 準備使用 Cloud Functions for Firebase 開發的 LINE Chatbot。
2. 準備泰語和英語的豐富菜單。
3. 創建條件以捕獲關注類型的 Webhook 事件
4. 從用戶個人資料中檢索 “語言” 值。
5. 顯示豐富菜單以匹配該用戶的語言。

<!-- more -->

# 1. 準備使用 Cloud Functions for Firebase 開發的 LINE Chatbot。

對於從未開發過具有用於 Firebase 的 Cloud Functions 的 LINE Chatbot 的用戶，請遵循以下文章的步驟（1-3 就足夠了），但如果有經驗的話。現在跳到步驟 2。

> [使用 Messaging API 和 Cloud Functions 在 Firebase 建置 LINE Bot](https://medium.com/linedevth/%E0%B8%AA%E0%B8%A3%E0%B9%89%E0%B8%B2%E0%B8%87-line-bot-%E0%B8%94%E0%B9%89%E0%B8%A7%E0%B8%A2-messaging-api-%E0%B9%81%E0%B8%A5%E0%B8%B0-cloud-functions-for-firebase-20d284edea1b)

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
