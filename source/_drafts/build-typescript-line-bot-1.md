---
title:
  "[object Object]": null
categories: 學習紀錄
tags:
---

![](https://i.imgur.com/0QAGPDc.png)

# 什麼是 TypeScript？

# 前言

趁著最近有個新點子 - [Announcer](https://github.com/louis70109/Announcer)，因為使用 LINE 來當公告的群組也不少，用文字宣達有沒那麼吸睛，因此就想到使用 LIFF 的 [ShareTargetPicker](https://developers.line.biz/en/docs/liff/developing-liff-apps/#share-target-picker) 並開始著手寫 TypeScript，雖然之前有使用過來寫我另一隻機器人 - [圖奇獸](https://github.com/louis70109/Twitch-Bot)，但是基於 [Bottender](https://github.com/Yoctol/bottender) 之上，且套件都已經幫我包好好的，對於從頭起專案這個技能就很陌生，因此接下來就來開始起專案吧！

<!-- more -->

# 介紹

首先你的電腦一定要有安裝 [Node.js](https://nodejs.org/zh-tw/download/)，下載並安裝完後會擁有一個 `npm` 的指令，以下就會使用此指令來起專案。

> 若你是 windows 用戶可以參考卡米哥的文章 - [從零開始在 Windows 使用 Node.js 打造專屬於你的 LINE Bot 聊天機器人](https://medium.com/@EtrexKuo/%E5%BE%9E%E9%9B%B6%E9%96%8B%E5%A7%8B%E5%9C%A8-windows-%E4%BD%BF%E7%94%A8-node-js-%E6%89%93%E9%80%A0%E5%B0%88%E5%B1%AC%E6%96%BC%E4%BD%A0%E7%9A%84-line-bot-%E8%81%8A%E5%A4%A9%E6%A9%9F%E5%99%A8%E4%BA%BA-173ac0f6be92)

建立一個資料夾後並進入剛剛建立的資料夾：

```bash
mkdir typescript-line-bot
cd typescript-line-bot
```

接著就使用 `npm init` 指令來初始化一個屬於你的 package.json，它會詢問很多問題，逐步輸入對應的訊息或使用預設，這份檔案會是之後人家在看 node 專案的第一個入口(相關資訊皆在此)，因此裡面的資訊盡量越詳細越好 🙂！

![npm init](https://nijialin.com/images/2020/npm-init.png)

產生出 package.json 之後接著我[參考這篇](https://medium.com/@peterchang_82818/typescript-example-%E6%95%99%E5%AD%B8-tutorial-%E7%AF%84%E4%BE%8B-%E9%96%8B%E7%99%BC-%E6%95%99%E5%AD%B8-%E5%88%9D%E5%AD%B8%E8%80%85-%E7%92%B0%E5%A2%83-nodejs-javascript-react-js-3%E6%AD%A5-888fa8033fc7)來建立 TypeScript 環境，以下引用一下文章使用方法：

# 結論
