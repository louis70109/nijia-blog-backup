---
title: LIFF v2.3.1 更新內容 - Concat & Replace 模式
tags:
  - LINE
  - LIFF
categories: LINE
date: 2020-07-21 11:32:08
---


# 前言

大家好，我是 LINE Taiwan 的 Tech Evangelist – NiJia Lin。隨著 LIFF v2.3.0 上線後 LIFF 出現了 `Concatenate` 與 `Replace` 兩個模式的選項，初次使用的朋友可能會有點困惑，以下就使用一些 Scenario 為各位介紹一下這兩個功能之間的差異。

![](https://i.imgur.com/SkUlT3P.png)

> 在更新之前建立的 LIFF 模式皆為 `Replace`，往後新增的 LIFF page 模式皆會**預設**為 `Concatenate`，要麻煩各位多注意一下模式上的選擇。

- JS SDK release: [LIFF v2.3.1 released](https://developers.line.biz/en/news/2020/07/16/release-liff-2.3.1/)
- [LIFF v2.3.0 released](https://developers.line.biz/en/news/2020/06/29/release-liff-2.3/)

<!-- more -->

# 環境

習慣使用套件可朋友可以參考我們官方出的套件 - [@line/liff](https://www.npmjs.com/package/@line/liff)

## CDN 路徑注意

測試時若未使用 npm package 時需要注意 CDN 版本，一般來說使用 https://static.line-scdn.net/liff/edge/2/sdk.js 它會抓最新版本，
但若是**指定版本**的話  則需像範例網址 ➡️ https://static.line-scdn.net/liff/edge/**versions/2.1.13**/sdk.js 去指定。

兩個路徑**最大差異**就在於網址中會多一個 `versions` 的 path，使用上需多注意！

> 欲了解更多相關內容請參考 [LINE document](https://developers.line.biz/en/docs/liff/developing-liff-apps/#specify-cdn-path)

# 介紹

這是在 2.3.1 後出現的 mode，以下是一些範例供大家參考，主要以 slash(`/`)、Query String、LIFF 網址接`子路徑`(`sub path`) 三個測向讓大家快速了解兩個 mode 的差異。

> 以下測試結果皆用 v10.12 版本測試，若 APP 版本低於 v10.11 以下可能有不同輸出結果。

## Replace mode

在更新之前已存在的 LIFF page 目前皆已 migrate 至 Replace mode，它是一個向下相容的模式提供給先前已有相關 workaround 處理掉在 Replace mode 上的例外情況，則可在不影響功能的情況下繼續使用，並讓開發者可以安排時間逐步將相關的 LIFF page migrate 至 `Concatenate` 上，而以下則是原本 Replace mode 相關的一些參數測試。

| 編號 | 類型    | 原始網址                   | 使用者進入網址                               | 結果顯示網址                           |
| ---- | ------- | -------------------------- | -------------------------------------------- | -------------------------------------- |
| 1    | Replace | https://YOUR_DOMAIN        | https://liff.line.me/LIFF_ID/                | https://YOUR_DOMAIN/                   |
| 2    | Replace | https://YOUR_DOMAIN        | https://liff.line.me/LIFF_ID/brown/?q=2#hash | https://YOUR_DOMAIN/brown/?q=2         |
| 3    | Replace | https://YOUR_DOMAIN/friend | https://liff.line.me/LIFF_ID                 | https://YOUR_DOMAIN/friend?liff.state= |
| 4    | Replace | https://YOUR_DOMAIN/friend | https://liff.line.me/LIFF_ID/                | https://YOUR_DOMAIN/friend             |
| 5    | Replace | https://YOUR_DOMAIN/friend | https://liff.line.me/LIFF_ID/brown           | https://YOUR_DOMAIN/friend/brown       |
| 6    | Replace | https://YOUR_DOMAIN/friend | https://liff.line.me/LIFF_ID/brown/?q=2#hash | https://YOUR_DOMAIN/brown/?q=2         |

## Concatenate mode

在這個模式中處理掉先前 `Replace` 上有的一些問題，下面列幾點簡單敘述一下：

- 斜線（`/`): 在 Replace mode 的 `case 1` 中會出現斜線引起錯誤，目前已皆會指向至最初的 Domain。
- `liff.state=`: Replace 的 `case 3` 的案例中中回傳的網址中會出現 `liff.state=`，而在 Concatenate 中已經將這部分排除。
- 子路徑(sub path)消失問題: 看到 Replace mode 中的 `case 6` 中在使用者進入網址後，應當結果是 `/friend/brown`，而 `/friend` 這個路徑消失的問題。目前在 `v2.3.1` 的版本中已經修正了之前會吃掉原始 `/friend` 這個 sub path 的問題。

大家可以參考以下的 scenario 去測試一下實際情況：
| 編號 | 類型 | 原始網址 | 使用者進入網址 | 結果顯示網址 |
| ---- | ----------- | -------------------------- | -------------------------------------------- | ----------------------------------- |
| 1 | Concatenate | https://YOUR_DOMAIN | https://liff.line.me/LIFF_ID/ | https://YOUR_DOMAIN |
| 2 | Concatenate | https://YOUR_DOMAIN | https://liff.line.me/LIFF_ID/brown/?q=2#hash | https://YOUR_DOMAIN/brown/?q=2#hash |
| 3 | Concatenate | https://YOUR_DOMAIN/friend | https://liff.line.me/LIFF_ID | https://YOUR_DOMAIN/friend |
| 4 | Concatenate | https://YOUR_DOMAIN/friend | https://liff.line.me/LIFF_ID/ | https://YOUR_DOMAIN/friend |
| 5 | Concatenate | https://YOUR_DOMAIN/friend | https://liff.line.me/LIFF_ID/brown | https://YOUR_DOMAIN/brown |
| 6 | Concatenate | https://YOUR_DOMAIN/friend | https://liff.line.me/LIFF_ID/brown/?q=2#hash | https://YOUR_DOMAIN/friend/brown/?q=2#hash |

# 結論

藉由上述範例快速帶大家了解這次 v2.3.1 更新的 `Replace` & `Concatenate`，本次更新調整 LIFF SDK 上的一些使用方法與問題修正，目前開發團隊正逐步的修正每個議題，接下來隨著 LIFF 的新功能上線時我們會將第一手將資訊釋出讓大家知道 🙂。
