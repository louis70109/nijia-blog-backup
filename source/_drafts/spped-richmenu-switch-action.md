---
title: 使用 Richmenu Switch Action 將 LINE Personalize 中豐富菜單的切換速度提高到光速
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

![](https://nijialin.com/images/2021/switch-menu/1.jpeg)

相信現在在泰國使用OA（LINE官方賬號）的人，可能沒有人知道Rich Menu或者幫助引導用戶使用我們主要服務的菜單。其中獲得它非常容易，只需使用工具或編寫程序即可完成。
但對於這篇文章 將談論通過編程創建富菜單。這種方法的優點是 用戶可以自行切換富菜單，例如：


<!-- more -->

![](https://nijialin.com/images/2021/switch-menu/2.gif)
從上圖可以看出，當前的Rich Menu切換延遲了很多，因為後面的步驟很多。

![](https://nijialin.com/images/2021/switch-menu/3.png)

1. 用戶按下 Rich Menu 以通過消息或 Postback 操作從聊天室向 LINE 服務器發送請求。
2. LINE 服務器會將 Webhook 事件轉發到我們的 Bot 應用程序。
3. 機器人應用程序處理豐富菜單切換到的 webhook 事件，並將切換請求發送回 LINE 服務器。
4. LINE 服務器將更改請求用戶的豐富菜單。

注意到在切換Rich Menu給用戶看之前，必須有4個請求，當然請求越多，延遲也越高。

---

# 了解 Richmenu Switch Action

**Richmenu Switch Action**是為Rich Menu而生的Action，它會幫助用戶比以前更快地切換Rich Menu，因為發生的請求在Client和LINE服務器之間只有2個請求。
![](https://nijialin.com/images/2021/switch-menu/4.png)

1. 用戶按下 Rich Menu 向 LINE 服務器發送請求。
2. LINE 服務器接受請求並將 Rich Menu 切換到請求用戶。

注意：LINE服務器收到請求後，除了為用戶切換Rich Menu外，同時還會以Postback事件的形式向Bot應用發送Wehook。

關於如何使用 Richmenu Switch Action 創建豐富的菜單，有 4 個步驟。

1. 為 A 型和 B 型準備豐富的菜單。
2. 創建豐富的菜單
3. 自定義豐富的菜單別名
4. 將 Rich Menu 分配給用戶。
5. 其他與 Alias 相關的 API

---

# 1. 為Type A和B準備豐富的菜單

要為 A 和 B 的 Rich Menu 創建圖像，請按照以下文章的第1 步操作。

> [使用 LINE 的 Rich Menu 打造一個食譜選單](https://medium.com/linedevth/%E0%B9%80%E0%B8%81%E0%B9%88%E0%B8%87-rich-menu-%E0%B9%83%E0%B8%99-line-messaging-api-%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B8%84%E0%B8%A3%E0%B8%9A%E0%B8%AA%E0%B8%B9%E0%B8%95%E0%B8%A3-6cf12b394f38)


然後按照上述文章的第3 項為兩個富菜單創建 JSON 。例如，我將 Rich Menu命名為 **richmenu-a**（另一幅名為 **richmenu-b** 的圖像），並將更多按鈕（另一幅圖像為Back按鈕）的區域定義為可點擊。此時忽略操作設置。

![](https://nijialin.com/images/2021/switch-menu/5.png)

> 注意：名稱可以與連字符一起使用，但不得包含空格。

---

# 2. 建立 Rich Menu

在這一步中，取上一步得到的JSON，修改新的Action如下。

```
// Action ของ Rich Menu แบบ A
areas.action.type: "richmenuswitch"
areas.action.richMenuAliasId: "richmenu-b"
areas.action.data: "richmenu=b"
// Action ของ Rich Menu แบบ B
areas.action.type: "richmenuswitch"
areas.action.richMenuAliasId: "richmenu-a"
areas.action.data: "richmenu=a"
```

<script src="https://gist.github.com/jirawatee/da1e9a6e6430140f406118789c8c140e.js"></script>

一旦我們自定義了兩種 Rich Menu 類型的 JSON，那麼我們必須按照文章的 4.1（創建）和 4.2（上傳）步驟創建一個 Rich Menu 。您可以使用[Postman](https://www.postman.com/) 之類的工具來幫助。結果必須被richMenuId拒之門外。2.眼鏡蛇標識

![](https://nijialin.com/images/2021/switch-menu/6.png)

---

# 3. 定義 Rich Menu 別名
在這一步中，我們需要將 Alias 分配給 Rich Menu，在 A 和 B 之前都知道。

```
Headers:
  + Authorization: Bearer {channel access token}
  + Content-Type: application/json
Endpoint: https://api.line.me/v2/bot/richmenu/alias
Method: POST
Body:
  + richMenuId: ID ของ Rich Menu ที่ได้จากข้อ 2
  + richMenuAliasId: ชื่อของ Rich Menu โดยสามารถระบุเป็น a-z, A-Z, 0-9, _, และ - สูงสุด 100 ตัวอักษร
```
如果成功，您將獲得 200 狀態並{}返回。

---

# 4.為用戶分配 Rich Menu

最後一步是給我們帶來已經用OA或LINE Chatbot展示過的Rich Menu，定義為大家看到相同的item 4.3或將其定義為單個item，[文章](https://medium.com/linedevth/6cf12b394f38)的item 4.6或4.7 ，以及然後看看結果 一起努力 它有多快！

![](https://nijialin.com/images/2021/switch-menu/7.gif)

# 5. Alias相關的其他API
## 5.1 更新豐富菜單別名

定義 Rich Menu Alias 的便利之一是我們可以不用回到步驟 1-3 來更新目標 Rich Menu ID，但是這種方法不是實時的，會有一個緩存期。所以會有效的。
```
Headers:
  + Authorization: Bearer {channel access token}
  + Content-Type: application/json
Endpoint: https://api.line.me/v2/bot/richmenu/alias/{richMenuAliasId}
Method: POST
Param:
  + richMenuAliasId: ชื่อของ Rich Menu (สูงสุด 100 ตัวอักษร)
Body:
  + richMenuId: ID ของ Rich Menu ที่อยู่ใน channel เดียวกัน
```


如果成功，您將獲得 200 狀態並{}返回。

## 5.2 獲取豐富菜單別名列表

```
Headers:
  + Authorization: Bearer {channel access token}
Endpoint: https://api.line.me/v2/bot/richmenu/alias/list
Method: GET
```
如果成功，將返回狀態 200，並返回這樣結構的 JSON。

```json
{
  "aliases": [
    {
        "richMenuAliasId": "richmenu-alias-a",
        "richMenuId": "richmenu-862e6ad6..."
    },
    {
      "richMenuAliasId": "richmenu-alias-b",
      "richMenuId": "richmenu-88c05ef6..."
    }
  ]
}
```

## 5.3 Get Rich Menu Alias Info
```
Headers:
  + Authorization: Bearer {channel access token}
Endpoint: https://api.line.me/v2/bot/richmenu/alias/{richMenuAliasId}
Method: GET
Param:
  + richMenuAliasId: ชื่อของ Rich Menu (สูงสุด 100 ตัวอักษร)
```

如果成功，將返回狀態 200，並返回這樣結構的 JSON。

```json
{ 
  "richMenuAliasId": "richmenu-alias-a", 
  "richMenuId": "richmenu-88c05ef6..." 
}
```

## 5.4 刪除豐富菜單別名

由於1個Chatbot最多可以有1000個Rich Menu Alias，所以以防萬一它有限制並且想要創建更多。您需要先刪除不使用的任何別名。

```
Headers:
  + Authorization: Bearer {channel access token}
Endpoint: https://api.line.me/v2/bot/richmenu/alias/{richMenuAliasId}
Method: DELETE
Param:
  + richMenuAliasId: ชื่อของ Rich Menu (สูงสุด 100 ตัวอักษร)
```

如果成功，您將獲得 200 狀態並`{}`返回。

---
# 結論


LINE發布的Richmenu Switch Action從用戶的角度幫助了Rich Menu的實時切換，同時也減少了開發者的工作量。告訴我是誰在這裡讀的。不用不知道說啥哈哈哈哈
最後，如果這篇文章對您有用，請按Clap、按Share 並按Follow 發布：LINE Developers Thailand以免錯過我們的新文章。今天，我不得不說再見。下一篇文章再見。

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
