---
title: "【LINE API 的小眉角】- Flex, LIFF, Richmenu"
tags:
---

# LIFF reply 收費問題

它是使用 Message api 的 Reply 功能來幫忙使用者發送條件引發 Bot 行為，並非是透過 Push api 發送讓 Bot 反應，這邊需要多注意喔！

> 但是現在 LIFF 還沒有 `postback` 的功能喔！😭

# Flex button 文字(text)欄位空值問題

flex 的 button text 的文字不能用 0 長度的字串，但可以用 `' '` 中間為空白鍵的字串去解決長度 0 的問題，否則會出現以上的錯誤:

```
Response Data -
  {
    "message": "A message (messages[0]) in the request body is invalid",
    "details": [
      {
        "message": "must be non-empty text",
        "property": "/contents/0/footer/contents/1/action/text"
      },
      ...
    ]
  }
```

# User id 的問題 - Provider

如下圖所示，左邊為我擁有的 provider，而右邊框框則為兩個不同 provider 下屬於我的 user id，只要在同一個 provider 下 user id 都會是固定的，無論用 Login 或 Message API。
![](https://i.imgur.com/gqRltSU.png)

---

![](https://i.imgur.com/8rXmRy7.png)

# Richmenu

## 座標計算

richmenu 的 x,y 是從左上(0, 0)算到右下(n, n)
限制:

- Image format: JPEG or PNG
- Image size (pixels): 2500x1686, 2500x843, 1200x810, 1200x405, 800x540, 800x270
- Max file size: 1 MB

> [參考](https://developers.line.biz/en/docs/messaging-api/using-rich-menus/#creating-a-rich-menu-using-the-messaging-api)

## 使用 link 的方式指定給特定使用者

➡️ python API - [連結特定使用者](https://github.com/line/line-bot-sdk-python/blob/master/linebot/api.py#L640)

若只需要連結特定使用者的話使用這個 api，我目前使用情境有兩個

- Bot 裡有多重身份需要依照角色不同而給不同的 richmenu
- 實作上下頁的功能，透過讓使用者按下特定位置時觸發更新成另一張圖片

```python
def link_rich_menu_to_user(self, user_id, rich_menu_id, timeout=None):
```

➡️ python API - [一次連結多個使用者](https://github.com/line/line-bot-sdk-python/blob/master/linebot/api.py#L661)

```
def link_rich_menu_to_users(self, user_ids, rich_menu_id, timeout=None):
```

範例影片
![](https://i.imgur.com/nFA7A7p.gif)

## 設定 richmenu 為預設

若是使用 setDefault 的話需要上一頁再回來才會更動，因為 setDefault 的行為則是對當前 Bot 的所有使用者設定，如果想要馬上變化的話則是使用上述 link 的方式哦！
