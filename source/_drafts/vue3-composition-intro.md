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

![](https://nijialin.com/images/2021/)

# 前言

在 Vue 3 出來之後我有嘗試了一下新的功能，結合 LIFF 做了一個 side project - [Announcer-Vue](https://github.com/louis70109/announcer-vue)，當然也有寫了一篇相關使用的文章 [在 Vue3 中引入 LIFF 的 ShareTargetPicker 分享 FlexMessage 訊息給 LINE 好友](https://nijialin.com/2020/09/12/how-to-use-liff-in-vue3/)，那既然會用了，當然也要來了解一下一些 Composition API 的介紹，那以下就是我去參加 Kuro 的簽書會所聽到的內容。

<!-- more -->

# 介紹

新版本一出，大家就會想嚐鮮使用新版本，但這邊講者提到若開發需求需要支援 IE 時請勿當先行者直上 Vue3([文章有提到](https://book.vue.tw/appendix/migration.html#vue-2-x-%E8%87%B3-3-0-%E5%BF%AB%E9%80%9F%E5%8D%87%E7%B4%9A%E6%8C%87%E5%8D%97))

- Vue3：透過 [Proxy API](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy) 來綁定 getter/setter，但因為 IE 不支援 Proxy API，因此若需要處理到 IE 就請用 Vue2。([相關參考](https://stackoverflow.com/questions/64836337/using-vue-3-in-ie11/64837153))
- Vue2 是透過 [Object.defineProperty](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty) 實作，看到[瀏覽器相容列表](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty#%E7%80%8F%E8%A6%BD%E5%99%A8%E7%9B%B8%E5%AE%B9%E6%80%A7) IE 是支援的。

除了 IE 支援度問題以外，目前就我所知 Vue3 向下相容基本上達到九成以上，且也可以在 3 版中套入 2 版的相關 API 實作。


## Html v-for 迴圈 的 key 可以放在父階層

```javascript
<div v-for="item in items">
  <div v-key="index">商品1</div>
  <div v-key="index">商品2</div>
  ...
</div>
```

- Vite 支援 vue 以外的框架
- Vite alias -> config ‘@‘ to an resolve path
- 會有 tpye=‘module’

- Vue3 掛載都是在 createApp() 後面一直接著 .use() 後再掛置 #app

- Store.commit -> mutation

- 用 composition api 做類似 vuex 會遇到的問題
  - 設計的方式不是來處理共享的元件
  - 解決過去都使用 mixin 的作法，在同個 component 會有機會衝突，在 life cycle 中很容易互相影響 component
  - 需要使用 reactive 去 hook 相關數值

每個 component API 都有自己的 data, method, compute - 在個別去 import 避免在北改時影響到其他的頁面

- Use inject and provide to hook like Vuex mutation, reactive data like store

# 結論
