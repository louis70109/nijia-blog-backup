---
title: 2020 六月 LINE 平台更新整理與 LINE Group/Room Chatbot 的展示
categories: 學習紀錄
tags:
---

![](https://i.imgur.com/0QAGPDc.png)

# 前言

大家好，我是 LINE Taiwan 的 Tech Evangelist – Evan Lin。這次很開心受到 chatbot 社群的邀請，參加了 “Chatbot meetup 聊天機器人小小聚 20 @Online” 的聚會活動，並且分享 LINE API 更新與個人開發的心得。在此也跟各位分享本次參與的心得，並且也希望透過社群分享的力量能夠讓聊天機器人的開發動能更加的盛大。

社群 Chatbots Meetup： https://chatbots.kktix.cc/
本次活動網頁: 活動網址
本次活動的共筆紀錄： https://hackmd.io/@chatbot-tw/meetups-021

由於 Chatbots Meetup 本身屬於社群自主性的活動，裡面也有許多社群朋友所贊助的閃電秀。裡面的所有內容也是相當的難得與有趣。也希望能夠透過本篇文章讓大家稍微了解 Chatbots Meetup 社群閃電秀的魅力。

這次活動總算又回到 LINE 台灣的辦公室來舉辦，同時這也是疫情後 LINE 辦公室第一次舉辦線下的聚會。希望透過這次的聚會可以讓更多朋友了解到打造自己的聊天機器人是如此讓人開心的事情。

### 整場分享的影片：

<iframe width="560" height="315" src="https://www.youtube.com/embed/8Lu4LHKSMlo?start=369" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<!-- more -->

## LINE Platform 平台 2020 六月 & 七月更新

![](../images/2020/0623_2.jpg)

#### [投影片](https://speakerdeck.com/line_developers_tw/line-api-platform-update-202007)

<script async class="speakerdeck-embed" data-id="279ac2f6f39348c482533ff9f12568d0" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

在 6/22 的更新當中我們 Issue access_token 的功能([參閱](https://developers.line.biz/en/reference/messaging-api/#issue-channel-access-token-v2-1)除了可以拿到 chatbot 中 JWT 樣式的 access_token，裡面還有一個 unique 的 key_id 欄位，可以使用這個新的 API - [Get all valid channel access token key IDs v2.1](https://developers.line.biz/en/reference/messaging-api/#get-all-valid-channel-access-token-key-ids-v2-1) API 去找到

以下是 Get all valid channel access token key IDs v2.1 的流程圖：
![](https://i.imgur.com/LEAYqrL.png)

<script async class="speakerdeck-embed" data-slide="3" data-id="279ac2f6f39348c482533ff9f12568d0" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

需要注意的部分就是 Get all valid channel access tokens v2.1 的 API 會在 7/22 後就會被棄用，因此若使用相關功能的朋友可以使用新的 [Get all valid channel access token key IDs v2.1](https://developers.line.biz/en/reference/messaging-api/#get-all-valid-channel-access-token-key-ids-v2-1) API 哦！

### 06/29 LIFF v2.3.0 released

<script async class="speakerdeck-embed" data-slide="5" data-id="279ac2f6f39348c482533ff9f12568d0" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這次的更新中可以在 LIFF 的網址中使用子路徑(`/path`)以及 Query parameters (`?key=value`)了，在 LINE Developers console 中增加了兩個模式 `Concatenate` 以及 `Replace`，更新之前就已經存在的 LIFF page 則會已被換到 `Replace` 上，而新建立的 LIFF page 則預設為 `Concatenate`。

若你已有相關的 workaround 並且暫時不想更新的話則就繼續使用 `Replace` 模式。

- liff.shareTargetPicker 已經可以抓出錯誤囉！
<script async class="speakerdeck-embed" data-slide="8" data-id="279ac2f6f39348c482533ff9f12568d0" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

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
