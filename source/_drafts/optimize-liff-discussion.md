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

![](https://nijialin.com/2020/images/1.png)

# 前言

<!-- more -->

# 介紹

## HTML - link

```html
<link rel="preload" as="script" href="super-important.js" />
<link rel="preload" as="style" href="critical.css" />
<link
  rel="preload"
  as="font"
  crossorigin="anonymous"
  type="font/woff2"
  href="myfont.woff2"
/>
```

## CSS mask

## JS preload

```js
Use Case 3: Decouple Load from Execution
用 JavaScript 動態觸發 preload，預先下載好，等到需要時才執行：(Source)

function downloadScript(src) {
  var el = document.createElement("link");
  el.as = "script";
  el.rel = "preload";
  el.href = src;
  document.body.appendChild(el);
}

function runScript(src) {
  var el = document.createElement("script");
  el.src = src;
}
```

# preconnect

# 結論

引用：
preload 告訴瀏覽器：「這份資源對目前的頁面是必要的，請用最快的速度下載此資源。」
preconnect 告訴瀏覽器：「這個網頁將會在不久的將來下載某個 domain 的資源，請先幫我建立好連線。」
prefetch 告訴瀏覽器：「這資源我等等會用到，有空的話幫我先下載」。

# References

- [[教學] 深入淺出 Preload, Prefetch 和 Preconnect：三種加快網頁載入速度的 Resource Hint 技巧](https://shubo.io/preload-prefetch-preconnect/)
- [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content)
