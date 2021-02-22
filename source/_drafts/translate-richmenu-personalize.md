---
title: 如何以個性化方式在 LINE 中顯示 Rich Menu 以匹配用戶的機器語言
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

![](https://nijialin.com/images/2021/translate/richmenu-personalize/1.png)

在過去的一年中，Rich Menu 上的文章非常受歡迎，它的優點是在用戶聊天頁面上顯示重要的**選單(Menu)**並可以選擇各種操作，降低用戶使用官方帳號的門檻。而對於擁有 LINE 正式帳戶或 LINE Chatbot 的用戶而言，加上創建步驟是相當簡單的，可以透過 [Official Account 後台](https://manager.line.biz/)或是讓具有程式能力的朋友透過呼叫 API 的方式建立 Rich Menu，若能這麼容易就建立 Rich Menu，那麼成為每個帳戶必須具備的基本功能也就不足為奇了。

本文中我將邀請所有人開發一個 Rich Menu，以便能夠顯示出來每個用戶在手機上使用的語系。首先必須知道的是 “**該用戶使用哪種語言？**”，我們可以透過哪種方式獲取用戶手機上的語系，早期我們只能取得 `userId`、`displayName`、`pictureUrl`和`statusMessage`，而現今 LINE 已在用戶的個人資料訊息中添加了一個 **language** 參數以供使用。

到目前為止，我們已經準備好了想法。因此，讓我們看一下開發它的步驟：

1. 準備使用 Cloud Functions for Firebase 開發的 LINE Chatbot
2. 準備**泰語**和**英語**的 Rich Menu
3. 建立條件以獲取 Follow 類型 Webhook 的事件
4. 從用戶個人資料中取得 “**language**” 參數
5. 讓用戶匹配對應語系的 Rich Menu

<!-- more -->

# 1. 準備使用 Cloud Functions for Firebase 開發的 LINE Chatbot

對於從未開發過具有用於 Firebase 的 Cloud Functions 的 LINE Chatbot 的用戶，請遵循以下文章的步驟（1-3 就足夠了），但如果有經驗的話。現在跳到步驟 2 - 準備**泰語**和**英語**的 Rich Menu。

> [使用 Messaging API 和 Cloud Functions 在 Firebase 建置 LINE Bot](https://medium.com/linedevth/%E0%B8%AA%E0%B8%A3%E0%B9%89%E0%B8%B2%E0%B8%87-line-bot-%E0%B8%94%E0%B9%89%E0%B8%A7%E0%B8%A2-messaging-api-%E0%B9%81%E0%B8%A5%E0%B8%B0-cloud-functions-for-firebase-20d284edea1b)

注意：隨著使用 Cloud Functions 開發 LINE Chatbot，因為您需要在 Google 網域外調用 LINE API，Cloud Functions 會要求您從 Spark 切換到 Blaze，但好處是您會在 Blaze 中獲得更多的免費配額。

![](https://nijialin.com/images/2021/translate/richmenu-personalize/2.png)

# 2. 準備**泰語**和**英語**的 Rich Menu

此步驟將根據 [在 LINE 中完成設定 Rich Menu](https://medium.com/linedevth/%E0%B9%80%E0%B8%81%E0%B9%88%E0%B8%87-rich-menu-%E0%B9%83%E0%B8%99-line-messaging-api-%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B8%84%E0%B8%A3%E0%B8%9A%E0%B8%AA%E0%B8%B9%E0%B8%95%E0%B8%A3-6cf12b394f38) 文章將方法分為 3 個子步驟。

## 2.1 使用 Rich Menu Maker 創建 Rich Menu 圖像

讀者可以通過使用兩種語言為 Rich Menu 創建圖像來遵循文章的項目 1 ，在此示例中，圖像將創建 2 張圖像（下載並嘗試）。

![](https://nijialin.com/images/2021/translate/richmenu-personalize/3.jpeg)

> 英文的 Rich Menu 範例

![](https://nijialin.com/images/2021/translate/richmenu-personalize/4.jpeg)

> 泰文的 Rich Menu 範例

## 2.2 使用 LINE Bot Designer 為 Rich Menu 創建 JSON

讀者們可以參考[此篇文章](https://medium.com/linedevth/%E0%B9%80%E0%B8%81%E0%B9%88%E0%B8%87-rich-menu-%E0%B9%83%E0%B8%99-line-messaging-api-%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B8%84%E0%B8%A3%E0%B8%9A%E0%B8%AA%E0%B8%B9%E0%B8%95%E0%B8%A3-6cf12b394f38)的步驟 3 使用 [LINE Bot Designer](https://developers.line.biz/zh-hant/services/bot-designer/) 建立 Rich Menu，透過使用兩種語系(泰語、英語)為 Rich Menu 建立兩個 JSON。

![](https://nijialin.com/images/2021/translate/richmenu-personalize/5.png)

在這個範例中，如果點擊 Rich Menu 則將打開 [LINE Developers 網站](https://developers.line.biz/)。

## 2.3 通過 Messaging API 創建 Rich Menu

請把從上述工法得到的 JSON 和遵循[此篇文章](https://medium.com/linedevth/%E0%B9%80%E0%B8%81%E0%B9%88%E0%B8%87-rich-menu-%E0%B9%83%E0%B8%99-line-messaging-api-%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B8%84%E0%B8%A3%E0%B8%9A%E0%B8%AA%E0%B8%B9%E0%B8%95%E0%B8%A3-6cf12b394f38)的第 4.1 項(Create Rich Menu) 和 4.2 項(Upload Rich Menu Image)，可以使用類似 [Postman](https://www.postman.com/) 的工具來幫助呼叫 LINE API 以建立兩種語系的 Rich menu，其結果一定是 **richMenuId**，而我們需要建立兩次取得泰語與英語的 richMenuId。
![](https://nijialin.com/images/2021/translate/richmenu-personalize/6.png)

> 中文相關內容可以參考
>
> - [Day14 - LINE Richmenu 介紹](https://nijialin.com/2019/09/28/Day14-LINE-Richmenu-%E4%BB%8B%E7%B4%B9/)
> - [Day15 - 串接 LINE Richmenu API](https://nijialin.com/2019/09/29/Day15-%E4%B8%B2%E6%8E%A5-LINE-Richmenu-API/)

# 3. 建立條件以獲取 Follow 類型 Webhook 的事件

當用戶將我們的聊天機器人添加為朋友或取消阻止我們的聊天機器人時，我們將捕獲 Webhook 事件的關注類型，以便根據用戶的機器語言顯示 Rich Menu。

[來自 webhook 事件的 15 個信號將喚醒您的 LINE 機器人。](https://medium.com/linedevth/12-%E0%B8%AA%E0%B8%B1%E0%B8%8D%E0%B8%8D%E0%B8%B2%E0%B8%93%E0%B8%88%E0%B8%B2%E0%B8%81-webhook-events-%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B8%88%E0%B8%B0%E0%B8%9B%E0%B8%A5%E0%B8%B8%E0%B8%81%E0%B9%83%E0%B8%AB%E0%B9%89-line-bot-%E0%B8%82%E0%B8%AD%E0%B8%87%E0%B8%84%E0%B8%B8%E0%B8%93%E0%B8%95%E0%B8%B7%E0%B9%88%E0%B8%99%E0%B8%88%E0%B8%B2%E0%B8%81%E0%B8%A0%E0%B8%A7%E0%B8%B1%E0%B8%87%E0%B8%84%E0%B9%8C-4cb7da653274)

根據上述文章的第 2 點，從 Follow 事件中的有效負載結構中得出。我們感興趣的是兩件事情，events[0].type 並且 events[0].source.userId 因此我們打算寫一個條件並保持價值 userId 這樣的。

```javascript
exports.LineBot = functions.https.onRequest((req, res) => {
  const event = req.body.events[0];
  if (event.type === 'follow') {
    const userId = event.source.userId;
  }
  return null;
});
```

# 4. 從用戶個人資料中取得 “**language**” 參數

在這一步中，我們將使用 `userId` 上一步來識別用戶的語言。讓我們根據以下文章的條款 2.1 檢索配置文件。

[與通過 LINE 中的各種 API 檢索用戶個人資料的位置完全相同。](https://medium.com/linedevth/%E0%B8%A3%E0%B8%B9%E0%B9%89%E0%B8%84%E0%B8%A3%E0%B8%9A%E0%B8%88%E0%B8%9A%E0%B9%83%E0%B8%99%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B9%80%E0%B8%94%E0%B8%B5%E0%B8%A2%E0%B8%A7%E0%B8%81%E0%B8%B1%E0%B8%9A%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%94%E0%B8%B6%E0%B8%87-user-profile-%E0%B8%9C%E0%B9%88%E0%B8%B2%E0%B8%99-api-%E0%B8%95%E0%B9%88%E0%B8%B2%E0%B8%87%E0%B9%86%E0%B9%83%E0%B8%99-line-dafb17e5864a)

因此，我將創建一個像這樣的 getProfile（）函數。

```javascript
const getProfile = (userId) => {
  return request.get({
    headers: LINE_HEADER,
    uri: `${LINE_MESSAGING_API}/profile/${userId}`,
    json: true,
  });
};
```

然後，您可以通過發送變量來調用函數，僅`userId`此而已。

```javascript
exports.LineBot = functions.https.onRequest(async (req, res) => {
  const event = req.body.events[0];
  if (event.type === 'follow') {
    const userId = event.source.userId;
    const profile = await getProfile(userId);
    const language = profile.language;
  }
  return null;
});
```

> 注意：由於我們將不得不等待 getProfile（）函數的回調，因此為了收緊代碼，我使用了 **async / await** 來提供幫助。

# 5. 讓用戶匹配對應語系的 Rich Menu

到最後一步 即根據每個用戶的語言定義豐富菜單。順便說一下，該鏈接將遵循 [LINE 中 Rich Menu](https://medium.com/linedevth/%E0%B9%80%E0%B8%81%E0%B9%88%E0%B8%87-rich-menu-%E0%B9%83%E0%B8%99-line-messaging-api-%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B8%84%E0%B8%A3%E0%B8%9A%E0%B8%AA%E0%B8%B9%E0%B8%95%E0%B8%A3-6cf12b394f38) 文章的 4.6 條，[完成公式](https://medium.com/linedevth/%E0%B9%80%E0%B8%81%E0%B9%88%E0%B8%87-rich-menu-%E0%B9%83%E0%B8%99-line-messaging-api-%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B8%84%E0%B8%A3%E0%B8%9A%E0%B8%AA%E0%B8%B9%E0%B8%95%E0%B8%A3-6cf12b394f38)，我將創建一個函數。linkRichMenu（）並通過傳遞變量 userId 和 language 從上一步獲得的變量進行調用。這就是整個代碼。

<script src="https://gist.github.com/jirawatee/ec8f05a496a2d5b95cedcd059a8a19ea.js"></script>

準備好了，外殼程序，轉到 functions 文件夾並使用命令進行部署

```bash
firebase deploy --only functions
```

然後讓我們看看結果。

![](https://nijialin.com/images/2021/translate/richmenu-personalize/7.gif)

# 結論

可以看到 LINE 已添加 language 到用戶的個人資料 我們可以使用它來創建豐富菜單之外的個性化體驗，例如以用戶語言回復等。我希望本文中的技術將有助於讀者應用。並為您的 LINE 聊天機器人創建 “一見鍾情” 或 “一見鍾情”。
在離開所有人之前，也請按跟隨出版物。這樣您就不會錯過我們的任何新文章 今天我必須先離開 next 下一篇再見。🙏 您好，兄弟姐妹，泰國開發人員。
