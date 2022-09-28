---
title: 【標題】題目
categories: 學習紀錄
tags:
---


![](https://nijialin.com/images/2022/)
![](https://nijialin.com/images/common.jpeg)


# 前言

從以前使用雲端硬碟，如Dropbox, Google Drive, Box...我們都很習慣可以手動拉照片、影片上去放，而在開始寫程式之後理所當然就會想用 API 丟，但這些雲端硬碟一般來說除非用模擬器，不然理論上應該是不好用程式跑，而在公有雲出來後，就有像是 AWS S3, Google Cloud Storage 等等的服務陸續出來，讓大家可以使用他們的服務建立自己的硬碟空間，也不用自己架伺服器弄硬碟空間，權限管控都幫你弄好好，也可以用 API 訪問，實在是很方便呢！

隨著程式越寫越多，除了在 LINE Bot 上需要圖片網址才可以發送圖片外，像是 video.js 以及許多很多服務、工具越來越依靠　https 相關的網址來找圖片，接下來就讓筆者就帶大家認識一下近期使用的一些範例以及我發現的另一種上傳方法。

<!-- more -->

# 介紹


## Google Cloud Storage(GCS)

- $$

雖然需要付錢，但相關的 API 文件都非常的豐富，網路上也有許多語言範例可以參考，在連結其他 Google 服務上網內互打也會快滿多的，且另外也還可以放前端編譯完的靜態檔案(dist)，

## GitHub repo

- 空間限制5G([Document]())

不過目前我的部落格已經超肥([專案]())，看起來也還可以使用，因此若初期想使用或許可以使用看看

## 應用 - LINE Bot 收到圖片後傳到 GitHub 並使用

以下是使用 Python 為範例，在一次的 Webhook 收到圖片之後，會收到 Message Id，可以透過這個 ID 去取得圖片、影片相關資料(但不能收檔案)

<script src="https://gist.github.com/louis70109/d9badb4defce9c33a5e89b1d2c0c82ed.js"></script>

# 結論

<style>
  section.compact {
    font-size: 150%  
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
</style>