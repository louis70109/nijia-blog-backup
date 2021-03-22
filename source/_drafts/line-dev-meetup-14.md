---
title: 【Let’s Play in DataPark】
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

Data in LINE We Are Facing

slide6

在一個資料科學團隊當中，資料量的多寡是一個很重要的課題，資料量越大時所運算出來的資源才會相對正確

- 資料工程師 (Data Engineer)
- 資料科學家 (Data Scientist)
- 資料分析師 (Data Analyst)

以上三個角色的介紹可以參考 [「How ML Powers LINE Services」機器學習如何的讓 LINE 的服務能更貼近使用者](https://engineering.linecorp.com/zh-hant/blog/how-ml-powers-line-services/)

而在 [LINE Developer Meetup 開發者小聚系列活動 #13](https://linegroup.kktix.cc/events/20200918) 之後，經過內部討論之後在流程上多了一個角色:

- 機器學習服務工程師 (ML Service Engineer)
  在完成模型訓練後，要設計並建立可規模化的機器學習服務架構，使模型能夠在線上服務

slide

更詳細團隊介紹可以參考 TECHPULSE 上的影片

<iframe width="560" height="315" src="https://www.youtube.com/embed/YCKYwfGY-Rc?start=290" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

劃分了這麼多角色就是為了在一個 ML 工作流程中的每個部分讓不同角色發揮自己的長才於對應的地方，讓工作的效率大大提升，以下簡單敘述一下每個階段會做的事：

- Prepare：需要用哪些資料、怎麼取得、資料標注等等
- Discover：挖掘資料特徵、尋找適合演算法
- Develop：模型開發、版本控管、實驗 meta data 紀錄
- Train：參數調整、計算資源分配
- Test：模型驗證與分析
- Deploy：部署到線上環境，注重模型效能、硬體計算資源、規模化
- Monitor/Analysis：服務的可靠性。模型 decay、應用模型後所帶來的成效

slide

而在這麼多的服務當中，講者簡單將服務們區分為 MarTech & NLP 兩大塊

- MarTech：利用 ML 來做「以 User 為主」的個人化廣告以及用戶行為預測等等來幫助行銷操作
- NLP：各種「以內容為主」的應用，像是近似文章搜尋、自動擷取文章的關鍵字等等

slide

在資訊爆炸的現代，推薦廣告系統常常會遇到三種族群，「無論如何都支持」、「絕對不支持」、「不打擾沒事，打擾就離開」，因此精準推薦廣告讓資源效益最大化一直是一個課題，因此講者在此開始敘述如何訓練「Uplift Model」，這邊使用柴犬與秋田犬的案例來敘述，並透過每個服務在時間內的成效行為資料來尋找投遞廣告的對象族群。

Uplift By Declines slide

接著敘述 **LINE 購物** (電商聯盟平台，給大家搜尋比價導購賺點的地方)是如何協助使用者在商品海中快速找到你想要的產品，就會是我們在意的地方，因此介紹了 related search, 相關搜尋, 這個推薦模組，他會根據你搜尋的關鍵字，回傳一串推薦關鍵字給你


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
