---
title: "[研討會心得]  2020 六月 LINE 平台更新整理與 LINE Group/Room Chatbot 的展示"
categories:
  - 研討會心得
tags: ["研討會心得", "DevRel", "LINE"]
---

![all user](https://nijialin.com/images/2020/chatbot-taichung-008/IMG_4651.jpg)

# 前言

大家好，我是 LINE Taiwan 的 Tech Evangelist - NiJia Lin。這次很開心受到 chatbot 社群的邀請，參加了 "[中部人的 Chatbots Meetup 聊天機器人小小聚 #8](https://chatbots.kktix.cc/events/chatbots-meetup-in-central-taiwan-008)" 的聚會活動，並且分享 LINE API 更新與個人開發的心得。在此也跟各位分享本次參與的心得，並且也希望透過社群分享的力量能夠讓聊天機器人的開發動能更加的盛大。

- 社群 Chatbots Meetup： [https://chatbots.kktix.cc/](https://chatbots.kktix.cc/)
- 本次活動網頁: [活動網址](https://chatbots.kktix.cc/events/chatbots-meetup-in-central-taiwan-008)

由於 Chatbots Meetup 本身屬於社群自主性的活動，裡面也有許多社群朋友所贊助的閃電秀。裡面的所有內容也是相當的難得與有趣。也希望能夠透過本篇文章讓大家稍微了解 Chatbots Meetup 社群閃電秀的魅力。

這次活動總算又回到 LINE 台灣的辦公室來舉辦，同時這也是疫情後 LINE 辦公室第一次舉辦線下的聚會。希望透過這次的聚會可以讓更多朋友了解到打造自己的聊天機器人是如此讓人開心的事情。

### 投影片

<script async class="speakerdeck-embed" data-id="5fe13412f6ac4959a2bc468a90aa5b10" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這次主題主要圍繞著三個平台實作

- LINE: 提供 機器人(Bot)/網頁(LIFF)/通知(Notify) 的服務
- Heroku: 部署的主機，會含有 Domain/服務套件(SQL、排程)
- GitHub: 放置程式碼的倉庫

搭配我已經寫好的專案: [LINE-subscribe-open-data-bot](https://github.com/louis70109/LINE-subscribe-open-data-bot)

> 整體使用 flask/Python 3.7、PostgreSQL 實作，若想在本地端起服務的話要有這兩個喔！

<script async class="speakerdeck-embed" data-slide="9" data-id="5fe13412f6ac4959a2bc468a90aa5b10" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

在 Fork 專案到自己的帳號下之後，往下會找到 `Deploy to Heroku` 按鈕，按下去之後會到達設定名稱的畫面

<script async class="speakerdeck-embed" data-slide="10" data-id="5fe13412f6ac4959a2bc468a90aa5b10" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這邊會需要加入兩個 Heroku 套件來輔助這次的實作：

- Heroku Scheduler
  - 輸入：`python scripts/sync_to_sql.py`
  - 輸入：`python scripts/notify_me.py`
- Heroku Postgres

<script async class="speakerdeck-embed" data-slide="13" data-id="5fe13412f6ac4959a2bc468a90aa5b10" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

環境變數

```
LINE_CHANNEL_ACCESS_TOKEN=
LINE_CHANNEL_SECRET=
LINE_NOTIFY_CLIENT_ID=
LINE_NOTIFY_CLIENT_SECRET=
LINE_NOTIFY_REDIRECT_URI=
LIFF_BIND_ID=
LIFF_CONFIRM_ID=
LIFF_SHARE_ID=
DATABASE_URL=postgres://USER:PASSWORD@127.0.0.1:5432/postgres
```

- 圍繞三個平台 LINE Heroku, Github
- add template to send url for everyone by dai
- Heroku scheduler need to verify credit card
- LINE messaging api/LIFF/Notify
- how to build an open source flow
-

# 閃電秀 - 我要奮發向上！聊天機器人有哪些書？

<iframe src="//www.slideshare.net/slideshow/embed_code/key/qc23PODCp5yDfj" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/jarsing/lightning-talk-chatbotbooks-20200822" title="我要奮發向上！聊天機器人有哪些書？" target="_blank">我要奮發向上！聊天機器人有哪些書？</a> </strong> from <strong><a href="https://www.slideshare.net/jarsing" target="_blank">佳新 陳</a></strong> </div>

身為主辦人 & LINE API Expert 幫大家整理目前市面上有的書，雖然資訊迭代速度很快，想想有些時候我們都窩在網路上太久，若能好好地透過書籍溫習一下 Chatbot 知識也很讚喔！

### 總結:

希望透過這個 LINE Group/Room Demo Bot 可以讓開發者們更了解如何使用群組與聊天室的相關 API ，開發出更有創意的聊天機器人。

### 關於活動其他聽眾的分享:

- [【Chatbot Taiwan 20】這次參加我又學到了什麼呢 @ LINE](https://nijialin.com/2020/06/24/chatbot-meetups-20-sharing/)

## 活動小結

社群分享永遠是讓創意激盪的最佳方式，而 Chatbots Meetup 是一個很熱情與充滿創造力的社群組織。也希望有更多有創意的開發者願意加入 LINE Chatbot 的開發行列，更希望能熱情的參與社群的活動與一起來分享。

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：[@line_tw_dev](https://lin.ee/s5RsZHo)

![](http://www.evanlin.com/images/2020/line-tw-dev-qr.png)

## 關於「LINE 開發社群計畫」

LINE 今年年初在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來察看最新的狀況。詳情請看:

- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
