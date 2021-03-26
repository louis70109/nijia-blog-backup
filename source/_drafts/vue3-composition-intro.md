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

<!-- more -->

# 介紹

在 Vue 3 出來之後我有嘗試了一下新的功能，結合 LIFF 做了一個 side project - [Announcer-Vue](https://github.com/louis70109/announcer-vue)，當然也有寫了一篇相關使用的文章 [在 Vue3 中引入 LIFF 的 ShareTargetPicker 分享 FlexMessage 訊息給 LINE 好友](https://nijialin.com/2020/09/12/how-to-use-liff-in-vue3/)，

- 若要支援ＩＥ則使用 vue2
    - Else Vue3 -> 約九成 API 都有向下相容
- Html v-for 迴圈 的 key 可以放在父階層


- Vite 支援 vue 以外的框架
- Vite alias -> config ‘@‘ to an resolve path
- 會有 tpye=‘module’


- Vue3 掛載都是在 createApp() 後面一直接著 .use() 後再掛置 #app

- Store.commit -> mutation


- 用 composition api 做類似 vuex 會遇到的問題
    - 設計的方式不是來處理共享的元件
    - 解決過去都使用 mixin 的作法，在同個 component 會有機會衝突，在 life cycle 中很容易互相影響 component
    - 需要使用 reactive 去 hook 相關數值

每個 component API 都有自己的 data, method, compute
	- 在個別去 import 避免在北改時影響到其他的頁面

- Use inject and provide to hook like Vuex mutation, reactive data like store
# 結論
