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

首先，在已經透過 vue-cli 建立的專案並在 Component 中初始化 LIFF app。並且已經在我的 [LINE Developer Console](https://developers.line.biz/console/) 中註冊 LIFF App。

<script src="https://gist.github.com/nottyo/ad63b1648ec9ee6c96be1a5626ddb31b.js"></script>

# 使用 Cypress 來寫 Vue Component Test

透過 `cypress-vue-unit-test` 提供的 `mount` API 來使用 Cypress 測試 Vue Component 是相當容易的，如此一來我們就可以安裝該套件來對其 Component 進行測試。在這裡我將使用 Cypress 控制 LIFF 的 APIs，按照所需測試使用 [Cypress Stub Feature](https://docs.cypress.io/guides/guides/stubs-spies-and-clocks.html)，讓 liff.init() Stub 時 Promise 總是回傳 resolve。大致如下：

<script src="https://gist.github.com/nottyo/cc86b71c2b597e537ef2888ddd52db53.js"></script>

若 liff.init() 的 Parameters 正確傳送，我們能查看函數的變化嗎？
是的，接著我們可以使用此 Command 進行測試。

```
sh$ yarn test:components
```

Cypress 將啟動 UI Test Runner。

![](https://nijialin.com/images/2020/cypress-liff/4.png)

讓我們選擇 `App.spec.js` 並按 "執行"，我們會看到 **Test Passed**。

![](https://nijialin.com/images/2020/cypress-liff/5.png)

您可以看到在介面上都沒有測試，因為這是一項檢查是否 liff.init() 成功的測試。如此一來很快，不是嗎？

# Test Scenario 2: Negative Test with LIFF SDK

在這次的範例中，我們打算做 LIFF SDK 的 Negative Test 。我會假設如果 liff.init() 的 Promise `Reject` 了 app，我們則須看在 App.vue 的程式碼中使否有 Handle Error。在這份程式碼中我已經使用 try/catch 包裝 liff.init()，在執行失敗時彈出 modal 向用戶顯示錯誤。
通過模擬這種情況下的 Negative Test，我們將像之前一樣再次使用 Cypress Stub，將 liff.init() 設定返回 Promise Reject，可以這樣寫：

<script src="https://gist.github.com/nottyo/fac82631d895d759ad7ea0bcdea64808.js"></script>

使用 Cypress 進行測試時，將看到像這樣彈出 Error Modal。
![](https://nijialin.com/images/2020/cypress-liff/6.png)

# Test Scenario 3: Authentication with LINE Login + Get User Profile

在此範例中，我將建立一個用於顯示 LINE User Profile 的 Component，將使用 `liff.getProfile()` 這個 API 來索取用戶訊息，而在使用此 Component 的 liff.getProfile() 之前須先進行 LINE Login，且同時我還之前先檢查用戶是否已登錄。若此時用戶還沒登入則會在 `liff.login()` 階段被 Redirect 至 LINE Login。

此外，我還使用 `liff.ready` 這個 API 來確認 APP 中的 Component 是否在 liff.init() 階段成功調用至 APP 中。

<script src="https://gist.github.com/nottyo/e4c34130a1fcdb1eb6e996fb7c3cb1fa.js"></script>

# 動手做

為了測試 Profile Component，我必須對屬性進行存根處理，liff.ready 就像它已經 liff.init()成功完成一樣，這是 liff.ready 使它等於 Promise 解析的結果。Cypress.sinon.replace(liff, 'ready', Promise.resolve())像這樣
此外，我們將總是存根 liff.isLoggedIn 返回，true 以便不必像已經登錄一樣使 LINE Login 複雜化。剩下的就是存根 liff.getProfile 返回 promise resolve，並將我們存根的值作為用戶配置文件返回。

<script src="https://gist.github.com/nottyo/fcfab3f6cd4d4c60c469eef406554a26.js"></script>

當運行測試出現時 我們可以看到我們已經用存根用戶配置文件渲染了一個配置文件組件，並且可以使用賽普拉斯命令在 DOM 元素上聲明值。
我們還可以使用命令 `Cypress.vue` 來訪問您的 Vue 實例！而且我們可以使用此命令來檢查 Vue 實例中的各種屬性，例如，在此示例中，我要檢查是否正確存儲了 User Profile Object 值的數據屬性。能跑 `Cypress.vue.$data.<propertyName>`可訪問性很棒，不是嗎？

![](https://nijialin.com/images/2020/cypress-liff/7.png)

# Test Scenario 4: Emulate Opening LIFF App from LINE Native App

在此示例中，我們將模擬打開 LIFF 應用程序的環境，類似於從 LINE 移動應用程序中打開它的環境。我將使用 APIliff.isInClient()來檢查它是否已在 LINE 應用程序中打開，並 liff.getOS()檢查是否什麼平台也正在開放？

<script src="https://gist.github.com/nottyo/363bbd27695312e5d8302b1cbc9d18c7.js"></script>

在編寫測試時，我們對函數`liff.isInClient()`進行存根以始終返回 true 並`liff.getOS()`返回 ios。
此外，我還使用它 `cy.viewport(‘iphone-xr’)`來模擬屏幕大小，就像在移動 iPhone 上運行一樣，賽普拉斯為此準備了一個 [Mobile Viewport](https://docs.cypress.io/api/commands/viewport.html) 預設供我們使用。您可以在此處查看更多信息。

<script src="https://gist.github.com/nottyo/c53bf9410dfe4399db4a9482426c82e9.js"></script>

![](https://nijialin.com/images/2020/cypress-liff/8.png)

# Cypress 與另一個 Unit Test Framework 比較

可以看出，賽普拉斯的優勢在於它可以在真實的瀏覽器上運行，從而支持所有瀏覽器本機 **API**，以及賽普拉斯使之適合進行測試的其他功能，例如 **Time Travel**，**Debuggability**。賽普拉斯可以建立虛擬的單元測試，但是仍然可以以更快的速度運行更快的合酶。
除了 Vue.js，賽普拉斯還支持其他 Web 框架上的單元測試，[React](https://github.com/bahmutov/cypress-react-unit-test)和[Angularjs](https://github.com/bahmutov/cypress-angularjs-unit-test)也可以使用賽普拉斯進行單元測試。
![](https://nijialin.com/images/2020/cypress-liff/9.png)
可以完整查看本文中的所有源代碼示例。在下面的鏈接 如果有人對使用賽普拉斯有疑問，您可以加入 Cypress.io 泰國社區進行諮詢。
我希望本文能為所有開發人員提供一個構想，以開始為我們的 LIFF App 編寫單元測試，以便我們的 LIFF App 可以長期輕鬆維護，並具有良好的代碼質量。幸福的寫作測試，大家快樂的測試！
您可以在下面的鏈接中看到本文的整個源代碼的示例。

> [liff-cypress-unit-tests](https://github.com/nottyo/liff-cypress-unit-test)

![](https://nijialin.com/images/2020/cypress-liff/10.png)

# 參考

- [cypress-vue-unit-test](https://github.com/bahmutov/cypress-vue-unit-test)
- [vue-cli-plugin-cypress-experimental](https://github.com/jessicasachs/vue-cli-plugin-cypress-experimental)
