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

<!-- more -->

# 介紹

Flex Message 是什麼？它是一個 LINE 很強大的訊息圖文選單，能夠讓開發者透過 JSON 的方式建立起漂亮的選單(如下)，讓 LINE 官方帳號(Official Account)的擁有者(Provider)可以使用設計過的訊息選單與用戶做更多的互動。

![](https://nijialin.com/images/2021/line-simulator/sample.png)

# 如何設計 Flex Message？使用 LINE Simulator

許多開發者在開發 Flex Message 給 Chatbot 或是 ShareTargetPicker ([參考文章](https://engineering.linecorp.com/zh-hant/blog/share-target-picker-liff/))時經常會透過 [LINE Simulator](https://developers.line.biz/flex-simulator) 來將想要的樣式透過介面上的操作選項來處理想發送在 LINE 平台上的內容。

![](https://nijialin.com/images/2021/line-simulator/send0.png)

- LINE 官方提供的一個強大介面
- 可發送

官方新聞稿 - [You can now send test messages from Flex Message Simulator](https://developers.line.biz/en/news/2021/05/20/send-test-message-flex-message-simulator/)

- [使用 2020 Flex Message 的 10 個新功能 – 讓您在 LINE 的訊息設計更有彈性](https://engineering.linecorp.com/zh-hant/blog/2020-flex-message-10-reason/)
- [在 Vue3 中引入 LIFF 的 ShareTargetPicker 分享 FlexMessage 訊息給 LINE 好友](https://engineering.linecorp.com/zh-hant/blog/how-to-use-liff-in-vue3/)
- [Flex Message 的 Update 1 已公開](https://engineering.linecorp.com/zh-hant/blog/flex-message-update1/)
- [2020/10 Flex Message Update 2 released](https://developers.line.biz/en/news/2020/10/08/flex-message-update-2-released/)
  對戰範例一：

<script src="https://gist.github.com/louis70109/9a6f3b742b603e298a321a3e96a8b9e9.js"></script>

疊層範例：

<script src="https://gist.github.com/louis70109/4cf6eda9a4267b24041435cebfe6b333.js"></script>

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
