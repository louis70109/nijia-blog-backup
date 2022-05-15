---
title: 【標題】題目
categories: 學習紀錄
tags:
---

![](https://nijialin.com/images/2022/line-api-update-1)
![](https://nijialin.com/images/common.jpeg)

# 前言

<!-- more -->

# 介紹



## Rich menu 更新


> [官方 API 更新新聞](https://developers.line.biz/en/news/2022/05/13/richmenu-keyboard/)

Rich Menu 在與官方帳號互動時很方便，不過過去在使用上會遇到一些小問題，在如今已經有方法解決囉！讓我們繼續往下看。


### 過去遇到 或 無法處理的問題

- 從 Rich Menu 按下按鈕後送出 Flex Message 後，如果訊息量太長，上面的內容會看不到
- 只能手動縮小 Rich Menu
- 切換鍵盤步驟過多
  - 高互動的官方帳號不好處理(例如: 遊戲型OA)
### 現在能怎麼做?

在這次更新中支援了以下四種功能:

- closeRichMenu: 關閉 rich menu
- openRichMenu: 打開 rich menu
- openKeyboard: 打開鍵盤
- openVoice: 打開 voice message 的輸入模式


此外還可以透過 [postback action](https://developers.line.biz/en/reference/messaging-api/#postback-action) 在打開鍵盤同時，輸入文字，並且可以帶有 `\n`，最多 300 字

範例:
```json
{
  "type": "postback",
  "label": "Buy",
  "data": "action=buy&itemid=123",
  "displayText": "Buy",
  "inputOption": "openKeyboard",
  "fillInText": "---\nName: \nPhone: \nBirthday: \n---"
}
```

> API Expert - 均民 詳細寫了一篇文章，歡迎大家參考: [新功能：在官方帳號開關選單、切換文字或語音輸入](https://taichunmin.idv.tw/blog/2022-05-14-line-postback-input-option.html)


##  LIFF 更新

最近 LIFF 團隊釋出了讓大家可以快速建立 web app 的工具，支援了各大主流框架，且使用方式相當容易。

> 參考[最近的新聞](https://developers.line.biz/en/docs/liff/cli-tool-create-liff-app/#advance-preparation)

### 透過 npx 初始化一個 LIFF app
```
$ npx @line/create-liff-app
```

### 選擇想用的框架與相關參數

![](https://nijialin.com/images/2022/line-api-update-1/2.png)

- 名稱
- 框架
- 型別
  - JavaScript/TypeScript
- LIFF ID
  - 會在 `.env` 中，還沒填後續可以改
- 套件管理？ yarn || npm


# 結論

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

<style>
  section.compact {
    font-size: 150%  
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
</style>
