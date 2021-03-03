---
title: 嘗試透過 Sticker 建立 Sticker-Driven Conversations 的 Chatbot
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

<!-- more -->

![](https://nijialin.com/images/2021/translate/sticker-driven/1.png)

> [翻譯原文](https://medium.com/linedevth/line-chatbot-sticker-driven-conversation-920087b8fe44)

![](https://nijialin.com/images/2021/translate/sticker-driven/2.jpeg)
![](https://nijialin.com/images/2021/translate/sticker-driven/3.png)

<script src="https://gist.github.com/tandevmode/a833ff7ca8b1e2bcd9fcc50770fa6667.js"></script>

```javascript
let keywords = event.message.keywords;
let stickerIntent = "";
for (var i = 0; i <= 2; i++) {
    stickerIntent += randomItem(keywords) + " ";
}
...
function randomItem(items) {
    return items[Math.floor(Math.random() * items.length)];
}
```

```javascript
req.headers['x-line-signature'] = crypto
  .createHmac('SHA256', LINE_CHANNEL_SECRET)
  .update(body)
  .digest('base64')
  .toString();
req.headers.host = 'dialogflow.cloud.google.com';
req.headers['content-length'] = Buffer.byteLength(body, 'utf8');
```

![](https://nijialin.com/images/2021/translate/sticker-driven/4.gif)

<script src="https://gist.github.com/tandevmode/e5045de4e811aa979f86fbf462e8c043.js"></script>

# 4.

```sh
ngrok http 3000
```

![](https://nijialin.com/images/2021/translate/sticker-driven/5.png)
![](https://nijialin.com/images/2021/translate/sticker-driven/6.png)

# 5.

## 5.1

![](https://nijialin.com/images/2021/translate/sticker-driven/7.png)

## 5.2

![](https://nijialin.com/images/2021/translate/sticker-driven/8.png)

## 5.3

![](https://nijialin.com/images/2021/translate/sticker-driven/9.png)

# Demo

![](https://nijialin.com/images/2021/translate/sticker-driven/10.gif)

# Reference

- [揭示如何使 Dialogflow 開發的 LINE Bot 支持 Text 以外的各種事件](https://medium.com/linedevth/%E0%B8%A7%E0%B8%B4%E0%B8%98%E0%B8%B5%E0%B8%97%E0%B8%B3%E0%B9%83%E0%B8%AB%E0%B9%89-line-bot-%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B8%9E%E0%B8%B1%E0%B8%92%E0%B8%99%E0%B8%B2%E0%B8%94%E0%B9%89%E0%B8%A7%E0%B8%A2-dialogflow-%E0%B8%A3%E0%B8%AD%E0%B8%87%E0%B8%A3%E0%B8%B1%E0%B8%9A-events-%E0%B8%95%E0%B9%88%E0%B8%B2%E0%B8%87%E0%B9%86%E0%B8%99%E0%B8%AD%E0%B8%81%E0%B9%80%E0%B8%AB%E0%B8%99%E0%B8%B7%E0%B8%AD%E0%B8%88%E0%B8%B2%E0%B8%81-text-2cae8214c647)
