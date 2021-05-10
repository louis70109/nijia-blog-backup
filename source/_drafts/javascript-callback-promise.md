---
title: 【標題】題目
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

近期在想活動時想到之前有做個[彈幕機器人](https://github.com/louis70109/Screen-LINE-Bullets)，異想天開下想說在上面加個投票系統，不過為求方便想快速完成，因此想說用 Docker 啟動一個 Redis 來做個 PoC，因為當初為求前後端方便彈幕機器人就使用全 js 的方式撰寫，在很直觀找到最多星星的 Redis 套件 - [node-redis](https://github.com/NodeRedis/node-redis)，以下就分享我被 callback 雷到的經驗ＸＤ

<!-- more -->

# TL;DR

https://github.com/louis70109/vote-bullets-line-bot/blob/master/utils/redis.js

官方說本身要支援的話要等到 v4 版本，或是用 `util.promisify` 的方法去讓他變成 Promise，

# 結論
