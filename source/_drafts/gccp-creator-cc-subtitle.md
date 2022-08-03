---
title: 【標題】題目
categories: 學習紀錄
tags:
---

![](https://nijialin.com/images/common.jpeg)

# 前言

隨著大影片時代開始，人們開始拍攝各種題材的題目，身為創作者的你最痛的點是什麼？影片？題材？對我來說就是字幕問題！人人看影片都需要字幕的部分，那該怎麼減輕上字幕的工作呢？這次就利用 GCP 上的服務(STT, GCS)，分享當中使用的一些眉眉角角，至少先讓你可以擁有一個入門級的字幕，降低大家初期在做影片所花的時間，把精力放多一點到創作上，最後在搭配 video.js 來展示。

- [分享的議程](https://coscup.org/2022/zh-TW/session/P7HXPX)
- [大會共筆](https://hackmd.io/@coscup/r1TovCJ65/%2F%40coscup%2Frk8ivC1a5)
<!-- more -->

> 此次在 COSCUP 2022 分享內容是日常的 Side Project

# 主題圍繞

- 凡事總有個原因
- Speech-To-Text
- Cloud Storage
- IAM & Role
- Cloud Run
- Youtube & Video.js
- Take Away

## 凡事總有個原因

1. 減少獨自製作影片的 effort
2. 增加被平台看見的機會
3. 想紅

### 這個專案怎麼能增進效率呢？

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/d069e1978c504743b6509a7fc336c0fb?slide=6" title="GCCP Creator @ COSCUP 2022" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

製作影片之前花費的功夫就有許多硬體、拍攝手法、剪輯相關，但這些就我目前經驗而言應該大家體會的過程都會是一樣。

而在這個過程中我們能做的事情就是透過雲端服務來處理`逐字稿`-`對時間線`-`輸出SRT`，到底能怎麼做呢？

### 使用 CC 字幕的原因

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/d069e1978c504743b6509a7fc336c0fb?slide=7" title="GCCP Creator @ COSCUP 2022" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

#### 優點篇

- 不必等字幕做完才出影片
- 上字幕難免出錯，修改快速
- 自適應(不受解析度影響)
- 提高影片曝光率(Youtube 識別)
- Youtube 編輯器夠用
- 額外優惠
  - 幫助聽障人士
  - 電腦版有自動翻譯
  - 有機會讓粉絲幫忙共編

#### 缺點篇

- 預設是關閉，需要訓練用戶
- 中文觀眾習慣看內字幕
- 字卡特效較少(不夠吸睛)
  - 會擋住原本的特效，有個遮罩 embed 在最前面

## 我在講它要聽！ ✍️ 開啟 SpeechToText

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/d069e1978c504743b6509a7fc336c0fb?slide=12" title="GCCP Creator @ COSCUP 2022" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

通常我們在使用服務時，都會很習慣進 UI 看一下這服務能做到些什麼事，而 STT 的 UI 上就是一些常見設定，來源、編碼、取樣率...，讓還在觀察測試的用戶可以先稍微玩看看了解 STT 能力到哪，在進行 API 使用的部分。

## 總會需要個玻璃櫃 🦖 建立 Cloud Storage

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/d069e1978c504743b6509a7fc336c0fb?slide=16" title="GCCP Creator @ COSCUP 2022" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

Cloud Storage(GCS) 顧名思義就是要建立一個雲端儲存庫，相當於 AWS S3，除了可以放上東西儲存以外，也可以透過它去介接其他的服務，此篇後面將會透過 Eventarc 去介接 Cloud Storage 與 Cloud Run。

> GCS 與 AWS S3 經常也會被拿來放置前端編譯完放置檔案的地方，再透過其他 DNS route 之類的功能，借接起來把前端資訊打在用戶的瀏覽器上。
> 其他參考 [Day28 - 用 AWS S3 幫忙轉址到原有的服務上](https://nijialin.com/2019/10/12/Day28-%E7%94%A8-S3-%E5%B9%AB%E5%BF%99%E8%BD%89%E5%9D%80%E5%88%B0%E5%8E%9F%E6%9C%89%E7%9A%84%E6%9C%8D%E5%8B%99%E4%B8%8A/)

## 而且要有鎖頭 🔐 來點 IAM & Role

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/d069e1978c504743b6509a7fc336c0fb?slide=19" title="GCCP Creator @ COSCUP 2022" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

首先要先到 GCP 左上的找到 `IAM & Role`，找到 Service Account(服務帳戶) 建立授權過的帳號。

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/d069e1978c504743b6509a7fc336c0fb?slide=20" title="GCCP Creator @ COSCUP 2022" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

順利建立完後會出現有兩種方式的金鑰讓你選擇使用，這邊一般會使用 `JSON 的檔案`來與雲端服務串接 API 使用。

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/d069e1978c504743b6509a7fc336c0fb?slide=21" title="GCCP Creator @ COSCUP 2022" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

這邊與大家分享一個切身之痛的事情，之前有次因為與 .gitignore 發生了點誤會，不小心把 JSON Key 往 GitHub 踢，結果導致 Key 被抓到拿去做壞壞的事，因此被寄了通知信鎖住帳號 QAQ，所以以下提供一些之前文章有做過的做法給大家，盡可能必免把 Key 踢出去的方法。

- 建立一個暫時檔
- 路徑放環境變數中
- 寫入 `GOOGLE_APPLICATION_CREDENTIALS`
- ⚠️ 需要框架啟動前
- ⚠️ 需整理成 JSON 樣式
- 單引號 -> 雙引號

> 更詳細內容請參考我之前寫的文章：[把 JSON 字串寫入記憶體中的暫時檔案並放路徑至環境變數中 | Python, FastAPI](https://nijialin.com/2022/04/02/python-env-import-json-string/)

## 萬事皆上雲 ⛅️ 如何部署到 GCP

### 做什麼才會觸發 - 在 CloudRun 設定 Eventarc

## 不想住這邊，我要搬走！使用 video.js 的 hints

### CORS 那我要去愛別人 – API 我還你原形

### 既然你不聽那我來硬的 – CLI 降肉！

### 過去即是永恆 – 快取放我走！

### 不都在講同一件事？Video.js 需要 VTT

## 管理大師 ⏰ 的我們能帶走點什麼？

✍️ 揮揮衣袖，不帶走一片雲彩

- STT 時間支援最低到 nano，但在 Youtube - 字幕上也算很精準
- STT 測試起來以一分鐘為分水嶺，太短的影片可能不適用
- 減少初期敲字幕稿的時間(30~40%)，只需後續細修、對時間
- 編輯器用別人的就好，別想自己寫 ( ~~還我三個禮拜！~~ )

# 結論

# 活動小結

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：@line_tw_dev
![](https://www.evanlin.com/images/2020/line-tw-dev-qr.png)

# 關於「LINE 開發社群計畫」

LINE 於 2019 年開始在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來查看最新的狀況。詳情請看:

- [2021 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2021-line-tw-devrel/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)

<style>
  section.compact {
    font-size: 150%  
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
</style>
