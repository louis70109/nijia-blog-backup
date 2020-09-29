---
title: 讓我們開始使用 Cypress 為 LIFF app 編寫單元測試
categories: 學習紀錄
tags:
---

![](https://nijialin.com/images/2020/cypress-liff/logo.png)

> [原文連結](https://medium.com/linedevth/%E0%B9%80%E0%B8%A3%E0%B8%B4%E0%B9%88%E0%B8%A1%E0%B8%95%E0%B9%89%E0%B8%99%E0%B9%80%E0%B8%82%E0%B8%B5%E0%B8%A2%E0%B8%99-unit-tests-%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B8%81%E0%B8%B1%E0%B8%9A-liff-app-%E0%B8%82%E0%B8%AD%E0%B8%87%E0%B8%84%E0%B8%B8%E0%B8%93%E0%B8%94%E0%B9%89%E0%B8%A7%E0%B8%A2-cypress-%E0%B8%81%E0%B8%B1%E0%B8%99-214f5b0c66b7)

# 前言

大家好，本文將帶大家開始使用 Cypress 為您的 LIFF（LINE 前端框架）Application 寫單元測試，它非常容易撰寫。並且可以從本文的範例中幫助
來閱讀這篇文章的朋友。若之前沒有嘗試過開發 LIFF App，建議您首先閱讀以下文章。因為在本文中可能會有很多技術術語，因此在使用它們之前必需要有 LIFF App 開發的基礎知識。

> Article: https://medium.com/linedevth/liff-v2-release-85fdfb678cc6

<!-- more -->

# 使用 LINE 平台進行 LIFF 應用測試的主要問題

我相信每個開發人員都會以不同的方式測試 LIFF App。根據我在 LIFF App 進行自動化測試的經驗中，我遇到了很多問題。因此我想總結以下 3 個常見問題：
![](https://nijialin.com/images/2020/cypress-liff/1.png)

1. LIFF App 和 LINE Platform 具有很高的依賴性：例如，假設我們要使用 liff.getProfile() 這個 API，則需要先重新導向讓使用者進行 LINE Login，然後才能使用它。如此一來控制 LINE Login 就很困難。這樣情況下很容易變成 `Flaky Tests`（“Flaky Tests” 意指在測試結果中會出現不正常行為的測試）
2. 無法 Simulate Negative Test：假設我們要使用 `Promise` 的`Reject` 測試 liff.init() 並且檢查我們的應用程式是否可以處理各種 Scenario，在一般的測試下很難達到預期效果。
3. 要在 LINE Native App 上模擬與 LIFF App 一樣的環境相當困難。因為有時我們的 LIFF App 對於每個平台可能會有不同的操作行為，例如在 LINE App 和外部瀏覽器上運行。桌面可能具有不同的 UI 設計和功能，它們的運作模式會有所不同。若此時我們想如何簡化模擬這些測試環境，我認為這會相當困難。

> 從以上所有問題 可以使用 Cypress 作為工具對 LIFF App 進行單元測試來進行編輯和實現。

對於那些以前從未聽說過 Cypress 的人，您可以閱讀我之前寫過的[介紹文章](https://medium.com/cypress-io-thailand/%E0%B8%A3%E0%B8%B9%E0%B9%89%E0%B8%88%E0%B8%B1%E0%B8%81-cypress-web-test-framework-%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B8%88%E0%B8%B0%E0%B8%97%E0%B8%B3%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B8%84%E0%B8%B8%E0%B8%93%E0%B8%A5%E0%B8%B7%E0%B8%A1-selenium-%E0%B9%84%E0%B8%9B%E0%B9%84%E0%B8%94%E0%B9%89%E0%B9%80%E0%B8%A5%E0%B8%A2-405a11d7341)。

很多人可能會認為 Cypress 是否僅適用於 End-to-End Test？答案不是！Cypress 可以在 Unit Test、Integration Test 和 End-to-End Test 中進行各種級別的測試，所以今天我將帶大家來看看如何使用 Cypress 進行 Unit Test，並與使用其他框架相比有什麼優勢。

# Let’s Get Started

以下範例我選擇使用 Vue.js 來開發 LIFF App。

![](https://nijialin.com/images/2020/cypress-liff/2.png)
我透過使用 vue-cli 來手動 Config 一個新的專案，如下所示：

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

重要的是 Cypress 創建了一個名為 Cypress Vue unit test 的 plugin，以幫助我們輕鬆地在 Vue.js application 上編寫單元測試。

[cypress-vue-unit-test](https://github.com/bahmutov/cypress-vue-unit-test)是基於 Vue 官方單元測試函式庫 - [vue-test-utils](https://vue-test-utils.vuejs.org/) 所實作的套件。而它可以運行在真實的瀏覽器以及 Cypress 的所有功能上。

我們也可以通過 [vue-cli](https://cli.vuejs.org/guide/cli-service.html) 安裝此套件。為了能夠使用此套件，您需要使用 **Cypress 4.5.0** 和 **Node.js 8** 或更高版本。

```sh
sh$ vue add cypress-experimental # vue-cli > 3
```

該方法會自動將 Cypress 添加到您的專案中，並創建一個 task: `test:components` 並包括 Cypress 的基本配置。因此，您也可以輕鬆地執行 Vue Components 的單元測試。

# 執行 Vue.js App

首先先執行 Vue.js App，確保專案建立是否可以正常運行。

```
sh$ yarn serve
```

![](https://nijialin.com/images/2020/cypress-liff/3.png)

# 加入 LIFF SDK 於 Vue Component 中

我將通過像這樣通過 npm 包輕鬆安裝 LIFF SDK，開始將我的 Vue.js 應用轉換為 LIFF 應用。

```
sh$ yarn add @line/liff // LIFF SDK
sh$ yarn add vue-sweetalert2 // for modal dialog
```

# Test Scenario 1: Initialize LIFF App

首先，在已經透過 vue-cli 建立的專案並在 Component 中初始化 LIFF app。我已經創建了 LINE 登錄頻道，並在 [LINE Developer Console](https://developers.line.biz/console/) 中註冊了 LIFF App。

<script src="https://gist.github.com/nottyo/ad63b1648ec9ee6c96be1a5626ddb31b.js"></script>

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
