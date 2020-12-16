---
title: Kubernetes 和 Docker 之線上討論分享會
categories: 研討會
tags: ['Kubernetes', 'Docker', 'CNTUG']
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

![](https://nijialin.com/images/2020/1.png)

# 前言

<!-- more -->

# 介紹

當天的影片
一言難盡的關係：Kubernetes 和 Docker 之線上討論分享會

<iframe width="560" height="315" src="https://www.youtube.com/embed/nc3mBN3LzvM" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- 主要 follow 這次 v1.20.0 的改動
  - [CHANGELOG](https://github.com/kubernetes/kubernetes/blob/master/CHANGELOG/CHANGELOG-1.20.md#deprecation)
- 講解 Kubernetes [官方的敘述](https://kubernetes.io/blog/2020/12/02/dont-panic-kubernetes-and-docker/)

在這此的改動中移除了 `dockershim`，此舉動讓許多開發者非常的擔心自己的基礎設施(Infra)是否會被影響甚至不能用，這次的線上研討會則來敘述這次的更動。

- Docker 不是唯一解，只要可以支援 OCI 都可以解決
- Support `Open Container Initiatives(OCI)`，更多 OCI 說明可[參考這篇](https://ithelp.ithome.com.tw/articles/10216880)

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
