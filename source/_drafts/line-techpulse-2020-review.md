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

- VKS
- CLOVA
- IU -> MLU
- <script async class="speakerdeck-embed" data-slide="2" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

接著由 CTO - Marco Chen 為各位帶來 LINE TAIWAN 開發團隊今年來的戰果。首先因應今年初疫情影響，除了大家都感受到了生活上的一些改變，不僅對大家，對 LINE 以及 LINE 的工程團隊們都有最直接的影響，

- 官方帳號上`三月與四月`相比成長了 `140%`
- 視訊電話`二月到五月`上漲 `235%`
- LINE TODAY 的`中華職棒(CPBL)`一度閉門比賽，讓線上直播成長了 `74%`
- 因為藝人們紛紛尋找線上直播的解決方案，因此直播的人數也是大大的提升
- 國內旅遊一度被影響到相當嚴重，但適逢疫情舒緩以及連假，LINE TRAVEL 一度成長了 `24 倍`之多！

<script async class="speakerdeck-embed" data-slide="7" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

因為 LINE 是以網路服務為基礎的通訊軟體，在新常態中，人們生活習慣改變，使用網路服務的行為也改變了，因此讓 LINE 受到了別與平常的流量，在這環境下雖然公司成長了，但因為需要應付這麼大的流量，勢必得需要提供更穩定的基礎設施來增加可用性。

<script async class="speakerdeck-embed" data-slide="9" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

因此接下來就介紹 Verda 這個屬於 LINE 的雲端基礎設施平台，在當時還沒普及容器化服務時團隊很容易因為預防高峰流量而多準備機器避免意外發生，因此這部分就在敘述從`虛擬主機`轉移到`容器化`的過程

- 推薦社團: [Cloud Native Taiwan User Group](https://www.facebook.com/groups/cloudnative.tw)

<script async class="speakerdeck-embed" data-slide="12" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

但要建立一個平台絕對是有所考量，在建立 Verda Kubernetes Service 時 LINE 總部則就以

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

2.  Life on LINE CLOVA by Aaron Wu https://speakerdeck.com/line_developers_tw/line-techpulse-2020-life-on-line-clova

3.  Platform API Update by Evan Lin https://speakerdeck.com/line_developers_tw/line-techpulse-2020-platform-api-update

<script async class="speakerdeck-embed" data-slide="4" data-id="73943b1c8b0f4dde9a81fd856cf4ab24" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

既然都知道 LINE 了，你怎麼會不知道 LINE Bot 相關的知識呢？今年增加了一個 `Narrowcast` 的相關 API，目的是為了讓開發者可以更快速的使用 Narrowcast 來篩選出適合的受眾，並將訊息精準的發送給他，那大家一定會很好奇它有什麼條件可以使用

- 性別
- 年齡
- 作業系統
- 地區

#### 使用案例

今天你是個手機銷售商，近日剛好有新款手機上市，且依照你們的商業分析得知男性族群消費力比較高此時你可以搜尋台北地區三十歲以上使用 iOS 系統的的男性，透過這樣去行銷你的廣告，符合自家需求並正確地找到你的客戶。

<script async class="speakerdeck-embed" data-slide="6" data-id="73943b1c8b0f4dde9a81fd856cf4ab24" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

### Icon and Display name switcher

> 曾經在 [TECHPULSE 2018](https://www.slideshare.net/linecorp/line-platform-api-update-chatbot) 的演講上有出現過的 Icon Switch 功能，當時受到相當多開發者的詢問。但是由於當時 Icon Switch API 仍然算是 Partner API (指的是需要透過跟 LINE 申請合作的開發廠商，才能使用的功能)，所以能使用的開發者並不多。[參考網址](https://engineering.linecorp.com/zh-hant/blog/chatbot-icon-switch/)

而今年初 LINE 開放了這個強大的 API 給各位開發者，讓大家可以更靈活地使用它來讓你的 Chatbot 更生動！

講者在這部分使用一個例子來說明用途：「經常大家在經營許多店家官方帳號的時候，在一些程式中條件無法正確判斷時，就需要讓客服人員透過官方帳號來回覆使用者的問題，此時使用 Icon Switch 這個 API 即可快速切換身份也同時讓使用者能夠在視窗內快速辨別身份。」

> 「藉由這個 API 也讓使用者可以感覺到 chatbot 不再是個冷冰冰的機器，而是有溫度的互動。」

你可以透過以下範例程式快速實踐 Icon Switch：

- Golang: https://github.com/kkdai/line-bot-icon-switch
- Python: https://github.com/louis70109/line-icon-switch-python

- Emoji
- 取得使用者語系
- Group/Chatroom API
  - name
  - number of people
- Unsend Event
- Video viewing complete

<script async class="speakerdeck-embed" data-slide="14" data-id="73943b1c8b0f4dde9a81fd856cf4ab24" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

- Share target picker

- Channel access token v2.1
- Retry API

### Endpoint API

這部分更詳細介紹可以參考我十月至 Chatbot meetups 的分享文章 - [管理 LINE Bot 相關資訊](https://engineering.linecorp.com/zh-hant/blog/line-api-platform-update-202010/#%E7%AE%A1%E7%90%86-line-bot-%E7%9B%B8%E9%97%9C%E8%B3%87%E8%A8%8A)

### Flex Message Update 2

https://engineering.linecorp.com/zh-hant/blog/line-api-platform-update-202010/#flex-message-update-2

## LIFF

Concate mode

4. Scaling Machine Learning at LINE by Shawn Tsai and Penny Sun https://speakerdeck.com/line_developers_tw/line-techpulse-2020-scaling-machine-learning-at-line

![](https://nijialin.com/images/2020/techpulse/shawn.jpg)
![](https://nijialin.com/images/2020/techpulse/penny.jpg)

[2021 加速轉型 9 大趨勢（六）加速 AI 生命周期循環，MLOps 將成企業 AI 落地規模化的關鍵一步](https://www.ithome.com.tw/news/141978)

#### 下午議程:

1. LINE Pay New Service My Card by Hugo Huang https://speakerdeck.com/line_developers_tw2/line-techpulse-2020-line-pay-new-service-my-card
2. How GitOps Helps
   Kubernetes Adoption by Denny Tsai https://speakerdeck.com/line_developers_tw/line-techpulse-2020-how-gitops-helps-kubernetes-adoption
3. Improve Automated Acceptance Tests through Test Isolations by Bryan Liu https://speakerdeck.com/line_developers_tw/line-techpulse-2020-improve-automated-acceptance-tests-through-test-isolations

更多資訊： https://techpulse.line.me/

### 閃電秀 (Lightning Talks) 投影片集錦：

閃電秀 (Lightning Talk) 一直以來都是技術研討會最精彩的部分之一。

不光是可以在很多的時間內聽到許多有趣的分享，更可以聽到許多精闢的技術分享與摘要。

這次要分享的就是 LINE TECHPULSE 2019 的閃電秀的部分，本次閃電秀分成三大主題，相關投影片依序如下：

1. Lightning Talk - Client Development
   1. LINE LINE SHOPPING App with Flutter by Chia-Cheng Chu (Aaron) https://speakerdeck.com/line_developers_tw/line-techpulse-2020-line-line-shopping-app-with-flutter
   2. Android Message Capturing by Jerry Che https://speakerdeck.com/line_developers_tw/line-techpulse-2020-android-message-capturing
   3. Efficient Event Tracking Mechanism with Flutter by Kuan Wei Lin https://speakerdeck.com/line_developers_tw/line-techpulse-2020-efficient-event-tracking-mechanism-with-flutter
2. Lightning Talk - Client Development
   1. SmartPOI by Johnson Wu https://speakerdeck.com/line_developers_tw/line-techpulse-2020-smartpoi
   2. LDS - Sharing UI Components Between LINE Projects by Petr Mareš https://speakerdeck.com/line_developers_tw2/line-techpulse-2020-lds-sharing-ui-components-between-line-projects
   3. Large Scale Scrum (LeSS) Road, Where does it leads? by William Fu https://speakerdeck.com/line_developers_tw2/line-techpulse-2020-large-scale-scrum-less-road-where-does-it-leads

<script async class="speakerdeck-embed" data-slide="37" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

3. Lightning Talk - TECH FRESH
   1. Life as FRESH LINER by Mandy Chang https://speakerdeck.com/line_developers_tw2/line-techpulse-2020-life-as-fresh-liner
   2. From Classroom Assignment to Realistic Problem in LINE by Troy Chiu https://speakerdeck.com/line_developers_tw2/line-techpulse-2020-from-classroom-assignment-to-realistic-problem-in-line
   3. My Life in LINE : As a Junior LINER, Senior TECH FRESH by Carolyn Chen https://speakerdeck.com/line_developers_tw2/line-techpulse-2020-my-life-in-line-as-a-junior-liner-senior-tech-fresh

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
