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

![](https://nijialin.com/images/2021/coscup/keynote/1.JPG)

# 前言

<!-- more -->

# 什麼是 COSCUP?

[COSCUP](https://coscup.org/2021/zh-TW/) 是亞洲最大的開源會議之一，自 2006 年開始由開源社群舉行的年度會議，也是台灣自由開源軟體運動 (FOSSM) 的主要倡導者。COSCUP 包含演講、贊助商、社群攤位，以及 BoF 社群同樂會等，COSCUP 的宗旨在於提供一個聯結開放原始碼開發者、使用者與推廣者的平台。

> 可惜今年因為疫情關係改為線上，但也不減大家參與 COSCUP 的熱情！

<script async class="speakerdeck-embed" data-slide="3" data-id="98f89fa9638e48bfbbeaff2bcd9d9653" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

參與社群活動一直是我很喜歡做的事情之一，從演講中分享自己這段日子學習的經驗、攤位上與每位社群朋友交流意見、甚至到坐下來一起研究某段**程式碼/專案**的可行性，而若能在 COSCUP 中分享任何主題對我來說都是一個非常棒的肯定，因此除了在攤位與大家分享外，我也踴躍於 COSCUP 中投稿(2019, 2020)，今年也很榮幸可以代表 LINE 講一場 Keynote！

# Open Up with LINE - From Beginning TO THE NEXT

<iframe width="560" height="315" src="https://www.youtube.com/embed/iaFAOS6XS00?start=37" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

> 歡迎大家收看影片，頻道中也有許多很棒的分享喔！

<script async class="speakerdeck-embed" data-slide="5" data-id="98f89fa9638e48bfbbeaff2bcd9d9653" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

今年是 LINE 的十週年，對於 LINE 來說，過去的十年只是一個開始。 10 週年概念口號 “To The Next” 表達了 LINE 將繼續傾聽用戶的聲音，並在未來 10 年繼續創造更好服務的理念。

## 支持開源專案

<script async class="speakerdeck-embed" data-slide="9" data-id="98f89fa9638e48bfbbeaff2bcd9d9653" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

或許大家很常用也熟知 LINE Chatbot、LINE Login、LIFF 等等的技術與服務，在提供服務之虞 LINE 也花了很多心力建置了許多開源專案，希望藉由分享我們的使用情境、經驗、開源貢獻來幫助每位開發者，在開發的路上能夠更高效、更有彈性的去創造許多創意的產品，以下列幾個讓大家稍微瞭解一下：

> Open Source 的程式碼以及任何內容，都是經由內部縝密的各項審查才可以對外開放，因此大家在使用上不太需要擔心喔～

### [line/armeria](https://github.com/line/armeria)

Armeria 是個讓 Java 開發者能夠使用的微服務框架，在現在容器化這麼盛行，開發上會因應許多技術需要開發，如 gRPC、Spring Boot、Kotlin 一條龍開發等等，都可以透過 Armeria 更輕易使用到許多的技術。像是 http/2、日誌記錄、監控、追蹤也都有提供，並且有 async 架構提供出色的性能跟高併發能力

- 範例專案：https://github.com/line/armeria-examples

<script async class="speakerdeck-embed" data-slide="9" data-id="98f89fa9638e48bfbbeaff2bcd9d9653" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

另一方面，在 2020 年也正式釋出 **1.0 的版本**，1.0 對於大型開源專案來說都是個里程碑，意味著開源專案是能夠 Production。此外還有一個重點，就是有超多 Contributor 第一次貢獻 Pull Request 就是給 Armeria 啦，當然送 Pull Request 除了**新刪修**程式之外，大家也可以從修改文件、增加範例程式開始著手，此舉也可以讓你更快速地學習如何貢獻開源專案喔！

> 更多開源專案細節可以參考此篇文章 [LINE 開發社群計畫: 「手把手教你建立自己的開源專案」](https://engineering.linecorp.com/zh-hant/blog/gdsc-opensource/)

### [Central Dogma](https://github.com/line/centraldogma)

當然還有更多的開源專案大家可以上去查看並使用它們

## 參與開源

### 動手做比較有印象

<script async class="speakerdeck-embed" data-slide="21" data-id="98f89fa9638e48bfbbeaff2bcd9d9653" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

上述提到這麼多開源專案相關的內容，或許大家有疑問，一定要送程式碼才是參與開源嗎？當然有，就是把你所學的內容透過文章/部落格的方式記錄下來，可以是短短的一篇解決某個問題(如上圖)，也可以是一整篇來解釋緣由，並分享到社群上讓更多人知道，可能你現在紀錄的問題，也正好是其他人正在卡關的問題，如果能透過分享的方式幫助到別人，是否也覺得很棒呢？

# 團隊介紹

## Frontend 工程團隊

<iframe width="560" height="315" src="https://www.youtube.com/embed/HGu7jUmxXJA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

LINE 裡有許多服務都是使用 Web 相關技術打造而成的，而作為前端的一份子，就是要讓用戶可以在 Client 端與 Web 端使用起來的體驗一致，以下這些服務你使用時是否也覺得跟 APP 差不多呢？

<script async class="speakerdeck-embed" data-slide="4" data-id="3448a654c505429ba38fb8c1a7f24a65" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

且由於前端產品線很多，許多時候需要打造共用的工具來讓不同服務可以使用共同的元件，把已有成效的解決方案有計畫的打造出來，除了品質統一與避免重造輪子之外，也讓往後新進來的人員能夠有個標準化的內容參閱來維護既有的產品。

<script async class="speakerdeck-embed" data-slide="9" data-id="3448a654c505429ba38fb8c1a7f24a65" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

而接下來公司的方向將會漸漸將重心轉換到自然流量上，因此 Frontend 團隊就會更多處理 **SEO** 與 **Web 效能優化** 相關的工作內容，同時也引入 SSR 以及 AMP 來對齊公司的目標。

<script async class="speakerdeck-embed" data-slide="12" data-id="3448a654c505429ba38fb8c1a7f24a65" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

當然在裡面也會與不同團隊的成員合作，讓產品可以更快速地交付、維護、更安全以外，內部也會透過分享來讓更多團隊了解不同的解決方案的優點。

最後，Frontend 團隊由於成員會持續協助不同專案以及產品的開發，在大家學習到不同的經驗之後也會透過許多的讀書會來分享不同專案間的差異與經驗，藉由交流也讓彼此可以更快速的上手且了解不同專案的屬性。

今年 [Front-end Engineer](https://careers.linecorp.com/jobs/7) 正在擴大招募，尋找在前端領域的高手們來一同來打造驚艷的產品於 LINE 生態系中。

## LINE Pay 團隊

<script async class="speakerdeck-embed" data-slide="4" data-id="3298c104de1646e89c202f575f04fc4f" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

除了大家平常所使用且熟悉的支付服務以外，其實日常也需要處理**金融相關**、**信用卡回饋**等等的專案內容，而從 [TECHPUSE 2020](https://www.youtube.com/watch?v=K9ZHOdjZyug) 之後，LINE Pay 陸續提供了 Extra Service 來達到在地化服務，像是 **我的會員卡**、**廣告投放**與透過**LINE Pay 地圖**讓大家知道到底有哪些商家支援 LINE Pay，不用出門就可以知道可去哪邊使用 LINE Point 回饋點數了。

<iframe width="560" height="315" src="https://www.youtube.com/embed/rndT5K8isww?start=336" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

在日常處理不同的專案之外，LINE Pay 也含有許多內部 PoC 專案，身為工程師一定會有很多想法想用，想實驗很多新學的東西，透過這些專案去驗證想法的可行性，讓想法有機會進入產品之中。

若認同 LINE Pay 文化，歡迎加入 LINE Pay：

- [Front-end Engineer](https://careers.linecorp.com/jobs/76)
- [Server-side Engineer](https://careers.linecorp.com/jobs/75)

> Q: 請問不熟 Java 可以投 LINE Pay backend 嗎? 例如: Python, Go。
> A: 都歡迎來面試，不過可以多花一點時間準備 JAVA 會比較好。

> Q: 請問專案開發，包括 planner, dev, security, qa 總共有多少人執行一個專案？
> A: 實際上人數沒辦法透露，但參與人數會跟專案大小有關。

## LINE TODAY 團隊

<script async class="speakerdeck-embed" data-slide="4" data-id="0e5a937f3ac24af2a3e0c34ddced2ed6" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

作為大家天天會用的主流新聞平台，除了日常提供大家許多新聞相關題材外，其實裡面也含有許多不同的內容，如：**賽事直播**(近期很火紅的 NBA 季後賽也有轉播)、
**電影訂票**、**選情專區**、**泰國限定的樂透**、**電影**...等等，擁有這麼多功能都是為了讓用戶可以在 LINE TODAY 中看到大家最新、最值得關注的內容。

<script async class="speakerdeck-embed" data-slide="11" data-id="0e5a937f3ac24af2a3e0c34ddced2ed6" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

擁有這麼多功能的平台，同時也是一個跨國的產品，同時也提供給泰國、印尼以及香港，為了服務這麼廣大的用戶，在開發流程上也採取了 Large Scale Scrum 的方式([這部分可參考 TECHPULSE 議程](https://www.youtube.com/watch?v=mMF_cwGGze0))來管理這麼龐大的團隊，目前也正積極找 [Frontend](https://careers.linecorp.com/jobs/7)、[Server-Side](https://careers.linecorp.com/jobs/250)、[QA Automation](https://careers.linecorp.com/jobs/18)、[QA](https://careers.linecorp.com/jobs/19) 的工程師，若您對於更詳細的介紹大家可以參考 Recruitment Day 的影片喔！

<iframe width="560" height="315" src="https://www.youtube.com/embed/jlevziTzues" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## LINE 電商團隊

<iframe width="560" height="315" src="https://www.youtube.com/embed/Gf8c4Atkmt0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

電商已成為現代人不可或缺的一部份，在本次的議程中很詳細地透過不同的例子(母親節、送禮優惠...)來解釋在 LINE 電商服務中的不同使用情境，讓大家可以更快速的了解透過 LINE 來購買相關東西時的好處以及可用性。

<script async class="speakerdeck-embed" data-slide="5" data-id="1cfe6d52cca148ff96fc555e41ad1f53" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

接著再透過大家常見的 LINE Point 點數回饋來解釋從 LINE SHOPPING 導購服務中所延伸的整體架構流程，讓大家了解到為了整體的延展性與維護性需要透過怎樣的設計才能夠達到。

<script async class="speakerdeck-embed" data-slide="6" data-id="1cfe6d52cca148ff96fc555e41ad1f53" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

而在電商這麼大的團隊中也與其他團隊一樣，是透過 Scrum 的方式來管理與交付產品，除了有效管理交付內容之外，也可以讓團隊成員以最有效的方式來完成產品內容。

當然團隊裡不可少的 code review 與內部分享會都會有，透過這些流程讓大家在更了解不同成員的思路之外，也能讓團隊中有更多的交流來有效的促進產品的活力！

- [Server-Side Engineer](https://careers.linecorp.com/jobs/250)

## QA 工程團隊

<script async class="speakerdeck-embed" data-slide="2" data-id="9b2a340848894e58bc109bd6f19ab992" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

開場 Richard 帶大家了解 Quality Assurance(QA) 以及 Quality Control(QC) 的差別，很多時候會覺得當產品(服務)要上線前只要讓 QA 測完後就可以上線，而若在上線前的階段才做測試，往往所遇到的問題以及付出的代價都會相對高許多。

<script async class="speakerdeck-embed" data-slide="3" data-id="9b2a340848894e58bc109bd6f19ab992" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

而在 LINE Taiwan QA 部門這邊為了確保整體服務的品質，會在專案早期就參與計劃定製，與 Developer、Design、Planner..等等不同部門的角色一起討論整個流程，協助訂定不同的 Scenario 讓初期的討論可以更加完整。

<script async class="speakerdeck-embed" data-slide="4" data-id="9b2a340848894e58bc109bd6f19ab992" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

而在開發階段時，QA 同仁則會開始建立許多不同情境的測試案例，同時也與 developer 討論相關情境與測試自動化的相關問題，讓 QA 的同仁可以有更好的切入點找出問題，同時也透過自動化讓整體作業更加順暢。

<script async class="speakerdeck-embed" data-slide="7" data-id="9b2a340848894e58bc109bd6f19ab992" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

同時 QA 團隊除了建置自動化流程外，也會打造 CI/CD 輔助優化整體流程。我們透過自動化讓我們獲得了不少的好處。更多精彩內容也歡迎各位參閱影片內容。

<script async class="speakerdeck-embed" data-slide="11" data-id="9b2a340848894e58bc109bd6f19ab992" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

若您對於優化提升品質與以及自動化工程等等的工作內容有興趣的話歡迎參考以下職缺，目前也正如火如荼地找尋優秀人才！

- [QA Automation Engineer](https://careers.linecorp.com/jobs/18)
- [QA Engineer](https://careers.linecorp.com/jobs/19)

> Q: 請問您們用 cypress 自動化測試工具時，有遇到什麼困難點嗎？

1. Cypress 是 Javascript based, 大部分的 QA 需要學習了解 JS 的特性
2. Cypress 不支援 mobile app solution
3. 目前 Cypress 未支援 iframe，官方已經在開發中
4. Cypress 無法進行垮 domain 測試
5. 團隊從 Python / Selenium / Robot Framework 體系切換過來，對 JS 開發生態 / 語法的不熟悉。這個是透過團隊內部的 study group，以及直接找前端同事請益的方式解決

> Q: 當有測試的情境是無法用 cypress 測試時，是如何克服呢

1. 就技術上而言，如果夠了解 JS 相關語言，可以解決蠻多 Cypress 本身的限制。例如上方提到 iframe 的問題，可以運用 jQuery 寫一個 Cypress comment 來處理，抑或是請教前端工程師來協助一同開發 Cypress。
2. 如果是 UX 相關的情境，不得不手動測，自動化的幫助就是把小工具準備好，讓測試執行順暢。
3. 就測試情境上來說，應該蠻多機會會遇到 E2E 需要 cross domain 的 situation．LINE QA 團隊其實會把 test case 維持一個主軸來測試，test case 不會過於複雜，遇到 crosses domain 會運用 mock, stub 等相關 SUT 概念來完成整合測試。

## LINE TECH FRESH 技術新星人才計畫

<script async class="speakerdeck-embed" data-slide="3" data-id="865916ecea2a421587fe956fff64b23d" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

過去在公開活動中，同仁們時常會被詢問：「實習生再加入後是否只能在特定團隊內工作？」，過往有許多同學透過特定專業能力進到實習生計畫中，而我們都很鼓勵每位同學勇於挑戰不同的領域，持續強化不同的專業能力，找尋出自己的想走的道路。

<script async class="speakerdeck-embed" data-slide="7" data-id="865916ecea2a421587fe956fff64b23d" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

除了日常專案與累積技術能力之外，我們很鼓勵透過文章的方式呈現來記錄自己的學習成果，同時也將自己的學習成果分享給未來的學弟妹們，讓大家可以參考學長姐們的結晶，有興趣可以參考以下內容：

- [Life in LINE – 直擊 TECH FRESH 實習內容！](https://engineering.linecorp.com/zh-hant/blog/life-in-line-tech-fresh-sharing/)
- [Life in LINE – 你不知道的 LINE TECH FRESH 實習日常](https://engineering.linecorp.com/zh-hant/blog/line-tech-fresh-2021/)
- [LINE TECH FRESH – 技術新星人才計劃，實習經驗大公開](https://engineering.linecorp.com/zh-hant/blog/tech-fresh-2020/)
- [輕鬆「Go」建事件驅動應用 @ Golang Taipei Gathering #55](https://engineering.linecorp.com/zh-hant/blog/20210226-golang-event-driven/)
- [LINE Developer Day 2020 – The past and future of machine learning research 議程回顧](https://engineering.linecorp.com/zh-hant/blog/line-dev-day-2020-the-past-and-future-of-machine-learning-research/)

<script async class="speakerdeck-embed" data-slide="8" data-id="865916ecea2a421587fe956fff64b23d" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

此外，我們每個月皆會舉辦月會讓實習生可以在固定的時間中與不同專業領域的 Mentor 們聊聊，除了了解前輩們過往的經驗之外，透過交流也可以了解到新興人才們所思考以及顧慮的部分，也讓我們能夠更持續的優化這個計畫的內容。

<script async class="speakerdeck-embed" data-slide="11" data-id="865916ecea2a421587fe956fff64b23d" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

在經過一年的磨練過後，我們也希望菁英同學們有機會加入 LINE 工程部門的大家庭中，一同為 LINE 打造 WoW 的產品給社會大眾，讓你所寫的每一行程式碼都成為大家日常生活的一部份！

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
