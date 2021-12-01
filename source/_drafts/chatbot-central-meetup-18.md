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


大家好，我是 LINE Taiwan 的 Tech Evangelist - NiJia Lin。這次很開心受到 chatbot 社群的邀請，參加了 "[中部人的 Chatbots Meetup 聊天機器人小小聚 #18 @ 臉書社團直播](https://hackmd.io/@chatbot-tw/chatbots-meetup-in-central-taiwan-018)" 的聚會活動，並且分享 LINE API 更新與個人彈幕遊戲的開發心得。在此也跟各位分享本次參與的心得，並且也希望透過社群分享的力量能夠讓聊天機器人的開發動能更加的盛大。

- 社群 Chatbots Meetup： [https://chatbots.kktix.cc/](https://chatbots.kktix.cc/)
- 本次活動網頁: [活動網址](https://chatbots.kktix.cc/events/chatbots-meetup-in-central-taiwan-018)
- 本次活動的共筆紀錄： [https://hackmd.io/@chatbot-tw/chatbots-meetup-in-central-taiwan-018](https://hackmd.io/@chatbot-tw/chatbots-meetup-in-central-taiwan-018)
- [簡報連結](https://speakerdeck.com/line_developers_tw/line-platform-update-202111)
<!-- more -->

# 整場影片分享

<iframe width="560" height="315" src="https://www.youtube.com/embed/xaOpNhB0vBs?start=373" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# 彈幕遊戲開發分享

## 後端 FastAPI 在 Docker 中開發(含資料庫)

- 環境孤立化，怎麼弄都跟外面的世界(筆電/PC) 沒關係
- Docker 非常肥，如果有空間考慮開發完記得刪除
<script async class="speakerdeck-embed" data-id="7491b80124ce4c0fa8e1c0a98172b6d2" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

## 實裝 Test Container 於 GitHub Actions 中

- 真實訪問資料庫

- Chatbot 部分
  - 測試階段因 LINE Bot 需要介面操作才有辦法觸發
  - 因此這邊建議可以 Mock LINE Server
  - 抑或是在抑或是在環境變數中設定 LINE Bot 的真實金鑰讓初始化成功
  - Webhook 裡面的用法針對韓式去做測試即可


## Chatbot 在本次的用途

- 透過對話當作簡易的管理介面
- 僅限 admin

# API Update 分享

# 結論

雖然 demo 時還是老樣子 Server 不聽話，只能先架設在本地端讓大家試玩，希望能透過這次的分享讓大家有新的點子以及參考內容來打造更酷很有趣的應用，Chatbot 社群也都非常有活力，歡迎各路好手踴躍前往分享參加。

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
- [2021 年 LINE 開發社群計畫活動時程表 (持續更新)](https://engineering.linecorp.com/zh-hant/blog/2021-line-tw-devrel/)
