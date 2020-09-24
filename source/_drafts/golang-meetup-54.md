---
title:
  "[object Object]": null
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

![](https://nijialin.com/images/2020/golang-54/go-logo.jpg)

# 前言

大家好，我是 LINE Taiwan 的 Tech Evangelist - NiJia Lin。這次很開心再度參加了<mark>Golang 社群第 54 場</mark>的聚會活動。在此也跟各位分享本次參與的心得，並且也希望透過社群分享的力量能夠讓開發動能更加的盛大。

- Golang 社群活動頁面： [https://www.meetup.com/golang-taipei-meetup/events/272926722/](https://www.meetup.com/golang-taipei-meetup/events/272926722/)

<!-- more -->

## 整場活動影片

<iframe width="560" height="315" src="https://www.youtube.com/embed/ShZsxFl0Ph4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# 介紹

<script async class="speakerdeck-embed" data-id="2865bb1c091b4210b4852bb76828a769" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

LINE Music 是一個強大且應用許多工具的服務，講者 - Wei 在本次社群分享中 Focus 在使用 Golang 的細節

> 很多人會很好奇 LINE Music 有什麼長處？可以參考官方部落格的這篇([【LINE MUSIC】獨家去人聲跟唱 歌神換你當！](http://official-blog.line.me/tw/archives/83474706.html))，

<script async class="speakerdeck-embed" data-slide="28" data-id="6e0e7afe98124bf08f13f200f1b45010" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

> 此投影片為其他分享會中提到的部分

<script async class="speakerdeck-embed" data-slide="3" data-id="2865bb1c091b4210b4852bb76828a769" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

從 Agenda 中即可得知 Music 為了讓整題服務更加順暢並因應不同的使用情境而套用相當多的工具，在這次的分享中也一一介紹每個工具是如何選擇且應用於當前的微服務。

<script async class="speakerdeck-embed" data-slide="5" data-id="2865bb1c091b4210b4852bb76828a769" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

在這張架構圖中清楚的展示在使用 golang 的微服務中，每個服務是透過何種流程去達到互相溝通的階段

外部的部分則分有<mark>Web</mark>、<mark>APP</mark>、<mark>External Resource</mark>(第三方資源)

- Web: 由於介面上相較 APP 來說比較複雜，因此在大部分的情況下會選用 GraphQL 增加彈性提供介面讓前端開發者可以有較多的選項去索取資源。
  - 推薦套件: [99designs/gqlgen](https://github.com/99designs/gqlgen)，並且很快地整合進 Gin 當中
- App: 因為介面大小較受限，因此大部分情況下是提供 RESTful API 讓 App 開發者去介接。
- External Resource: 當合作廠商更新了資源(ex: 音樂、歌手)時，為了確保資源的完整度則選擇透過 WebSocket 讓兩邊的 Server 溝通。

內部部分：

- 使用 [Gin] 框架來當作 API Gateway 介接前端的需求。
  - 在 Routing 可以很快速的劃分 Group 讓 Controller 共用
  - 客製化 Middleware 很方便
- 使用 gRPC 溝通內部服務降低 Response time

> LINE 再審查 Open Source 是很嚴格的，必須檢查 Source code 確保沒有資安上的問題才可以使用。

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
