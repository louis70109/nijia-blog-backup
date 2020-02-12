---
title: serverless cold start
tags:
---

![workload](https://i.imgur.com/gjLODpG.jpg)

# 前言

之前鐵人賽寫了一篇文章有提到 [Cold Start 的問題](https://nijialin.com/2019/10/14/Day30-%E8%80%81%E6%98%AF%E5%9C%A8%E5%90%B9-Serverless%EF%BC%8C%E4%BB%96%E7%9C%9F%E7%9A%84%E6%9C%89%E9%82%A3%E9%BA%BC%E5%A5%BD%EF%BC%9F/)，不過只有粗略介紹，這次就來好好的搜尋資料介紹一下～

> 有很多各式各樣的服務，SaaS、FaaS、KaaS、IaaS... 等各式各樣的架構，每個都是為了解決某個問題所誕生的，至於好或不好其實就是看使用場景而定，所以大家在選用時要注意一下你使用的場景哦！ㄌ

## 為什麼會休眠

這裡就要提到

- event-driven functions
  Most FaaS providers have 1–3 second cold starts

use case
![serverless-use-case](https://i.imgur.com/EM7TdWW.jpg)

## Cold start 比較表

| 服務                                                                          | 時間                                    |
| ----------------------------------------------------------------------------- | --------------------------------------- |
| AWS Lambda                                                                    | 10 minutes                              |
| Google Cloud Functions                                                        | Anywhere between 3 minutes and 5+ hours |
| [Heroku](https://devcenter.heroku.com/articles/free-dyno-hours#dyno-sleeping) | 30 minutes                              |
| Azure Functions                                                               | 20 minutes                              |

![platform cold start time](https://i.imgur.com/yZxWvlL.png)

## warm-up

這邊使用 AWS 來做範例
https://serverless.com/blog/keep-your-lambdas-warm/#installing-the-warmup-plugin

# 參考

[On the Serverless cold start problem](https://medium.com/faun/on-the-serverless-cold-start-problem-2fc0797da5cc)
[2018 Serverless Community Survey: huge growth in serverless usage](https://serverless.com/blog/2018-serverless-community-survey-huge-growth-usage/)
[Warm-up](https://serverless.com/blog/keep-your-lambdas-warm/#installing-the-warmup-plugin)
[Heroku cold start](https://devcenter.heroku.com/articles/free-dyno-hours)
