---
title: 如何規劃一個 chatbot 服務
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

![](https://nijialin.com/images/2021/)

# 前言

寫這篇時好友數 450+

跟在實事上的任何作品我相信都紅很快，如 口罩地圖、動森揪團系統...，只是這些題目紅的時候我個人沒有那麼大的憧憬去做相關題目。去年原本有`東南亞職業聯賽`(**ABL**)，我也做了一隻 Chatbot，只是當時用比較土炮的方法用 CSV 輸入議程，每次查詢時都進 CSV 查詢，但也適逢疫情關係而聯盟停辦進而機器人荒廢。但在最近出現了一個籃球新聯盟 `P+ league`，而我既然學 Python 也一段時間了也該拿來試試看爬蟲，因此下定決定開爬，以下會記錄一下在這過程中我有遇到的問題。

很習慣寫完一個 side project 就在技術社團發文

困境：

- TA 不同
- 技術相對不深

我的作法：

- 尋找 ptt 台灣相關籃球的版，最後找到`basketballTW`
- Facebook 一樣找一輪，找到 [P.LEAGUE + 台灣新職業籃球聯賽 (球迷討論區)](https://www.facebook.com/groups/292574422078791)
- LINE OpenChat 有貼，但目前只有一個隊伍有討論區，效果有限

- 結合 Chatbot 與 LIFF 的 ShareTargetPicker 的分享，把影片、戰績、比分分享給朋友
<!-- more -->

Flex Message 用法：

在回應單一訊息時則直接使用這樣的函式

```python
def response_flex():
  return {'type': 'flex'}
```

但諸如新聞或是球員數據，總是希望能使用像是 Carousel 來輸出，讓用戶可以左右滑動來查看數據，因此我就會這樣包裝：

```python
def response_carousel(flex):
  return {'type': 'carousel', 'contents': [flex]}
```

這樣的好處是讓上述 `response_flex()` 可以達到共用的目的，只要個別設計相關的 Flex(使用 [Simulator]())，當邏輯寫完之後產生 1~N 個 Flex Message 並放進一個陣列，丟給 carousel 函式即可達到共用！

User-Agent

在本地端可以，但一上 Heroku 之後想說 Chatbot 沒反應，是不是資料庫沒資料？使用 `heroku run bash` 進去跑一次腳本之後發現陣列值都時空的(本地可以上線不行)？因此就乾脆把網頁內容整個印出來(範例)：

```python
import requests
from bs4 import BeautifulSoup

res = requests.get('https://example.com')
soup = BeautifulSoup(res.content, 'html.parser')

print(soup.pretty())
```

發現一個很驚人的問題！當中的錯誤訊息認為我不是網頁因此擋下我的爬蟲(錯誤訊息待查)，實際原因是因為我沒有設定 `User-Agent` ([參考](https://stackoverflow.com/questions/27652543/how-to-use-python-requests-to-fake-a-browser-visit-a-k-a-and-generate-user-agent))，

> 這邊因為網站算小，因此不會有快取上的問題，而若讀者有遇到可以[參考設定](https://stackoverflow.com/questions/53899170/python-3-beautifulsoup-and-cache)

# 介紹

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
