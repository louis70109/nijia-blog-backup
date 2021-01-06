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

# 焦點回顧

## [LINE TAIWAN TECHPULSE Keynote](https://speakerdeck.com/line_developers_tw/line-techpulse-2020-keynote) / Marco Chen

![](https://nijialin.com/images/2020/techpulse/keynotw-1.jpg)

主軸：

## New Norma(新常態)

<script async class="speakerdeck-embed" data-slide="7" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

今年因為疫情，從全球、地區、公司、甚至到你我的生活中皆被影響。而 LINE 是以網路服務為基礎的通訊軟體也因為大家使用網路的需求量變多，在平台上也獲得了成長，整理如下：

- 官方帳號上`三月與四月`相比成長了 `140%`
- 視訊電話`二月到五月`上漲 `235%`
- LINE TODAY 的`中華職棒(CPBL)`一度閉門比賽，讓線上直播成長了 `74%`
- 因為藝人們紛紛尋找線上直播的解決方案，因此直播的人數也是大大的提升
- 國內旅遊一度被影響到相當嚴重，但適逢疫情舒緩以及連假，LINE TRAVEL 一度成長了 `24 倍`之多！

# `Verda Kubernetes Service`(`VKS`)

## 台灣工程團隊的考量點

<script async class="speakerdeck-embed" data-slide="9" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

雖然 LINE 時常應付大流量在各服務間均已經有相對應的策略，但隨著公司的成長同時 LINE 工程團隊也需要優化基礎設施，讓平台在接受這麼大的流量可以更`有效地使用資源`，並且提供更穩定的基礎設施來增加`彈性`與`可用性`。

因為在此之前出現了兩個問題`使用效率`與`維護性`，因為為了應付`流量高峰`而是先準備了許多資源，且因為每個服務會與不同的技術元件相依，導致無法經驗交流分享。在這之後我們意識到只有`作業系統虛擬化平台`還不夠，我們需要一個`執行環境虛擬化平台`，把應用程式與其相依性資源封裝起來。才能完全解決應用層與執行環境的區隔，讓應用程式可以任意的被部署在不同地方，而不會有資源相依性與版本衝突的問題。

<script async class="speakerdeck-embed" data-slide="12" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

與此同時，LINE 總部正在著手建立 `Verda Kubernetes Service`(`VKS`)，提供一個平台讓全球服務能夠使用，雖然這時 Container-based 的架構熱度非常高，但要建立一個平台絕對是有所考量，在開發時則考量以下三個部分：

- `靈活性`: 需要能夠自由擴充管理功能。
- `易用性`: 擁有許多生態系資源與 Open Source Software 可以使用。
- `維護成本`: 開發社群的活躍度，如果有 Bug 需要能很快被修復。

<script async class="speakerdeck-embed" data-slide="13" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

而在總部建置 VKS 時，台灣的工程部門團隊因為流量上升而收到很多新專案的開發需求，為了有效利用人力資源，我們正在研究如何強化開發與部署的效率，並在研究如果更好運用 Kubernetes。

當給台灣工程團隊有二個中長期目標：

- 部署效率
- 自動擴展(Auto-Scaling)

## 策略

<script async class="speakerdeck-embed" data-slide="15" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

在有一定規模下要引入一個新技術，許多東西需要持續優化改進，因此在這次的引入中組成了專案小組(Task Force)，讓原本服務間無法有效共用元件的問題逐一排除。首先，須先讓各個團隊對於 Kubernetes 有一定的認知，因此從`讀書會`-`準備教材`-`課程訓練`，經由一個這樣的週期讓學員可以對於技術有一定的掌握度，與此之後並成立了 SRE 團隊，協助排除日後專案中所遇到的問題，記錄下來讓經驗得以傳承，並與海外同事一同合作讓這平台更穩定。

## 成果

<script async class="speakerdeck-embed" data-slide="18" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

經過 Marco 詳細的敘述，除了原先預定的兩個方向`部署效率`以及`Auto-Scaling`以外，我們又額外獲得了兩個好處，不僅擁有更多的監控、追查問題工具，也讓系統微服務化，協同開發時相互影響的問題也降低了。

## 小結

如果你對於 DevOps 或容器化相關技術有興趣可以前往這兩個社團：

- [Cloud Native Taiwan User Group](https://www.facebook.com/groups/cloudnative.tw)
- [DevOps Taiwan](https://www.facebook.com/groups/DevOpsTaiwan/)

# LINE CLOVA

<script async class="speakerdeck-embed" data-slide="8" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

經過了一年的努力，將旗下兩大 AI 主力的品牌 LINE BRAIN 與 LINE Clova 整合成 LINE CLOVA，統整出 AI 產品與兩大解決方案：

- 產品：

  - CLOVA Chatbot
    - 讓用戶可以在很短的時間內建造出一隻 LINE AI Bot，除了有基礎的樣板之外，還能夠客製化調整調整內容格式，並同時支援六種以上的功能。
  - CLOVA Face(臉部辨識)
    - <script async class="speakerdeck-embed" data-slide="25" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>
  - CLOVA OCR(Optical Character Recognition)
    - OCR 能用在什麼地方呢？透過這張簡報應該就有想法了：
      - <script async class="speakerdeck-embed" data-slide="19" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

- 解決方案：
  - eKYC
    - 結合 Face 與 OCR 打造的解決方案，例如：用戶持有健保卡想看診，透過此解決方案可以讓系統自動填入一些基本資訊，減低手動輸入的成本
      - <script async class="speakerdeck-embed" data-slide="22" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>
  - AiCall 可以看以下影片，會讓你更有感喔！

<iframe width="560" height="315" src="https://www.youtube.com/embed/x5gt2sjnfh4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# CLOVA Develop - Cid

<script async class="speakerdeck-embed" data-slide="28" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這部分就由 Cid 說明這次 TECHPULSE 2020 的報到流程究竟是怎麼快速實現的。在大會前相信大家都有收到資訊並上傳自己的人臉，Server 這邊則會將資訊轉交給 CLOVA 做訓練，並於大會當天讓大家可以在櫃檯掃描並達到快速入場的效果。

<script async class="speakerdeck-embed" data-slide="33" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

由於 LINE 有許多相關的活動有入場的需求，當我們只要開發一個即可使用到各個場域，降低開發成本同時也提升使用者入場的消化速度。

> 若讀者對於成為「合作夥伴」的話，可以使用[這個表單](https://tw.linebiz.com/contact-us/inquiry-partner)來申請。

<script async class="speakerdeck-embed" data-slide="41" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃＃

接下來 Marco 就介紹 Verda 這個屬於 LINE 的雲端基礎設施平台，過往還在以`虛擬主機(VM)`為基礎設施時時常會需要預防高峰流量而多準備機器避免意外發生，只是在策略上開發團隊需要更注意`使用效率`與`維護性`的問題，因此這部分就在敘述從`虛擬主機`轉移到`容器化`的過程。

<script async class="speakerdeck-embed" data-slide="12" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

雖然說大家都認為 Container-based 的架構很讚，但要建立一個平台絕對是有所考量，而 LINE 總部在建立 Verda Kubernetes Service 時則考量以下三個部分：

- `靈活性`: 需要能夠自由擴充管理功能。
- `易用性`: 擁有許多生態系資源與 Open Source Software 可以使用。
- `維護成本`: 開發社群的活躍度，如果有 Bug 需要能很快被修復。

而總部在建立 VKS 的同時台灣團隊也正在嘗試各種可能性，並研究如何強化與部署的開發效率，以及有效地使用人力資源，同時也設立了兩個主要目標， `新人能立即加入開發`、`服務需 Auto-Scaling`

綜合所有考量後，採用了 Container-Based 的架構來整合服務

<script async class="speakerdeck-embed" data-slide="18" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

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
