---
title: 【翻譯】嘗試透過貼圖建立 Sticker-Driven Conversations 的 Chatbot
categories: 翻譯
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

大家好，我希望 2021 年對每個人來說都是美好的一年 😃，本次會分享一篇對於有在開發 LINE Chatbot 朋友相關的有趣文章。

12 月時，LINE 更新了 Messaging API 的新功能([新聞連結](https://developers.line.biz/en/news/2020/12/02/messaging-api-update-december-2020/))，方法是當用戶將**貼圖**發送給 Chatbot 時，將會從 Webhook 的 `keywords` 中找到貼圖的**關鍵字**訊息。

![](https://nijialin.com/images/2021/translate/sticker-driven/2.jpeg)

# 關鍵字的效果如何？

以前，當用戶發送的貼圖給我們時，從中只能拿到 `stickerId` 與 `packageId`，很難使用它做其他的用途，也因此我們無法理解使用貼圖時的上下文為何。

但如今增加了 `keywords` 這個欄位，它將幫助我們透過 **貼圖**(**Sticker**) 更好地去理解其中含意，了解用戶的意圖或感受(WoW!)

> 注意：`keywords` 欄位最多將只能擁有 15 個關鍵字，並且排序為**雖機**。

# 透過 Sticker 與您的 BMI Chatbot(Dialogflow)對話。

我將在本文中做的是開發給 [Jirawatee](https://medium.com/@jirawatee) 使用的 BMI Chatbot，[Jirawatee](https://medium.com/@jirawatee)希望 Chatbot 透過 Sticker 了解他的需求(Intent)。但眾所周知，Dialogflow 僅支持文字類型的文本，因此我們必須先創建一個 Proxy 幫忙轉譯，然後再將訊息轉發給 Dialogflow。

![](https://nijialin.com/images/2021/translate/sticker-driven/3.png)

由於本篇是屬於半實驗性的開發，因此我將透過 ngrok，將其作為 Local Server，並使用 Node.js 進行開發。主要步驟如下:

1. 建立 LINE Official Account (Chatbot)
2. 使用 Dialogflow 建構 BMI Chatbot
3. 建立 Proxy Server
4. 啟用 ngrok
5. 將 Chatbot 收集到的詞彙添加到 Dialogflow 做訓練

## 1. 建立 LINE Official Account (Chatbot)

如果您以前沒有創建 LINE Chatbot，則可以關注 Pee Tee 的這篇文章。至於是誰做的，您可以跳到下一個項目

## 2. 使用 Dialogflow 建構 BMI Chatbot

如建議的那樣，誰沒有 BMI Chatbot，請仔細閱讀下面的文章。

> 參考此篇文章(泰文)：[了解如何通過 BMI Bot 將 LINE Bot 與 Dialogflow 和 Firebase 集成。](https://medium.com/linedevth/%E0%B9%80%E0%B8%A3%E0%B8%B5%E0%B8%A2%E0%B8%99%E0%B8%A3%E0%B8%B9%E0%B9%89%E0%B8%81%E0%B8%B2%E0%B8%A3-integrate-line-bot-%E0%B9%80%E0%B8%82%E0%B9%89%E0%B8%B2%E0%B8%81%E0%B8%B1%E0%B8%9A-dialogflow-%E0%B9%81%E0%B8%A5%E0%B8%B0-firebase-%E0%B8%9C%E0%B9%88%E0%B8%B2%E0%B8%99-bmi-bot-5a30a672f6ae)

## 3. 建立 Proxy Server

此步驟是使用 Node.js 編寫一個 Web 應用程序，以接收當用戶向我們的 Chatbot 發送消息時 Line 從 Line 發送的 Webhook，然後我們將其解包。`keywords` 創建新消息 並轉發到 Dialogflow

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

創建新的文本類型文本的原則是:

- 正文：我們必須將 Sticker 類型的文本轉換為 Text 類型的文本，以便 Dialogflow 能夠理解它。實際上，我們可以採用所有關鍵字並將其發送。但是，如果仔細看，關鍵字的含義非常廣泛（例如 cony，sally，line，.. 也來），可能會使 Dialogflow 難以解釋 Intent，因此我嘗試了僅 3 個隨機關鍵字發送給 Dialogflow。

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

- Headers：這是一個非常棘手的問題，在上一篇文章中，我們可以 在轉發到 Dialogflow 之前，將 “x-line-signature” 和 “ hosts” 與 “ hosts” 一起使用，但是對於其他使用新 Body 造型的人，我們必須編輯稱為 ' 內容長度'也是！！！

```javascript
req.headers['x-line-signature'] = crypto
  .createHmac('SHA256', LINE_CHANNEL_SECRET)
  .update(body)
  .digest('base64')
  .toString();
req.headers.host = 'dialogflow.cloud.google.com';
req.headers['content-length'] = Buffer.byteLength(body, 'utf8');
```

給我一點鼠標：剛開始，我嘗試轉發，但 Dialogflow（她）沒有連接。我一直都在刷牙。🥺 之後，我來諮詢 Tee Tee。我們在一起坐了好幾個小時 在拍攝結束時，我們發現需要修復。內容長度 只有 ...
![](https://nijialin.com/images/2021/translate/sticker-driven/4.gif)

##＃ index.js 的所有代碼

<script src="https://gist.github.com/tandevmode/e5045de4e811aa979f86fbf462e8c043.js"></script>

# 4. 啟用 ngrok

對於以前從未使用過 ngrok 的新手，我們建議您閱讀這篇經驗豐富的用戶，以在端口 3000 負載下啟用 ngrok！

```sh
ngrok http 3000
```

![](https://nijialin.com/images/2021/translate/sticker-driven/5.png)

然後，像以前一樣，從 ngrok 獲取 URL，並添加 /webhook 放入我們的 Chatbot Channel。

![](https://nijialin.com/images/2021/translate/sticker-driven/6.png)

# 5. 將 Chatbot 收集到的詞彙添加到 Dialogflow 做訓練

Dialogflow 的英雄功能是我們可以輸入每個 Intent 的例句，因為我們選擇的泰文 BMI Chatbotkeywords 都是英文，所以我們也必須訓練更多的詞彙。

## 5.1 默認歡迎意向

![](https://nijialin.com/images/2021/translate/sticker-driven/7.png)

## 5.2 BMI 意圖

![](https://nijialin.com/images/2021/translate/sticker-driven/8.png)

## 5.3 BMI - 自定義 - 是意圖

![](https://nijialin.com/images/2021/translate/sticker-driven/9.png)

# Demo

![](https://nijialin.com/images/2021/translate/sticker-driven/10.gif)

## 得出結論

本文與此相關，提供了一些小技巧，這些技巧增加了一些功能，以使 Chatbot 通過不干膠標籤類型的文本理解用戶的意圖，請嘗試將其一起應用：)
注：關鍵詞實驗階段 - 它 keywords 仍處於試驗階段。將來可能會停止使用或更改

# Reference

- [揭示如何使 Dialogflow 開發的 LINE Bot 支持 Text 以外的各種事件](https://medium.com/linedevth/%E0%B8%A7%E0%B8%B4%E0%B8%98%E0%B8%B5%E0%B8%97%E0%B8%B3%E0%B9%83%E0%B8%AB%E0%B9%89-line-bot-%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B8%9E%E0%B8%B1%E0%B8%92%E0%B8%99%E0%B8%B2%E0%B8%94%E0%B9%89%E0%B8%A7%E0%B8%A2-dialogflow-%E0%B8%A3%E0%B8%AD%E0%B8%87%E0%B8%A3%E0%B8%B1%E0%B8%9A-events-%E0%B8%95%E0%B9%88%E0%B8%B2%E0%B8%87%E0%B9%86%E0%B8%99%E0%B8%AD%E0%B8%81%E0%B9%80%E0%B8%AB%E0%B8%99%E0%B8%B7%E0%B8%AD%E0%B8%88%E0%B8%B2%E0%B8%81-text-2cae8214c647)
