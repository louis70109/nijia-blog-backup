---
title: 【TypeScript】從頭建立屬於你的 TypeScript 專案
tags:
  - TypeScript
  - nodejs
categories: TypeScript
date: 2020-09-04 22:07:47
---


## 為什麼選擇 TypeScript？

雖然在動態語言中打滾了許久(Ruby ➡️ JavaScript ➡️ Python)，但對於型別定義這件事情還是一直耿耿於懷，而打滾的過程中也曾經寫過 Golang，隨後因為在 Chatbot 社群中接觸了 [Bottender](https://github.com/Yoctol/bottender) 並認識到了 TypeScript，因此改寫了第一個 Side Project - [圖奇獸](https://github.com/louis70109/Twitch-Bot) 為 TypeScript，深深的被 TypeScript 吸引過去，不僅擁有動態語言(JS)的彈性，又能有型別檢查(Type System)與介面(Interface)來輔助開發，在開發上都能~~滿江紅~~有滿滿的提示避免出錯，這也是型別檢查會帶來的好處(先天的 Linter)，只是往往都是靠人家 cli 來幫我 init project 卻沒動手做過，就借本篇來逐步初始化 project。

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

安裝 TypeScript 以及讓 Node.js 支援型別的套件

```
npm install typescript @types/node
```

安裝完之後接著就用 `tsc` 來幫忙初始化 tsconfig (TypeScript 的設定檔)

```
npx tsc --init
```

完成後使用 `ls` 來看看自己的檔案數量是否遇我的一樣
![npm tsc](https://nijialin.com/images/2020/npm-tsc.png)

接著就用編輯器打開這個資料夾開始更改(我用 VScode)，打開 tsconfig.json 後會看到一片密密麻麻的註解，找到 `outDir`(Output directory) 後將它移除註解並改成 `./dist`，讓之後 TypeScript 編譯完的檔案自動放在 dist 這個資料夾下。

![tsconfig](https://nijialin.com/images/2020/tsc-config.gif)

接著因為開發時需要幫忙 Reload，這邊就安裝 [ts-node](https://www.npmjs.com/package/ts-node) & [nodemon](https://www.npmjs.com/package/nodemon) 至 devDependencies 中(只在開發時才使用的套件)。

```
npm install ts-node nodemon --save-dev
```

安裝完套件之後就是來修改 script 裡面的內容，這邊 key 的內容即是你打 `npm run OOO` 裡面的內容：

- build: 從 TypeScript 編譯成 JavaScript。
- dev: 開發環境使用的指令。

```javascript
"scripts": {
    "build": "tsc",
    "dev": "nodemon index.ts"
  },
```

接著我們在本地端建立一個 `index.ts` 並且輸入以下範例：

```typescript
export function showTotal(first: number, second: number): number {
  const total: number = first + second;
  console.log(`The total is: ${total}`);
  return total;
}

showTotal(100, 200);
```

接著就可以執行 `npm run dev` 看看輸出結果，改動 showTotal() 裡面的值來測試一下是否正常 reload 喔！
![npm dev](https://nijialin.com/images/2020/npm-run-dev-1.png)

# 結論

這篇就快速紀錄一下從一個乾淨的資料夾到建立環境來測試 TypeScript 的過程，接下來預計會帶入 Express + LINE Frontend Framework(LIFF) 來實際操作 API 與前端溝通的內容，並說明處理相關設定的問題。

# 參考

- [Node.js](https://nodejs.org/zh-tw/download/)
- [ts-node](https://www.npmjs.com/package/ts-node)
- [nodemon](https://www.npmjs.com/package/nodemon)
- [從零開始在 Windows 使用 Node.js 打造專屬於你的 LINE Bot 聊天機器人](https://medium.com/@EtrexKuo/%E5%BE%9E%E9%9B%B6%E9%96%8B%E5%A7%8B%E5%9C%A8-windows-%E4%BD%BF%E7%94%A8-node-js-%E6%89%93%E9%80%A0%E5%B0%88%E5%B1%AC%E6%96%BC%E4%BD%A0%E7%9A%84-line-bot-%E8%81%8A%E5%A4%A9%E6%A9%9F%E5%99%A8%E4%BA%BA-173ac0f6be92)
- [3 步建立 Typescript 開發環境](https://medium.com/@peterchang_82818/typescript-example-%E6%95%99%E5%AD%B8-tutorial-%E7%AF%84%E4%BE%8B-%E9%96%8B%E7%99%BC-%E6%95%99%E5%AD%B8-%E5%88%9D%E5%AD%B8%E8%80%85-%E7%92%B0%E5%A2%83-nodejs-javascript-react-js-3%E6%AD%A5-888fa8033fc7)
