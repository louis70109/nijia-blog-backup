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

## Frontend

做出一個高可用性&彈性的應用程式都會是每位工程師的目標，所需要下的功夫也是要下足，以 TODAY 為例子
Liz 主要負責 LINE TODAY 的前端部分，TODAY 作為新聞網站的主要路口之一，隨著流量越來越大的情況下，效能優化就是很主要的部分，但有主要的兩個挑戰

- 大流量
- 產品架構

同時要注重：

- 彈性
- 效能

效能的挑戰，莫過於該評估現在是否有嚴重的效能問題，或是該把時間投資在其他新 feature 上

這邊以 [First Contentful Paint](https://web.dev/fcp/)(FCP) 作為一個 出現所有 DOM 所需的時間

slide

- 自己做快取
- SEO
- ...

### 彈性

彈性要面對較多與商業邏輯上的問題，處理上也要避免讓程式碼疊床架屋的方式進行



Isomorphic JavaScript
使用 Nuxt.js 來整合，處理上面那些事時可以讓一些事情交給前端做，同時提升效能也可以降低 Backend 的 workload，在這部分前後端使用同個語言也讓整個專案架構相似，藉此增加彈性。

Reuseable SDK 參考 [Workspaces in Yarn](https://classic.yarnpkg.com/blog/2017/08/02/introducing-workspaces/)
## Data dev

運用科技與量化技術來解決行銷通點

## 團隊介紹

### SHOPPING

MLE 來分享在服務中所應用日常的技能，加速整體服務的推薦

這次分享內容與上次不同的是，從 MLE 角度來分享

> 更多請參考[第 14 場 LINE Developers Meetup 活動分享](https://engineering.linecorp.com/zh-hant/blog/line-developer-meetup-14/#LINE-SHOPPING-購物)
### TODAY

座落許多服務於 TODAY 上，已是大家不可學少的一部份

持續優化現有架構，因此需要優秀的人才加入，一起處理台灣的新聞入口服務！

### PAY

應用密碼學於演幾上，並用刷 qr code 三秒的例子讓大家清楚的知道密碼學重要性

### SPOT

Location-based service ，在地化服務，

### AE & SRE

如果讓開發人員與維運人員之前的交付過程更順暢，工程文化在其中佔了很大的比例，有好的環境才有辦法讓整體服務交付更加順暢，並且又有品質保證，是不是很棒呢？

世界再走，工具超多，選擇適合自己團隊的工具將會大大加分

### Verda

LINE 私有雲服務，持續擴大中，去年 COSCUP 有分享，openstack 基底自己打造，對於 Infra 相關非常有興趣的朋友

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
