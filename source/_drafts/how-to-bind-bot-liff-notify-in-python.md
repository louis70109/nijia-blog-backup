---
title:
  "[object Object]": null
categories: 學習紀錄
tags:
---

![](https://i.imgur.com/0QAGPDc.png)

# 前言

最近因為要參加 「[中部人的 Chatbots Meetup 聊天機器人小小聚 #8 @ 台中夢森林](https://chatbots.kktix.cc/events/chatbots-meetup-in-central-taiwan-008)」，準備了一個專案來串接 LINE 服務

<!-- more -->

# 使用工具

- LINE
  - Messaging API: 使用者對話介面
  - Notify: 推播狀態用
  - LIFF: 在手機裡面開網頁綁定 Notify 用
  - [Simulator](https://developers.line.biz/flex-simulator/): 排訂閱訊息的樣式
- Flask/Python 3.8
- Ngrok

# 如何處理 LIFF 二次跳轉的問題

LIFF 在 v2.3 之後釋出的 Concatenate 模式會幫忙做一個二次跳轉，目的是為了把 `liff.state` 上 encode 過的 url decode 掉並跳轉到對應的 endpoint url 上，但使用者在設定 LIFF 時只會這樣設定：

![](https://i.imgur.com/C5pDkmW.png)

在 LIFF 中串上 Notify 很直觀地寫出以下程式時一定會噴錯誤訊息：

```python
class CallbackController(Resource):
    def get(self):
        user_id = request.args.get('state')
        token = lotify.get_access_token(code=request.args.get('code'))
        create_user_notify(user_id, token)
        return Response(render_template('confirm.html', liff_id=LIFF_CONFIRM_ID))
```

但你總不知道他中間到底跑了什麼東西，實際步驟如下：

使用者按了 👉 `https://liff.line.me/{LIFF_ID}` 後
⓵ 第一次跳轉 ⬇️
`https://6263de27b313.ngrok.io/notify/callback?liff.state=%3Fcode%3D21R1IZ86CN8ZXc4p3mqP3i%26state%3DUd6ab866a67af711d594b12b0baffb8ac`
⓶ LIFF 接到這串網址後，判斷是否為 `v2.3` & `Concatenate` 模式後把 liff.state 後面的值 decode 後組裝到 endpoint url 上並進行第二次跳轉 ⬇️
`https://6263de27b313.ngrok.io/notify/callback?code=21R1IZ86CN8ZXc4p3mqP3i&state=Ud6ab866a67af711d594b12b0baffb8ac`

正常來說結果應該要如上，但看著 spec 的結果去實作的你這麼想時就錯了，在第一次跳轉時網址全在 `liff.state` 上，還不是一個 fragment，因此上述的 code 會想拿 `state` & `code` 時就會出現 ValueError。

這時就就需要準備兩樣東西：

- 一個含有 liff.init({liff_id) 的跳轉頁面給 LIFF
- 後端也需要判斷掉當路徑上出現 liff.state 的狀態並導至跳轉頁面

#### 後端：

```python
class CallbackController(Resource):
    def get(self):
        if request.args.get('liff.state'):
            return Response(render_template('liff_redirect.html', liff_id=LIFF_CONFIRM_ID))
        ...
```

#### 前端 LIFF:

```html
...
<script src="https://static.line-scdn.net/liff/edge/versions/2.3.1/sdk.js"></script>

<script>
  liff
    .init({ liffId: "{{ liff_id }}" })
    .then(() => {})
    .catch((err) => {});
</script>
...
```

雖然多了一些步驟與方法，但能照著這個模式預設的行爲走皆大歡喜 🎉

# 結論

# 活動小結

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：@line_tw_dev
![](https://i.imgur.com/gxHgAzB.png)

# 關於「LINE 開發社群計畫」

LINE 今年年初在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來察看最新的狀況。詳情請看:

- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
