---
title: 'TECHPULSE 2020 - Keynote'
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

![](https://nijialin.com/images/2020/techpulse/1.JPG)

# 前言

各位好，我是 LINE TAIWAN 的技術推廣工程師 - NiJia Lin，很開心這次能以不同的身份(LINER)來參加於南港展覽館二館舉辦的一年一度 LINE 技術大會 - TECHPULSE，雖然今年很可惜的因為疫情關係無法邀請海外講者來台灣與各位分享，但同時也讓大家了解到 LINE Taiwan 工程團隊實力也是深不可測，這次我也將透過這篇文章讓你了解 LINE 所帶來的魔力吧！

> 在此之前也有分享一篇詳細的文章 - 歡迎大家參考 [您不能錯過的 LINE TAIWAN TECHPULSE 2020 年度盛會](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-techpulse-2020/)

<!-- more -->

呼應到之前介紹的 Face Sign，今年更結合了 CLOVA 的辨識技術讓相片牆
![](https://nijialin.com/images/2020/techpulse/photowall.JPG)

- keynote

# 焦點回顧

## [LINE TAIWAN TECHPULSE Keynote](https://speakerdeck.com/line_developers_tw/line-techpulse-2020-keynote) / Marco Chen

![](https://nijialin.com/images/2020/techpulse/keynotw-1.jpg)

主軸：

## 起因

## 考量點

## 策略

## 成果

- VKS
- CLOVA
- IU -> MLU
- <script async class="speakerdeck-embed" data-slide="2" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

接著由 CTO - Marco Chen 為各位帶來 LINE TAIWAN 開發團隊今年的技術分享，以及 LINE 平台的最新技術發展與應用案例。

今年因為疫情，從全球、地區、公司、甚至到你我的生活中皆被影響。而 LINE 是以網路服務為基礎的通訊軟體也因為大家使用網路的需求量變多，在平台上也獲得了成長，整理如下：

- 官方帳號上`三月與四月`相比成長了 `140%`
- 視訊電話`二月到五月`上漲 `235%`
- LINE TODAY 的`中華職棒(CPBL)`一度閉門比賽，讓線上直播成長了 `74%`
- 因為藝人們紛紛尋找線上直播的解決方案，因此直播的人數也是大大的提升
- 國內旅遊一度被影響到相當嚴重，但適逢疫情舒緩以及連假，LINE TRAVEL 一度成長了 `24 倍`之多！

<script async class="speakerdeck-embed" data-slide="7" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

雖然 LINE 時常應付大流量已經有相對應的策略，但隨著公司的成長 LINE 也需要優化基礎設施，讓平台在接受這麼大的流量可以更有效地使用資源，屏且提供更穩定的基礎設施來增加可用性。

<script async class="speakerdeck-embed" data-slide="9" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

接下來 Marco 就介紹 Verda 這個屬於 LINE 的雲端基礎設施平台，過往還在以`虛擬主機(VM)`為基礎設施時時常會需要預防高峰流量而多準備機器避免意外發生，只是在策略上開發團隊需要更注意`使用效率`與`維護性`的問題，因此這部分就在敘述從`虛擬主機`轉移到`容器化`的過程。

推薦社團:

- [Cloud Native Taiwan User Group](https://www.facebook.com/groups/cloudnative.tw)
- [DevOps Taiwan](https://www.facebook.com/groups/DevOpsTaiwan/)

<script async class="speakerdeck-embed" data-slide="12" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

雖然說大家都認為 Container-based 的架構很讚，但要建立一個平台絕對是有所考量，而 LINE 總部在建立 Verda Kubernetes Service 時則考量以下三個部分：

- `靈活性`: 需要能夠自由擴充管理功能。
- `易用性`: 擁有許多生態系資源與 Open Source Software 可以使用。
- `維護成本`: 開發社群的活躍度，如果有 Bug 需要能很快被修復。

而總部在建立 VKS 的同時台灣團隊也正在嘗試各種可能性，並研究如何強化與部署的開發效率，以及有效地使用人力資源，同時也設立了兩個主要目標， `新人能立即加入開發`、`服務需 Auto-Scaling`

綜合所有考量後，採用了 Container-Based 的架構來整合服務

<script async class="speakerdeck-embed" data-slide="18" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

最後我們獲得了許多好處多了兩個好處，

- 有很多共用的監控，追查問題的工具。
- 讓系統微服務化，協同開發時相互影響變小了

<script async class="speakerdeck-embed" data-slide="24" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

LINE 每天都承受著相當大的流量，超過 2 千萬人

<script async class="speakerdeck-embed" data-slide="33" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

最後一定要提到資訊安全相關的議題，在日常對話中其實 LINE 就透過許多加密手段來確保資料，讓每位使用者在使用 LINE 時可以更安心的使用，

<script async class="speakerdeck-embed" data-slide="34" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

而在近日推出的生物辨識登入，目的就是讓使用者可以不透過密碼靠特徵或指紋即可登入，降低輸入被竊取的風險，更詳細內容可以參考這篇：[不怕忘記密碼了～ LINE 開放「生物辨識」登入，iPad 用戶搶先體驗！](http://official-blog.line.me/tw/archives/84191413.html)

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
