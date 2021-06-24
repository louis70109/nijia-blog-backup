---
title: Vue tw 07
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

大家好，我是 LINE Taiwan 的 Tech Evangelist - NiJia Lin。這次很開心參加了 [v-tw meetup #007 @online ](https://vuejs.kktix.cc/events/v-tw-meetup-007)的線上聚會活動，。在此也跟各位分享本次參與的心得，並且也希望透過社群分享的力量能夠讓不同技術的開發動能更加的盛大。

- [Vue.js Taiwan 社群](https://www.facebook.com/groups/924388564307543)
- 本次活動網頁: [活動網址](https://vuejs.kktix.cc/events/v-tw-meetup-007)


<!-- more -->

# 介紹

## Vue 3 composition API

today 第四個 tab, 各家新聞的集中站，vue+nuxt 打造出來的，
升級到 vue3 需要注意什麼，希望今天的內容在工作上有幫助

怎麼解決現實世界的問題 Composition API

vue 生態系，大部分的工具都已經有做到穩定的版本，也要注意平常使用的生態系中的套件有無支援到 vue3

default 還是 2.0 的版本，vue3 整個 migration 的 guideline ，如果你追求穩定的話可能還是不建議 vue3

全球開發者大會中，可能在 Q3 切換到 vue3 

與QA緊密的合作，即便升級至vue3 ＱＡ也需要大量的工作量
Vue3 絕對不會 support IE11

之後有機會在 vue2 中使用到 composition API, 

現在官方有說 2.7 會支援 composition API

b若有用 class-base componenet 
不推薦往上升級， 卡在這兩個 package, 有出 beta 但目前還不穩定，實際使用問題很多

vite 並沒有跟 VUe 綁在一起，把 vue cli 搬到 vite

migration build 具體是一個 package, 一個 vue3 外掛，幫助 vue3 一些ＡＰＩ行為模擬成vue2
@vue/compat
減少衝突增加容錯率
更厲害的，決定要在 vue 2 or 3 mode, it could be use in diff componenet
部分 component 在2，一些在3
更好地做到 migration，因為不可能一次就改完，這個 package 給你了一些彈性
若有做升級計畫可以使用這個 package


## composition API

提供一些 best practice, 

他解決什麼問題

 component 一些邏輯需要共用

 today 中有許多內容需要共用，讓 module 可以共用

過去最容易遇到 component 的問題, namespace confliction

一直往上去 prop 的問題
today 有許多需要去 fetch article, 有許多 HOC

包裝起來之後讓 code 更好的被共用

幫助我們在寫邏輯時，讓大家在寫ＪＳ時想用何種 function 就用，讓每層關係來實現功能

講者很推薦，推薦 functional programing的方式來學習 hooks 相關的寫法，大家都一直有在靠攏 vue3

> 請問推薦現在用 Vue2 的 composition api module 來撰寫方便之後升級 Vue 3 嗎？
推薦 這也是官方的做法
## vite2

比較舊的瀏覽器無法吃到 ES imports, vite 只是開發工具, 
核心 es module, 一存擋回到瀏覽器就很快，跟 webpack 比較不同
工具是希望他可以支援不同的前端框架

比較不同的是 vite 建立一個ｓｔａｔｉｃ web server ，不編譯直接啟動，開啟請求後直接發送 request, static webserver 才及時編譯更新的部分，最後推送更新

webpack bundled->一直打包重新編譯

vite 只編譯新的部分

node 要在 12 以上

用 type=module 的方式來引入 ES 相關的功能

不需要灌額外的loader
vite沒有loader的概念

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
