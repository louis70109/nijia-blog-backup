---
title: 【標題】題目
categories: 學習紀錄
tags:
---


![](https://nijialin.com/images/2022/)
![](https://nijialin.com/images/common.jpeg)


# 前言

<!-- more -->

# 介紹

## MarTech

開始先提到在行銷上常使用 AARRR 來歸納用戶歷程的漏斗，也因為行銷人員需要在有限的行銷資源下，把資源頭放對的用戶上，進而達到平衡廣告的效益。

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/b10ee31f40924274afb48a8d69f0ada1?slide=9" title="竟然有人說AI不能拿來做行銷" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

接著 Johnson 提到，運用知識圖譜來協助尋找用戶在哪、新用戶在哪、活躍用戶在哪的相關問題，在透過 [Smart Channel(個人化廣告)](https://official-blog-tw.line.me/archives/80236712.html)的方式來投遞給對應用戶相關的資訊，其中也運用語意、卷積網路轉換特徵等等的方式來找到對應關係，也運用這個方法幫助 LINE SHOPPING、LINE SPOT、LINE POINTS...上找出近似關係搜尋，進而提高用戶成長。

## Uplift Model (增益模型)

這邊提到在跟商業團隊討論時，如何優化廣告的效率是很重要的議題，因為一直廣灑的話會有背後成本考量的問題，因此也要衡量廣告帶來的行銷行為。

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/b10ee31f40924274afb48a8d69f0ada1?slide=24" title="竟然有人說AI不能拿來做行銷" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

為了有效的投遞廣告，進而將用戶分眾來提升效益，因此定義了四個族群：

- Sure Thing: 即便不提供誘因，也會購買產品。
- Sleeping Dog: 不投遞還好，一投遞廣告喚醒後，造成負面的影響。
- Lost Cause: 看到廣告(誘因)也不會有反應的族群
- The Persuadable: 容易受到廣告誘因才去購買內容，這部份的人是我們需要的族群

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/b10ee31f40924274afb48a8d69f0ada1?slide=25" title="竟然有人說AI不能拿來做行銷" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

透過上方四個分眾，接著使用 Uplift Model 來找出相關的群眾(A/B testing)，除了增加投資報酬率(廣告有效投放、)之外，也要進而降低官方帳號被封鎖，讓效果可以更有最大的效益。

## CRM

### RFM

接著 Johnson 解釋在平常的購買行為上，是如何透過 [RFM](https://en.wikipedia.org/wiki/RFM_(market_research)) 來了解你的客戶群：
- R：什麼時候來
- F：來的多久
- M：花了多少錢，數量多少

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/b10ee31f40924274afb48a8d69f0ada1?slide=36" title="竟然有人說AI不能拿來做行銷" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

簡化成RFM(衡量用戶歷史價值)＆CLV(用模型估測未來用戶帶來的價值)，個別對不同的用戶下不同的行銷操作，預測接下來收益的提升，增加用戶未來在行銷上的價值。

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/b10ee31f40924274afb48a8d69f0ada1?slide=39" title="竟然有人說AI不能拿來做行銷" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

接著提到 RFM 模型上的切法部分，Data Dev 團隊用了許多方法來找到相關的切法。

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/b10ee31f40924274afb48a8d69f0ada1?slide=46" title="竟然有人說AI不能拿來做行銷" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

也解釋如何透過CLV來計算顧客終身價值，此外，用戶身上都會有RFM以及CLV的標籤，增加後許的行銷策略，讓未來的消費可以在更多一些。

透過RFM...，在透過CLV揭露用戶在未來的消費力

##

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/b10ee31f40924274afb48a8d69f0ada1?slide=53" title="竟然有人說AI不能拿來做行銷" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

因為 LINE 的服務很多，其中也會有許多用戶歷程資料(都是用戶同意的)，並透過 MLOps 把機器學習上在行銷應用上的內容，並讓每個解決方案能夠套用不同的服務與情境。

# 結論

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/b10ee31f40924274afb48a8d69f0ada1?slide=55" title="竟然有人說AI不能拿來做行銷" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

有了模型的輔助，除了幫助行銷同仁可以快速交付決策到市場上，並且也讓開發者在後續開發上能更有彈性以及擴展。

最後，希望透過這次的分享，能夠讓參加這次台大 AI 社課的同學可以更了解 LINE 台灣如何在 MarTech 上運用機器學習解決行銷需求上的一些經驗分享，如果你也喜歡這篇內容，歡迎分享！

# 活動小結

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：@line_tw_dev
![](https://www.evanlin.com/images/2020/line-tw-dev-qr.png)

# 關於「LINE 開發社群計畫」

LINE 於 2019 年開始在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來查看最新的狀況。詳情請看:

- [2021 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2021-line-tw-devrel/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)


<style>
  section.compact {
    font-size: 150%  
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
</style>