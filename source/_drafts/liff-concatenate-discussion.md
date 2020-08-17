---
title:
  "[object Object]": null
categories: 學習紀錄
tags:
---

![](https://i.imgur.com/K53Ndlh.png)

# 前言

在 6/29 時 LIFF 釋出了 v2.3.0 版，這次的更新中修正了舊有模式(Replace mode)上的問題(詳細可[參考這篇](https://engineering.linecorp.com/zh-hant/blog/new-liff-url-infomation/))，本篇範例則是測試在 concatenate 模式下 liff.state 跳轉時路徑是否正確。

<!-- more -->

# 介紹

這部分我會使用 Python 搭配 Flask 做範例說明，而下方我有提供 Node.js 版本，歡迎大家取用。

範例

- [Express/Node.js](https://github.com/louis70109/liff-concatenate-js)
- [Flask/Python](https://github.com/louis70109/liff-concatenate-python)

首先當使用者按下你在 LINE Developer Console 設定的 LIFF app url:

![](https://i.imgur.com/CBtmDbV.png)

而 LIFF 會將使用者導向到設定時的 domain 上，但 LIFF 是透過 liff.state 裡帶參數來進行跳轉

```
@app.route('/notify')
def hello_world():
    # workaround
    if request.args.get('liff.state'):
            return Response(render_template('redirect.html', liff_id=CONCAT_ID))

    fragments = request.args
    return Response(render_template('index.html', fragments=fragments, liff_id=CONCAT_ID))
```

- 跳轉
- Heroku deploy

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
