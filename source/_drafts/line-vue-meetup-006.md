---
title:
  "[object Object]": null
categories: 學習紀錄
tags:
---

![](https://i.imgur.com/0QAGPDc.png)

# 前言

- nuxt config
- 英文 西班牙文
  要額外跟 i18n 說明他什麼時候要用什麼語言
  用 router 去拿到
  會考慮到要不要 lazy loading
  定義什麼期望下用什麼檔案
  為什麼 Today 要用到
  2500 個訊息需要被轉換
  泰國喜歡玩樂透 所以有特別使用模組來做
  若工程師一開始看到會不知道要怎麼處理
  因此有 i18n 來讓工程師更快的進入
  全部幫在 async component 裡面調整 timeout, delay 之類
  nuxt i18n 會幫忙對應語系

問題一
page speed only 60% - already best.....QQ

要怎麼解決
700 多個 message 可不可以切碎讓載入加快
分類不同的 component .movie

JSON size 切碎還是差不多的結果 兩個會差不多

切到 100 的時候效果比較好
但需要 merge 時會拖累時間

solution2

在 production 才發生的問題 ＳＳＲ
nuxt 的機制 第一次是正常的 但被 async 影響到 html message

SSR & CSR
做個判斷若在 SSR 時處理掉，避免訊息重複

problem3

webpack 包裝成兩種不宜樣的東西
官方建議 export default
所以會把第一個誤以為是 object

module 則會 JSON parse
google V8 有背書 json parse 比較快

大的拆成小的
拆成 100keys 是合理的範圍
別多 loading
SSR import 完所有的 whole
CSR 建議每次都獨立去哪 每個 component 獨立處理
用 JSON parse 的速度比原生的還快

nuxt 預設就用 vuex 處理，所以不用擔心

巢狀在 merge 會很花時間，所以都是單層攤平來處理

LINE 後台有有個地方可以讓大家去維護

台灣的垃圾太複雜，因此 module 沒辦法共用

i18N 都只有單純文字，若有連結的話會另外處理避免 ＣＯＲＳ

<!-- more -->

# 介紹

# 結論

# 活動小結

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：@line_tw_dev
![](https://i.imgur.com/gxHgAzB.png)

# 關於「LINE 開發社群計畫」

LINE 今年年初在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來察看最新的狀況。詳情請看:

- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
