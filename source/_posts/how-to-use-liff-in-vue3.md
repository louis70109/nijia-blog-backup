---
title: 在 Vue3 中引入 LIFF 的 ShareTargetPicker 分享 FlexMessage 訊息給 LINE 好友
categories: Vue
date: 2020-09-12 13:44:16
tags: ["Vue", "LINE", "LIFF", "ShareTargetPicker"]
---

![](https://engineering.linecorp.com/wp-content/uploads/2020/09/1-1.png)

# 前言

身為技術推廣工程師必定是要跟上時代的潮流來試玩 Vue 3，主要是因為最近寫了一個 Side Project - [Announcer](https://github.com/louis70109/Announcer) 讓我可以再公布訊息時可以發送漂亮的樣板，而使用 Node.js 開發時因為需要使用 [LIFF](https://developers.line.biz/en/reference/liff/) 的 [ShareTargetPicker](https://developers.line.biz/en/reference/liff/#share-target-picker)，當時只透過 [EJS](https://ejs.co/) 幫我產生 html template 來發送 FlexMessage，一開始認為應該不會寫太多前端的邏輯，但隨著想增進更多的 UX 因此需要操作更多的前端邏輯(可以看看[這個 tag](https://github.com/louis70109/Announcer/releases/tag/v1-ejs) 裡的 views 資料夾)，但曾經寫過 Vue 2 的我當然不可能重新造輪子！同時也隨著最近參加 [Vue.js 社群聚會](https://engineering.linecorp.com/zh-hant/blog/vue-taiwan-006-sharing/)與大家聊到 Vue 3 已經可以先使用，因此就展開我 migrate EJS ➡️ Vue3 的路程了 😆，本篇就給大家多一點相關的使用介紹！

> FlexMessage 詳細介紹可以參考這篇 - [Flex Message 的 Update 1 已公開](https://engineering.linecorp.com/zh-hant/blog/flex-message-update1/)

<!-- more -->

# 介紹

> 範例專案在此: [GitHub](https://github.com/louis70109/liff-2_4-demo)

首先呢，就使用 vue 官方建議的 command line 來建立一個新的專案，名稱為 `liff-2_4-demo`:

```
vue create liff-2_4-demo
```

輸入之後就可以選擇要哪個模式，這邊我們選擇 `Vue 3 preview`
![vue init](https://nijialin.com/images/vue3/vue-init.png)

建立好了之後畫面如下，接著就用 `cd liff-2_4-demo` 進入資料夾開始
![vue init ok](https://nijialin.com/images/vue3/vue-init-ok.png)

接著分別安裝 Vue Router 以及 LIFF 套件讓後續開發比較順利些

```
npm install vue-router@next @line/liff
```

接著預設會給一個 `HelloWorld` 的 component，將之沿用並在 `src/` 下建立一個 `router` 資料夾，接著在 router/ 下建立一個 index.js 並加入以下的內容開始使用 Vue3 Router:

<script src="https://gist.github.com/louis70109/4c7ea0635e6f79af5ffb6f4781d87383.js"></script>

```javascript
import { createRouter, createWebHistory } from "vue-router";
import HelloWorld from "../components/HelloWorld.vue";
const routerHistory = createWebHistory();

const router = createRouter({
  history: routerHistory,
  routes: [
    {
      path: "/liff/template",
      component: HelloWorld,
    },
  ],
});

export default router;
```

> 若你在 Vue 3 使用 Router 的過程有問題的話可以[參考這篇文章](https://nijialin.com/2020/09/10/debug-vue3-router/)

Router 這邊處理好後就接著來處理 LIFF。接著進入到 `HelloWorld.vue` 的檔案中，找到 props 的部分將它置換成 `setup(){}`

> 關於 composition API 的使用方法請參考[這個網址](https://composition-api.vuejs.org/#basic-example)

```javascript
export default {
  name: "HelloWorld",
  setup() {},
};
```

## liff.init()

接著因為 LIFF 啟用時需要先 init ([參考](https://developers.line.biz/en/reference/liff/#initialize-liff-app))，在 Vue 這邊就選擇放在 `Mounted` 下，並且搭配著 async/await 來簡化一下 liff 的 sample code，可以選擇自己喜歡的方式去寫 🙂(對 Promise 不熟的話可以[參考這篇](https://nijialin.com/2020/06/13/learn-javascript-promise/))：

```javascript
import { onMounted } from "vue";
import liff from "@line/liff";
// ...
setup(){
  onMounted(async () => {
    try {
      await liff.init({ liffId: "123456-abcedfg" }); // Use own liffId
      if (!liff.isLoggedIn())
        liff.login({ redirectUri: window.location.href });
    } catch (err) {
      console.log(`liff.state init error ${err}`);
    }
  })
}
// ...
```

```javascript
onMounted(() => {
  liff
    .init({
      liffId: "123456-abcedfg", // Use own liffId
    })
    .then(() => {
      if (!liff.isLoggedIn()) liff.login({ redirectUri: window.location.href });
    })
    .catch((err) => {
      console.log(err.code, err.message);
    });
});
```

在行動裝置開啟 Liff 時會是有登入狀態，而 `if (!liff.isLoggedIn())` 是讓桌機版瀏覽器在進入時可以判斷並導向 LINE 的登入畫面來確保使用者登入的狀態

## liff.ShareTargetPicker()

由於在 掛載(mount)階段已經初始化好 liff 了，接著在這邊就可以直接使用並參考 [ShareTargetPicker](https://developers.line.biz/en/reference/liff/#share-target-picker) 的文件把 code 複製過來並一樣提供兩種使用方法給大家:

```javascript
async function sendTargetPicker() {
  if (!liff.isLoggedIn()) {
    liff.login({ redirectUri: window.location.href });
  }
  if (liff.isApiAvailable("shareTargetPicker")) {
    try {
      const picker = await liff.shareTargetPicker([
        {
          type: "text",
          text: "Hello, World!",
        },
      ]);
      if (picker) {
        // succeeded in sending a message through TargetPicker
        console.log(`[${picker.status}] Message sent!`);
      } else {
        const [majorVer, minorVer] = (liff.getLineVersion() || "").split(".");
        if (parseInt(majorVer) == 10 && parseInt(minorVer) < 11) {
          console.log(
            "TargetPicker was opened at least. Whether succeeded to send message is unclear"
          );
        } else console.log("TargetPicker was closed!");
      }
    } catch (error) {
      // something went wrong before sending a message
      console.log(error);
      console.log("Flex Message got some error");
      liff.closeWindow();
    }
  } else console.log("Please login...");
}
```

若不習慣用語法糖的話可以用原本的範例：

```javascript
function sendTargetPicker() {
  if (!liff.isLoggedIn()) {
    liff.login({ redirectUri: window.location.href });
  }
  if (liff.isApiAvailable("shareTargetPicker")) {
    liff
      .shareTargetPicker([
        {
          type: "text",
          text: "Hello, World!",
        },
      ])
      .then(function (res) {
        if (res) {
          // succeeded in sending a message through TargetPicker
          console.log(`[${res.status}] Message sent!`);
        } else {
          const [majorVer, minorVer] = (liff.getLineVersion() || "").split(".");
          if (parseInt(majorVer) == 10 && parseInt(minorVer) < 11) {
            // LINE 10.3.0 - 10.10.0
            // Old LINE will access here regardless of user's action
            console.log(
              "TargetPicker was opened at least. Whether succeeded to send message is unclear"
            );
          } else {
            // LINE 10.11.0 -
            // sending message canceled
            console.log("TargetPicker was closed!");
          }
        }
      })
      .catch(function (error) {
        // something went wrong before sending a message
        console.log("something wrong happen");
      });
  }
}
```

把這個 function 貼上去之後就加上 html 標籤來呼叫 `sendTargetPicker` 函式:

```html
<button @click="sendTargetPicker">Send Sample</button>
```

## 使用 Ngrok 建立一個含有 SSL 的暫時性網址

這邊使用 `npx` 來啟動 ngrok 的服務，避免安裝於全域污染環境(更多的使用方式[參考 npm](https://www.npmjs.com/package/npx)) ⬇️

```
npx ngrok http --region ap --host-header=rewrite 8080
```

![ngrok](https://nijialin.com/images/ngrok.png)

- Vue 預設輸出的 port 為 8080
- `--region`: 換個區域增加測試時的穩定性
- `--host-header=rewrite`:本地端測試時必須複寫 header，否則將能遇到 `Invalid Host Header` 的問題
  - 參考[ stackoverflow ](https://stackoverflow.com/questions/45425721/invalid-host-header-when-ngrok-tries-to-connect-to-react-dev-server)上的解答：

兩種使用方法:

```
ngrok http 8080 -host-header="localhost:8080"
ngrok http --host-header=rewrite 8080
```

到這裡測試環境已經啟動的差不多了，接著就來建立 LINE Login channel：
![login channel 1](https://nijialin.com/images/2020/vue-use-liff/login-create-1.png)

選擇完最左邊的 channel 之後並依序填入相關資訊，並選擇 `web app`：
![login channel 2](https://nijialin.com/images/2020/vue-use-liff/login-create-1.png)

待建立完成之後到 LIFF 的頁籤中新增(`Add`)一個 LIFF page，將剛剛使用 ngrok 建立的網址貼上只 Endpoint Url 輸入框並接著網址輸入`/liff/template`:
![](https://nijialin.com/images/2020/vue-use-liff/liff-create-1.png)

新增完 LIFF page 後要將 Channel `Published` 以及啟動 `ShareTargetPicker` 按鈕，並將下方的 LIFF url 複製起來貼到瀏覽器上
![publish login info](https://nijialin.com/images/2020/vue-use-liff/login-publish-liff-info.png)

輸入之後 LIFF 會自動 mapping 到剛剛輸入的 Endpoint url，首先在剛進入時因為在掛載(mount)階段，所以會先執行 `liff.init()`
![login page](https://nijialin.com/images/2020/vue-use-liff/login-page.png)

登入之後會導回到以下的畫面：
![vue page](https://nijialin.com/images/2020/vue-use-liff/liff-test-page.png)

按下按鈕之後會被引導到 `好友`/`群組`/`聊天室` 的分享頁面(可複選)：
![share to friends](https://nijialin.com/images/2020/vue-use-liff/liff-share-info.png)

分享之後就看到成果啦 🎉
![share message to group](https://nijialin.com/images/2020/vue-use-liff/liff-test-result.png)

這部分因為 demo 的關係只送出簡單的文字，若想送出很漂亮的樣板可以參考 [FlexMessage](https://developers.line.biz/en/docs/messaging-api/using-flex-messages/)，並且也有相關的線上工具 - [Simulator](https://developers.line.biz/flex-simulator/) 讓大家可以產生出自己要的樣板喔！

```javascript
{
  type: "text",
  text: "Hello, World!",
}
```

## Bonus

之所以會一直使用這個判斷式是因為有 IAB(In App Browser) 以及 External Browser 兩種模式，在情境不同時必須先確認有登入過 LINE 才可以使用之後的功能，否則很容易搞不清楚導致開始除錯後才發現沒確認這部分而浪費很多時間。

```javascript
if (!liff.isLoggedIn()) {
  liff.login({ redirectUri: window.location.href });
}
```

# 結論

以往只能讓 Chatbot 回應 FlexMessage，而現在能透過 LIFF 使用 ShareTargetPicker 是否有煥然一新的感覺呢？讓發訊息的身份不會只被綁在 bot 身上，使用者本身也能共用 FlexMessage，透過這篇帶大家逐步使用 Vue3 試玩 LIFF 的新功能，若大家有使用經驗、作品、問題的話歡迎至 [Chatbot 社群](https://www.facebook.com/groups/chatbot.tw/)分享喔！讓大家互惠一同建造出 WOW 的 Side Project 吧！🙂
![picker result](https://nijialin.com/images/2020/vue-use-liff/picker-result.png)

# 參考

- [ShareTargetPicker](https://developers.line.biz/en/reference/liff/#share-target-picker)
- [stackoverflow](https://stackoverflow.com/questions/45425721/invalid-host-header-when-ngrok-tries-to-connect-to-react-dev-server)
- [FlexMessage](https://developers.line.biz/en/docs/messaging-api/using-flex-messages/)
- [Simulator](https://developers.line.biz/flex-simulator/)
- [LIFF v2 API](https://developers.line.biz/en/reference/liff/)
