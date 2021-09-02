---
title: 【COSCUP throwback】日本團隊分享 | Verda, LIFF
categories: 研討會
tags: ['LINE', 'LIFF', 'Verda']
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

在 COSCUP 的安排中很幸運可以邀請到國外的同仁來為我們分享在當地工作的內容，本次文章則帶大家了解遺下在日本的團隊(Verda + LIFF)的工作內容，如果想回味當天講者實際分享的內容在稍後也可以看 youtube 影片回味一下喔!(當天也是有許多朋友前來詢問許多與日本工作相關的問題，生活、履歷等等)

- 投影片
  - [LINE Verda](https://speakerdeck.com/line_developers_tw/20210801-line-verda-tuan-dui-jie-shao)
  - [Build an mini-app ecosystem for LINE developers](https://speakerdeck.com/line_developers_tw/20210801-build-an-mini-app-ecosystem-for-line-developers)

<!-- more -->

# 介紹

## Verda 團隊分享

<iframe width="560" height="315" src="https://www.youtube.com/embed/iq0nSph2ZNk?start=4734" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

<script async class="speakerdeck-embed" data-slide="3" data-id="4ae92ff6f73b428b92a53f2aca576538" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

過去在 2020 COSCUP 中的 Cloud Native 議程中有分享到類似的內容，Verda 是 LINE 的私有雲服務，提供給 LINE 開發者所需要開發的基礎建設，而在經過了一年的時間機器數量又在更多了，也代表著服務一直在成長，需要更多的機器才能支撐的下

- [COSCUP 2020 年會 – LINE 工程團隊的議程分享](https://engineering.linecorp.com/zh-hant/blog/line-coscup-2020/)

<script async class="speakerdeck-embed" data-slide="4" data-id="4ae92ff6f73b428b92a53f2aca576538" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

而基礎設施的基底則是使用 OpenStack 作為基礎，且做為團隊的一員必須對雲原生的東西有一定的熟悉度，如 Kubernetes、Prometheus、Grafana、CI/CD 流程...諸多的內容

更多的內容可以參考 Verda 團隊的成員們分享的內容: [【Team & Project】Meet the Team Developing the Verda Platform Using OpenStack and Kubernetes](https://engineering.linecorp.com/en/blog/verda-platform-team/)

而作為私有雲的服務，需要提供給內部用戶穩定工具以及介面上的功能給全球的開發者使用，如果你也對於打造國際級企業內的服務，歡迎加入我們喔!

<script async class="speakerdeck-embed" data-slide="6" data-id="4ae92ff6f73b428b92a53f2aca576538" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

## LIFF 團隊

<iframe width="560" height="315" src="https://www.youtube.com/embed/iq0nSph2ZNk?start=7756" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

LINE Frontend Framework 是許多 LINE 開發者每天都會碰到的內容，本次也特邀在日本工作的台灣同仁來分享內容，以下簡錄當天的一些內容，更詳細可以參考以上影片喔！

## 為什麼要有 LIFF 呢?

<script async class="speakerdeck-embed" data-slide="5" data-id="f23e18b74ffa4660b5c76d592e6bf346" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

LINE 其實在 APP 中開發 Web 也有相當久的時間，在之前使用的技術上(底層是 Cordova)因為有一些技術上以及安全性的問題，且要引入到 LINE APP 中也是個負擔，因此在許多的規劃以及考量下就決定重新設計推出 LIFF 這套框架，不光是提供給內部使用，同時也可以推廣給所有目前正在使用 LIFF 的你使用!

當然最重要的就是要提供用戶簡潔與直觀的 API 設計，也避免與 APP 橋接後所遇到的問題。(也就有現在的支援一般瀏覽器的功能啦~~)

<script async class="speakerdeck-embed" data-slide="6" data-id="f23e18b74ffa4660b5c76d592e6bf346" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

因為 LIFF 是使用 JavaScript 開發的框架，因此大家在開發後也無須安裝，



因為有許多 Family Service 都需要網頁的方式去呈現

參考資源:

- [梅竹黑客松賽前企業工作坊 – LIFF shareTargetPicker](https://engineering.linecorp.com/zh-hant/blog/meichu-liff-share-target-picker-workshop/)
- [讓我們使用 Cypress 開始為 LIFF app 撰寫單元測試](https://engineering.linecorp.com/zh-hant/blog/cypress-liff-unit-test/)
- [開啟 LINE LIFF v2 的無限潛力 — liff.shareTargetPicker](https://engineering.linecorp.com/zh-hant/blog/start-liff-v2-sharetargetpicker-power/)
- [在 Vue3 中引入 LIFF 的 ShareTargetPicker 分享 FlexMessage 訊息給 LINE 好友](https://engineering.linecorp.com/zh-hant/blog/how-to-use-liff-in-vue3/)
- [您需要了解有關新 LIFF URL 的所有資訊](https://engineering.linecorp.com/zh-hant/blog/new-liff-url-infomation/)

<script async class="speakerdeck-embed" data-slide="8" data-id="f23e18b74ffa4660b5c76d592e6bf346" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

當中有提到為了讓開發者可以在任何地方開發 LIFF(不管在 **LINE APP** 或是**外部瀏覽器**上)，就會遇到許多瀏覽器上的挑戰，雖然瀏覽器大多都是以 Webkit 方式實作，但實際上還是會有些許的差異需要去做調整，因此就需要花許多時間去處理相對應的問題

> 在這過程中也能對各種的底層更加了解，是個非常棒的經驗!

<script async class="speakerdeck-embed" data-slide="9" data-id="f23e18b74ffa4660b5c76d592e6bf346" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

為了讓 LIFF 開發者的開發體驗(Developer Experience)更棒，也引入了 TypeScript 讓大家可以在開發時更快的使用到 LIFF 相關的 API Snippet、Hint 等等(當然還有開發上的靜態型別檢查的優點)，當然為了減少套件依賴的問題，開發上盡可能以 PureJS 來開發，降低 SDK 的 Bundle Size，當然如一些單元測試、CI、分析工具等也都是有在使用

<script async class="speakerdeck-embed" data-slide="11" data-id="f23e18b74ffa4660b5c76d592e6bf346" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

因為 LINE 非常注重資安問題，用戶在許多地方使用上都會需要同意很多的使用者條款，單然有些時候可能會影響到用戶的使用體驗導致不想使用等等，因此就有提議要降低 bounce rate 的作法(目前還在計畫中)，目標就是要讓用戶可以使用者體驗更棒，讓有需要的地方去執行即可，也是在遵守 Policy 的狀態下執行內容

<script async class="speakerdeck-embed" data-slide="12" data-id="f23e18b74ffa4660b5c76d592e6bf346" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

當中講者也是屬於早期 LIFF 的開發者，了解一些痛點上的內容，未來當然也希望改善開發者體驗上的內容

- 提升維護姓
- 改善測試的架構，讓 QA 可以更好的測試方式去測試
- 目前是一個專屬團隊在開發，當然也希望提供更好的架構讓想貢獻的開發者可以盡一分心力到 LIFF SDK 上，讓不同團隊可以開發出更多屬於自己的 Plugin 等等的內容。
- 規劃提供 Debug Tool、Playground 等等的工具來幫助普羅大眾的開發者們(好期待阿!!)，而不用真的實際串接 LIFF 才能執行。

當然最後如果你希望開發一個網頁框架，它是會在日常再大家手機中執行的內容，歡迎準備好你的履歷投到以下網址喔！

- [LIFF 職缺](https://linecorp.com/ja/career/position/1659)

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
