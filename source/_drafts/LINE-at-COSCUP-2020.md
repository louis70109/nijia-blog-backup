---
title:
  "[object Object]": null
categories: 學習紀錄
tags:
---

![](https://i.imgur.com/0QAGPDc.png)

# 前言

<!-- more -->

本次 LINE 出動了三個講者

# [How We Integrate and Develop Private Cloud in LINE](https://coscup.org/2020/zh-TW/agenda/PZPMCR) - Gene Kuo

![](https://i.imgur.com/XpyZt4Z.jpg)

<script async class="speakerdeck-embed" data-id="efd3904c14f7400cbbd4e62553e3976b" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

由我們 Verda Platform Development Team 的 LINEr - Gene Kuo 在 Cloud Native Hub 分享一個遠端的議程。

首先提到了為什麼 LINE 需要選擇自己的 private cloud(LINE 裡稱為 Verda)，並且對比 public cloud 相對應的問題：

| Question | Private        | Public      |
| -------- | -------------- | ----------- |
| 花費     | 可掌控         | 不易掌控    |
| 靈活度   | 高             | 低          |
| 開發     | As a developer | As a proxy  |
| 需求處理 | 討論價值在哪   | 只能 Yes/No |

## Verda 的 High Level Architecture:

這部分講者快速講解了 IaaS、PaaS、FaaS 個別在層級上使用的用途。

<script async class="speakerdeck-embed" data-slide="11" data-id="efd3904c14f7400cbbd4e62553e3976b" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

## LINE 擁有 2000+ Hypervisor, 50000+ VMs, 20000~ 實體主機

早期的服務已經擁有許多的主機群，因此運用既有的資源建立 private cloud，搭配軟硬體可以取得更多的好處。

<script async class="speakerdeck-embed" data-slide="12" data-id="efd3904c14f7400cbbd4e62553e3976b" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

## 困難點

<script async class="speakerdeck-embed" data-slide="14" data-id="efd3904c14f7400cbbd4e62553e3976b" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

接下來提到了整合 openstack 到 Verda 時帶來的挑戰與困難點，這裡提到的是與普羅大眾的 open source 一樣會遇到的問題，以下大概列出這次提到的困難點部分：

- Feature
- 政策問題
- 內部元件整合
- 版本升級
- 開發與除錯複雜度
- 在大架構下的效能問題

在使用中上沒辦法 100% 相容，因此需要自己開發 patch 來支援，例如： Quota 控制(eg. GPU / MEM / CPU allocation)，但開發有一定數量的 patch 後很有可能會在下次改版是 conflict，所以因此要降低客製化的需求避免衝突問題，同時也需要管理 patches 並分類它們。

使用大量的 solution 讓大家知道解法帶來的效益：

<script async class="speakerdeck-embed" data-slide="20" data-id="efd3904c14f7400cbbd4e62553e3976b" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

最後帶大家了解團隊內開發 Openstack 時的 workflow：

<script async class="speakerdeck-embed" data-slide="29" data-id="efd3904c14f7400cbbd4e62553e3976b" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

在這個議程中充分的說明 private & public cloud 優劣，並用大量的範例來說明 Verda 在 private cloud 裡所會遇到的困難與挑戰，最後就快速 Demo 帶大家了解 custom-source 的存放以及 git review 上的功能展示。

若有興趣的朋友歡迎參閱我們的文章： https://engineering.linecorp.com/en/blog/verda-platform-team/

# [The productivity brought by Clojure](https://coscup.org/2020/zh-TW/agenda/CFSTWL) - Laurence Chen

<iframe src="//www.slideshare.net/slideshow/embed_code/key/hFD5ddH6NrHXUX" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/humorless/the-productivity-brought-by-clojure-149170292" title="The productivity brought by Clojure" target="_blank">The productivity brought by Clojure</a> </strong> from <strong><a href="https://www.slideshare.net/humorless" target="_blank">Laurence Chen</a></strong> </div>

Clojure 有以下特性：

1. REPL-driven development
2. Immutable data structure
3. Composable functions
4. Immutable database

講者接著以 JS 為例說明在大部分 [M-expression](https://en.wikipedia.org/wiki/M-expression) 語言特性中與 [S-expression](https://en.wikipedia.org/wiki/S-expression) 的差異，並用 tree 的方式為大家快速介紹。

- 由於 Clojure 是 immutable data structure，因此大部分狀況下都是 copy on write。
- 若有更動到 tree 上的 node，則改動的部分會生成新的 node，其他沒有更動到的則直接 reference。
- 相對減省許多 memory。

有些 function 定義在 array or map

sequences operation -> 操作各種 map filter, reduct, first,rest...
而他是一個 linked list

其他語言有不一致的相關 function name，人腦需要記憶時會覺得很痛苦無法記錄下來

## Record function time

以往為了量測 function 執行時間時則需放入兩個 Timer 才可以計算出執行時間，而 Clojure 只需要在 vim 上輸入 `(time doSomething)` 即可馬上算出 function 執行時間(真的很方便)。

![](https://i.imgur.com/MZZGvxl.jpg)

- productivity 增加 30%

## Demo

使用範例帶大家快速的認識 Clojure 的好處：
![](https://i.imgur.com/MoXAea0.jpg)

![](https://i.imgur.com/UDACfbi.jpg)

## 小結

這個語言&語系我還是真的第一次聽到，從講者的分享中可以感覺到若已經習慣兩種生態的開發者其實若使用 Clojure 開發產品的話產出說不定真的比其他語言的開發速度快上許多，且在這場演講中講者用很實際的例子帶大家了解兩邊的差異，之後有機會不妨聽看看講者分享吧！

> 開發上若是括號上的問題並是使用 vim 開發的話可以[參考這篇](http://irongateinfo.blogspot.com/2017/02/clojure-vim-rainbow-parentheses-cljfmt.html)

# [Lotify: a python SDK for LINE Notify](https://coscup.org/2020/zh-TW/agenda/KNJDWQ) - NiJia Lin (就是我)

![](https://i.imgur.com/tuGOdi1.jpg)

<script async class="speakerdeck-embed" data-id="733b207481c441adab9cac7d241efc29" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

# 介紹

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
