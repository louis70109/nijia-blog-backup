---
title: "LINE 開發社群計畫: 2020 LINE 平台九、十月更新整理"
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

![](https://nijialin.com/images/1.png)

# 前言

大家好，我是 LINE Taiwan 的 Tech Evangelist - NiJia Lin。這次很開心受到 chatbot 社群的邀請，參加了 "[Chatbot meetup 聊天機器人新手小聚 24 @ Gandi](https://chatbots.kktix.cc/events/meetup-024)" 的聚會活動，並且分享 LINE API 更新與個人開發的心得。在此也跟各位分享本次參與的心得，並且也希望透過社群分享的力量能夠讓聊天機器人的開發動能更加的盛大。

- 社群 Chatbots Meetup： [https://chatbots.kktix.cc/](https://chatbots.kktix.cc/)
- 本次活動網頁: [活動網址](https://chatbots.kktix.cc/events/meetup-024)
- 本次活動的共筆紀錄： [https://hackmd.io/@chatbot-tw/meetups-024](https://hackmd.io/@chatbot-tw/meetups-024)

由於 Chatbots Meetup 本身屬於社群自主性的活動，所有內容也是相當的難得與有趣。也希望能夠透過本篇文章讓大家稍微了解 Chatbots Meetup 社群的魅力，讓更多朋友了解到打造自己的聊天機器人是如此讓人開心的事情。

<!-- more -->

### 整場影片分享

<iframe width="560" height="315" src="https://www.youtube.com/embed/n5LZlcQosGw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# LINE Platform Update 2020/10

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZFPN5inMtM8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

在九月與十月這兩個月中釋出了許多資訊，以下就一一帶大家了解一下究竟釋出了什麼新的強大 API 吧！

## LIFF 釋出 v.2.4.1

### Open another LIFF page would be checked at LIFF

### fix called twice

## Get bot info

<script async class="speakerdeck-embed" data-slide="7" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

## Webhook API

<script async class="speakerdeck-embed" data-slide="8" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

- Get
- PUT
- Verify(Test)

建議做法

- Version migration
- Rollback service
- Procedure migration(e.g. C++ -> Golang)

9~16 則是一個流程圖

## TLS migration

<script async class="speakerdeck-embed" data-slide="18" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

but we dont know our server supporting, so you could use verify webhook api to test you server.

### next test example

<script async class="speakerdeck-embed" data-slide="20" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

由於 webhook test 會送一個空的內容過去，若回傳 `200` 則代表當前 Server 是支援的喔！

> 轉換時間 2020/10~2021/01，有使用到 LINE 服務的大家要注意時間，記得 migration！

## Flex Message Update 2

### 1. Carousel count from `10` to `12`

### 2. Flex Message 相關參數新增

<script async class="speakerdeck-embed" data-slide="24" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

既然使用 `flex` 這個名詞，勢必得加入更多支援讓 Flex Message 更像瀏覽器上的 Flexbox，

- `justifyContent`
- `alignItems`
- `linearGradient`
  - 此參數讓讓背景顏色可以使用`漸層`，讓 Designer 可以更好的使用之配色。

> 詳細圖片則參考下方簡報

<script async class="speakerdeck-embed" data-slide="24" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

### 3. 開發者福音：Flex Message `content` 參數可為空值！

<script async class="speakerdeck-embed" data-slide="26" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

在寫 Flex Message 時會因為一些情境的判斷式讓 `content` 的值為一個空陣列，過往在解析時遇到`空值`會無法顯示(出錯)，隨著這次更新中已經可以讓 `content` 參數為空值，若開發者們有因為這個參數多寫的許多判斷式，現今已可開始試著將程式相關判斷式看看，可以更減省你的 code 喔！

### 4. Image, Icon, Text `size` property

<script async class="speakerdeck-embed" data-slide="28" data-id="deb0906716b845a3a132cbafbc1074e8" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這次更新中三個參數皆可使用 `px` 來設定大小，讓 Designer 們可以更有效地控制 Flex Message 的視覺，且 Image 還能以`百分比`(`percentages`) 表示，可以讓圖片更能適應各種手機尺寸。

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
