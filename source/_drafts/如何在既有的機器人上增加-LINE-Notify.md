---
title: 如何在既有的 Bottender chat app 上增加 LINE Notify
tags:
---

# 前言

之前寫了一個 flask 版本的 line notify [範例](https://github.com/louis70109/flask-line-notify)
這次就直接使用我之前的機器人 [Twitch Bot](https://github.com/louis70109/Twitch-Bot)上擴增綁定推播的功能，直接在既有的 Bottender Chat app 上把之前 Python 寫的 Notify 搬過來。
因為機器人初期預設是只有回覆功能，沒有綁定推播，但時常不知道實況主開台的時間導致沒跟到追隨的實況，既然如此就直接做一個推播功能讓我可以訂閱特定直播主而不會錯過實況！😆

# 新增 express

# 註冊 notify

# 建立一個 LIFF

藉由 LIFF 把 user id 放到 state 裡面（需要 state 使用說明）
在 notify callback 回來後會夾帶 code & state，而 state 是我們能控制的
將 user id 放在這的好處在於 Oauth 流程中這個 state 一般都會使用加密過的字串來
剛好 LINE user id 就很適合做這樣的使用
而我們順便藉由 callback 特性讓最後的頁面可以接收到 user id，在藉此去 mapping notify token
最後功能只要倒到對應的使用者 id 就可以進行推播了

> 每個 provider 都會有不同的 user id，所以不用擔心同一個 user id 到別人的 chatbot 上會有外流的問題喔！

# 綁定 Notify 後遇到的 mongoDB 問題

## index

> MongoDB indexes use a B-tree data structure. [[ref]](https://docs.mongodb.com/manual/indexes/#id2)

## Unique

使用 mongoose，目標想讓兩個欄位一起 unique，所以找到了[這篇](https://stackoverflow.com/questions/14283503/unique-documents-using-multiple-values-in-mongoose-schema)

首先先定義 Schema

```javascript
const StreamNotifySchema = new Schema({
  name: { type: String },
  userId: { type: String, index: true },
});
```

接著定義這兩個欄位為 unique

```javascript
StreamNotifySchema.index({ name: 1, userId: 1 }, { unique: true });
```

> ⏰ 這邊有個坑需要注意: 我在還沒找到兩個欄位一起 unique 這個方法前，當時我設定 `userId` 為 unique，之後加上這個方法後卻一直卡在 userId 重複的問題，解決方法就是先把這個 table `drop`掉，重新建立每個鍵值才會正常喔！
