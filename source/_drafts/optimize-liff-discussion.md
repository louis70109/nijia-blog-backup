---
title: '如何優化你的 LIFF'
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

# What is LIFF?

![](https://nijialin.com/2020/images/optimaze-liff/liff-size.png)

<!-- more -->

# 介紹

## Use html link tag to improve

由於 LIFF 是以 [LINE Login](https://developers.line.biz/zh-hant/docs/line-login/integrate-line-login/#login-%E6%B5%81%E7%A8%8B) 為基底打造的一個**前端框架**，因此他的網址也是使用 `https://api.line.me` 組成，因此在前端優化部分則可以使用 `preconnect` 讓瀏覽器在真正開始渲染之前可以先建立好連線，當開始使用時則不需從頭建立一次，藉此降低些許的 TCP 交握時間。

```html
<link rel="preconnect" href="https://api.line.me" />
```

雖然整體並不會差異太大(可能幾十 ms)，也因為現在設備都很高端因此不會有太大的影響，但在一些極限狀態下時或許預先建立連線或許也會有許多幫助喔！

> 若不清楚`三方交握`建議可以了解一下一個請求進入瀏覽器時所會發生的步驟。

## HTML - link

```html
<link rel="preconnect" href="https://example.com" />

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

## 使用 Async/Await liff 與否的差異

1.

```javascript
function initializeLiff(myLiffId) {
  var start = 0;
  var end = 0;

  start = new Date().getTime();
  liff
    .init({
      liffId: myLiffId,
    })
    .then(() => {
      // start to use LIFF's api
      initializeApp();
    })
    .catch((err) => {
      console.log(err);
    });

  end = new Date().getTime();

  console.log((end - start) / 1000 + ' sec');
}
```

2.

```javascript
async function initializeLiff(myLiffId) {
  var start = 0;
  var end = 0;

  start = new Date().getTime();

  await liff.init({ liffId: myLiffId });
  initializeApp();
  end = new Date().getTime();
  // 計算花多久時間
  console.log((end - start) / 1000 + ' sec');
}
```

將這兩份 code 分別貼進你的 liff app 中，會發現第一份 code 的執行效率較快，原因是因為在 `await` 時會等到整包 liff 都完成後再會做接下來的事情(`initializeApp()`)，而在第一份 code 中因為 liff 會連同 initializeApp() 一起跑完後渲染整個畫面，因此在整體速度上才會優於使用後者，因此若你有需要在 liff.init() 時就要做的事情，建議還是使用第一個寫法喔！

> 當前使用版本為 2.5.0

## Backend 自接自發

因為 liff 設計複雜，

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

雖然 LIFF 很好使用也幫忙 LINE Login，但在取得使用者資訊時千萬別直接使用來自瀏覽器裡存的使用者資訊，如需取得相關訊息請使用 `liff.getIDToken()` 以及 `liff.getAccessToken()` 產生的內容再轉交給你的 Server，避免資安上的疑慮喔

引用：
preload 告訴瀏覽器：「這份資源對目前的頁面是必要的，請用最快的速度下載此資源。」
preconnect 告訴瀏覽器：「這個網頁將會在不久的將來下載某個 domain 的資源，請先幫我建立好連線。」
prefetch 告訴瀏覽器：「這資源我等等會用到，有空的話幫我先下載」。

# References

- [[教學] 深入淺出 Preload, Prefetch 和 Preconnect：三種加快網頁載入速度的 Resource Hint 技巧](https://shubo.io/preload-prefetch-preconnect/)
- [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content)
