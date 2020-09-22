---
title: 讓我們開始使用 Cypress 為 LIFF app 編寫單元測試
categories: 學習紀錄
tags:
---

![](https://nijialin.com/images/2020/cypress-liff/logo.png)

# 前言

大家好，本文將帶大家開始使用 Cypress 為您的 LIFF（LINE 前端框架）Application 寫單元測試，它非常容易撰寫。並且可以從本文的範例中幫助
來閱讀這篇文章的朋友。若之前沒有嘗試過開發 LIFF App，建議您首先閱讀以下文章。因為在本文中可能會有很多技術術語，因此在使用它們之前必需要有 LIFF App 開發的基礎知識。

> Article: https://medium.com/linedevth/liff-v2-release-85fdfb678cc6

<!-- more -->

# 使用 LINE 平台進行 LIFF 應用測試的主要問題

我相信每個開發人員都會以不同的方式測試 LIFF App。根據我在 LIFF App 進行自動化測試的經驗中，我遇到了很多問題。因此我想總結以下 3 個常見問題：
![](https://nijialin.com/images/2020/cypress-liff/1.png)

1. LIFF App 和 LINE Platform 具有很高的依賴性：例如，假設我們要使用 liff.getProfile() 這個 API，則需要先重新導向讓使用者進行 LINE Login，然後才能使用它。如此一來控制 LINE Login 就很困難。這樣情況下很容易變成 Flaky Tests（“ Flaky Tests” 是一項運行且會導致某些測試結果失敗的測試）無需修改任何代碼）

> 去年 DevDay 有議程提到類似的部分，可以[參考文章](https://nijialin.com/2019/11/22/How-we-continuously-delivery-LINE-TODAY-App-with-high-agility-and-high-quality/)

2. 根本無法模擬反向測試測試：例如，假設我們要測試何時 liff.init() 並且想碰巧 Promise Reject 檢查我們的應用程序是否可以處理這種情況 我覺得很難。還是做不到比正常測試更好的
3. 像在移動 LINE Native App 上運行 LIFF App 一樣模擬環境非常困難：有時我們的 LIFF App 對於每個平台可能會有不同的使用行為，例如在 LINE App 和外部瀏覽器上運行。桌面可能具有不同的設計 UI 或功能，它們的工作方式有所不同。現在，我們如何簡化在這些環境中的測試仿真，我認為有時候這確實很困難？

> 從以上所有問題 可以使用 Cypress 作為工具對 LIFF App 進行單元測試來進行編輯和實現。

對於那些以前從未聽說過賽普拉斯的人，您可以閱讀我之前寫過的[介紹文章](https://medium.com/cypress-io-thailand/%E0%B8%A3%E0%B8%B9%E0%B9%89%E0%B8%88%E0%B8%B1%E0%B8%81-cypress-web-test-framework-%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B8%88%E0%B8%B0%E0%B8%97%E0%B8%B3%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B8%84%E0%B8%B8%E0%B8%93%E0%B8%A5%E0%B8%B7%E0%B8%A1-selenium-%E0%B9%84%E0%B8%9B%E0%B9%84%E0%B8%94%E0%B9%89%E0%B9%80%E0%B8%A5%E0%B8%A2-405a11d7341)。

很多人可能會了解賽普拉斯是否僅適用於端到端測試？答案根本沒有！由於賽普拉斯可以在單元測試，集成測試和端到端測試中進行任何級別的測試，所以今天我將帶大家來看看如何使用賽普拉斯進行單元測試。與使用其他框架相比，有什麼優勢？

# 讓我們開始吧

本文中的一個示例 我選擇使用 Vue.js 開發 LIFF App。

![](https://nijialin.com/images/2020/cypress-liff/2.png)
我通過使用 vue-cli 和 Config Project 作為手動選擇功能來創建一個新項目，如下所示。

```sh
sh$ vue create liff-cypress-unit-tests
Please pick a preset: Manually select features
Check the features needed for your project: Babel, Router, Linter
Use history mode for router? (Requires proper server setup for index fallback in production) Yes
Pick a linter / formatter config: Airbnb
Pick additional lint features: Lint on save
Where do you prefer placing config for Babel, ESLint, etc.? In dedicated config files
Save this as a preset for future projects? No
```

重要的是賽普拉斯創建了一個名為賽普拉斯 Vue 單元測試 插件的插件，以幫助我們輕鬆地在 Vue.js 應用程序上編寫單元測試。

在檜 [VUE 單元測試](https://github.com/bahmutov/cypress-vue-unit-test)是建立在[官方 Vue 的單元測試](https://github.com/bahmutov/cypress-vue-unit-test)庫的基礎上 VUE 測試 - utils 的。但是使用它可以在真實的瀏覽器以及賽普拉斯的所有出色功能上運行

我們也可以通過 [vue-cli](https://cli.vuejs.org/guide/cli-service.html) 安裝此插件。為了使用此插件，您將需要使用 **Cypress 4.5.0** 和 **Node.js 8** 或更高版本。

```sh
Save this as a preset for future projects? No
```

該插件將自動將 Cypress 添加到您的項目中，並創建一個任務，`test:components`其中包括 Cypress 的基本配置。因此，您也可以輕鬆地運行單元測試 Vue 組件。

![](https://nijialin.com/images/2020/cypress-liff/3.png)
![](https://nijialin.com/images/2020/cypress-liff/4.png)
![](https://nijialin.com/images/2020/cypress-liff/5.png)
![](https://nijialin.com/images/2020/cypress-liff/6.png)
![](https://nijialin.com/images/2020/cypress-liff/7.png)
![](https://nijialin.com/images/2020/cypress-liff/8.png)
![](https://nijialin.com/images/2020/cypress-liff/9.png)
![](https://nijialin.com/images/2020/cypress-liff/10.png)

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
