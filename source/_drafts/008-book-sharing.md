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

若放在 Head tag 上，可能會發現 Vue 沒有效果，因為瀏覽器還沒解析放入 <body> 中，因此要加入 `DOMContentLoaded` 來加入監聽事件。

```javascript
const vm = Vue.createApp({...});

document.addEventListener("DOMContentLoaded", ()=>{
  // When DOM ready.
  vm.mount('#app')
});
```

重新定義模板語法(避免`{{}}`被使用)：

```javascript
const vm = createApp({
  delimiters: ['%{','}%'],
  ...
})
```

避免環境污染：淺拷貝 vs 深拷貝:

```javascript
{...data}
```

vs

```javascript
JSON.parse(JSON.stringify(data));
```

盡可能避免使用 `_` 與 `$`，因會與 Vue 的核心內容衝突

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
