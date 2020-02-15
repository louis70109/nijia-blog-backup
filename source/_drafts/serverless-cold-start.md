---
title: serverless cold start
tags:
---

![workload](https://i.imgur.com/gjLODpG.jpg)

# 前言

之前鐵人賽寫了一篇文章有提到 [Cold Start 的問題](https://nijialin.com/2019/10/14/Day30-%E8%80%81%E6%98%AF%E5%9C%A8%E5%90%B9-Serverless%EF%BC%8C%E4%BB%96%E7%9C%9F%E7%9A%84%E6%9C%89%E9%82%A3%E9%BA%BC%E5%A5%BD%EF%BC%9F/)，不過只有粗略介紹，這次就來好好的搜尋資料介紹一下。

平常在做 open source 時比較常遇到休眠狀態應該就是 `Heroku`，而開頭要先澄清一下他是屬於 `PaaS` 的架構，而 AWS、Google、Azure 裡提供的 `Lambda`、`Cloud Run`、`Azure Function` 這些則屬於 FaaS 架構，而最常討論 `Cold start` 問題則是在 FaaS 上。

> 有很多各式各樣的服務，SaaS、FaaS、KaaS、IaaS... 等各式各樣的架構，每個都是為了解決某個問題所誕生的，至於好或不好其實就是看使用場景而定，所以大家在選用時要注意一下你使用的場景哦！

## 為什麼會休眠
一般會有休眠機制是因為這些服務建置時都是 `事件驅動`(`Event-Driven`)的方式去部署，意指是當前服務若收到訊息後，會呼叫對應的 Function 來處理對應服務所接收到的資料，

而在處理資料之後過一段時間若沒有繼續執行，雲端提供商會將容器先刪除，然後 function 會處於 inactive 狀態(cold)，而當 function 再度被觸發時(`cold start`)則會再啟動容器來執行對應 function 來處理事件。

Function Chain

## Cold start 流程

流程
![[參考](https://mikhail.io/2018/08/serverless-cold-start-war/#how-do-languages-compare-)](https://i.imgur.com/DQoGYns.png)

> 部署 -> 事件處理 -> 休眠 -> 刪除容器 -> 觸發 -> 啟動容器 -> 事件處理...

上述流程就是本篇介紹的 `cold start`

- event-driven functions
  Most FaaS providers have 1–3 second cold starts

use case
![serverless-use-case](https://i.imgur.com/EM7TdWW.jpg)

## Cold start 比較表

| 服務                                                                          | 時間                                    |
| ----------------------------------------------------------------------------- | --------------------------------------- |
| AWS Lambda                                                                    | 10 minutes                              |
| Google Cloud Functions                                                        | Anywhere between 3 minutes and 5+ hours |
| Azure Functions                                                               | 20 minutes                              |
| [Heroku](https://devcenter.heroku.com/articles/free-dyno-hours#dyno-sleeping) | 30 minutes                              |
> 前三個為 `FaaS` 架構，而 Heroku 則為 `PaaS` 架構喔！

![FaaS platform cold start time](https://i.imgur.com/yZxWvlL.png)

## 適合使用情境 - Chatbot 為例

在實作聊天機器人時我們可能會針對不同的目的來定義當前的機器人的屬性，以下簡單提幾項常見的機器人：

- 客服
- 服務狀態回報
  - CI/CD 建置狀態
  - 伺服器 Error
  - 排程
- 查詢
- 桌遊

基於方便我們會使用 Serverless 來幫忙部署，考慮到在有 cold start 狀態時其實

## warm-up

這邊使用 AWS 來做範例
https://serverless.com/blog/keep-your-lambdas-warm/#installing-the-warmup-plugin

# 參考

[On the Serverless cold start problem](https://medium.com/faun/on-the-serverless-cold-start-problem-2fc0797da5cc)
[2018 Serverless Community Survey: huge growth in serverless usage](https://serverless.com/blog/2018-serverless-community-survey-huge-growth-usage/)
[Warm-up](https://serverless.com/blog/keep-your-lambdas-warm/#installing-the-warmup-plugin)
[Heroku cold start](https://devcenter.heroku.com/articles/free-dyno-hours)
[serverless 啟動流程](https://mikhail.io/2018/08/serverless-cold-start-war/#how-do-languages-compare-)
