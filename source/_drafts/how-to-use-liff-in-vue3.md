---
title:
  "[object Object]": null
categories: 學習紀錄
tags:
---

![](https://i.imgur.com/0QAGPDc.png)

# 前言

身為技術推廣工程師必定是要跟上時代的潮流來試玩 Vue 3，主要是因為最近寫了一個 Side Project - [Announcer](https://github.com/louis70109/Announcer)，使用 Node.js 開發時因為需要使用 [LIFF](https://developers.line.biz/en/reference/liff/) 的 [ShareTargetPicker](https://developers.line.biz/en/reference/liff/#share-target-picker)，並且透過 [EJS](https://ejs.co/) 幫我產生 html template，一開始認為應該不會寫太多前端的邏輯，但隨著想增進更多的 UX 因此需要操作更多的前端邏輯(可以看看[這個 tag](https://github.com/louis70109/Announcer/releases/tag/v1-ejs) 裡的 views 資料夾)，但曾經寫過 Vue 2 的我當然不可能重新造輪子！同時也隨著最近參加 [Vue.js 社群聚會](https://engineering.linecorp.com/zh-hant/blog/vue-taiwan-006-sharing/)與大家聊到 Vue 3 已經可以先使用，因此就展開我 migrate EJS ➡️ Vue3 的路程了 😆，本篇就給大家多一點相關的使用介紹！

<!-- more -->

# 介紹

在寫這篇文章時 Vue router 需安裝 `^4.0.0-beta.9` 的版本
這裡分享我 Debug 的過程

首先我在開啟網頁時[遇到了這個問題](https://github.com/vuejs/vue-next/issues/972):

```
 warning  in ./node_modules/vue-router/dist/vue-router.esm.js

"export 'markNonReactive' was not found in 'vue'
```

[照著這個回答](https://github.com/vuejs/vue-next/issues/972?fbclid=IwAR0zL3QMDIsf0FhNJJQRmesHkNfTrqaJpqT8P1l2PaoKL2b0kXjGJEe42pw#issuecomment-615149911)我到了另一個專案(vue-router-next)的 [commit log](https://github.com/vuejs/vue-router-next/commit/7636f556cd654fbdf49b494925628593e8383453) 中看到了修改，從這更改訊息中就知道改成這個版本應該沒問題...

![vue-router-next-1](https://nijialin.com/images/vue3/issue1.png)

但...你 npm install 的 router 套件專案名稱為 `vue-next`，因此這樣子根本就不對啊！

若是使用 ngrok 來測試的開發者在一開始可以能遇到 `Invalid Host Header` 的問題

參考[ stackoverflow ](https://stackoverflow.com/questions/45425721/invalid-host-header-when-ngrok-tries-to-connect-to-react-dev-server)上的解答：

```
ngrok http 8080 -host-header="localhost:8080"
ngrok http --host-header=rewrite 8080
```

# 結論

- [LIFF v2 API](https://developers.line.biz/en/reference/liff/)
