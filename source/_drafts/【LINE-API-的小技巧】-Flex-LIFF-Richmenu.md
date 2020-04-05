---
title: "【LINE API 的小技巧】- Flex, LIFF, Richmenu"
tags:
---

- liff reply 不會收費
- flex 的 button text 的文字不能用 0 長度的字串，但可以用 ‘ ‘ 去替代空白
  richmenu 的 x,y 是從左上算到右下
- 同一個 provider user id 會是一樣
- richmenu 若是使用 setDefault 的話需要上一頁再回來才會更動，如果適用 link 的方式則會馬上改變

# Richmenu

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
