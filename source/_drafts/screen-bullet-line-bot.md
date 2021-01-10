---
title: 【標題】題目
categories: 應用
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

# 前言

![](https://nijialin.com/images/2021/bullts/bullets-sample1.gif)

去年下半年時於 [COSCUP 2020](https://coscup.org/2020/) 的閉幕閃電秀中與 [Chatbot 社群小聚](https://github.com/Chatbot-Taiwan/meetups/blob/master/taipei/2020.md#chatbot-meetup-23-at-onramp-studio)看到社群朋友展示使用 LIFF 來發射彈幕覺得有趣又回憶滿滿，從以前在看**ニコニコ動画**時就很常看到彈幕出現在影片中(甚至有時候彈幕還比影片還好笑)，而透過這樣的互動讓觀眾並及時回饋，拉近活動(影片、直播、演唱會...)與觀眾的距離。想到去年因為疫情需要把社群聚會改成線上，剛好在前一陣子搜尋到[這篇文章](https://qiita.com/youtoy/items/051dc658025a3b21c7f0)，以下就使用 Chatbot 搭配文章在使用 OBS 來使用它！

<!-- more -->

> 完整專案: [louis70109/Screen-LINE-Bullets](https://github.com/louis70109/Screen-LINE-Bullets)

# 介紹

## [GSAP](https://greensock.com/docs/v3/Installation)

對於一個動畫苦手卻又喜歡看特效的人有工具就再好不過了，除了可以自己寫 CSS Animation 以外，還可以使用 GSAP 這個套件來輔助，以下就使用參考文章中的範例來大概解釋一下運作原理

<script src="https://gist.github.com/louis70109/886d43a4a5b8ca1a24429c147fa35baa.js"></script>

- 建立一個 `createText()` 函式讓 Javascript 產生`個別彈幕的 HTML`
- 用`id="button01"`按鈕監聽 **click 事件**來啟動 createText() 函式
- 24, 25 行: 使用亂數並以`視窗上方`(`Top`)為起點增加亂數位置
- 26, 27 行: 加入文字於`子節點`(`子彈`)，再將整個 div 加入於 <body> 中(整個畫面)
- 針對特定 id 的 `<div>子彈` 進行動畫(右至左)，`duration` 則是移動速度
- 31 行: 跑到最左邊後要把`子彈`刪除

## 讓 Websocket 連結 Chatbot 跟前端吧！

首先先說明一下 Chatbot 這部分，一般來說寫 Chatbot 都是使用 Web API 的形式接收 Webhook 事件，但因為彈幕是即時性的且現在需求無需儲存文字，因此就使用 Websocket 來溝通前後端啦！

> NodeJS Webhook 寫法參考這篇: [JavaScript | WebSocket 讓前後端沒有距離](https://medium.com/enjoy-life-enjoy-coding/javascript-websocket-%E8%AE%93%E5%89%8D%E5%BE%8C%E7%AB%AF%E6%B2%92%E6%9C%89%E8%B7%9D%E9%9B%A2-34536c333e1b)

那我是怎麼讓 Chatbot Webhook 事件透過 Websocket 送出去呢？答案很簡單，參考[這份程式碼](https://github.com/louis70109/Screen-LINE-Bullets/blob/master/chatbot/index.js)或`下方 Gist` 第`14、15行`，我設定了`BULLETS`、`USER_AVATAR` 兩個全域變數，再透過 65 行把 Socket Server 與 API Server 綁在一起，接著第 67~82 行的 Websocket

<script src="https://gist.github.com/louis70109/fa0ae938a4b6f141e95191ff910a959e.js"></script>

## 在本地端啟動專案

- chatbot: Heroku or ngrok

## 彈幕與 OBS 融合

- 網頁提到最高層

# 結論

這還只是很陽春的功能，還沒有後台可以調整各種內容，

對直播設定有興趣，請參考[如何只使用一台 Mac 進行直播 feat. SoundFlower, OBS, Youtube](https://nijialin.com/2020/11/29/mac-stream-soundflower/)

# 活動小結

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：@line_tw_dev
![](https://www.evanlin.com/images/2020/line-tw-dev-qr.png)

# 關於「LINE 開發社群計畫」

LINE 今年年初在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來察看最新的狀況。詳情請看:

- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
