---
title: 【Parse Server】經驗談
categories: 學習紀錄
tags:
---

![](https://nijialin.com/images/2022/)
![](https://nijialin.com/images/common.jpeg)

# 前言

Parse Server 專案：[連結](https://github.com/parse-community/parse-server)
範例專案：[連結](https://github.com/parse-community/parse-server-example)

<!-- more -->

# 介紹

健康檢查 API：https://DOMAIN.herokuapp.com/parse/health

```
{
"status": "ok"
}
```

## [PostgreSQL](http://docs.parseplatform.org/parse-server/guide/#postgres)

官方文件會主推 MongoDB 來做，但因為 Heroku 現在已經不支援 mLab 的 MongoDB，因此在這環境下就得使用 PostgreSQL，但這邊有些需要注意的東西

- Heroku PostgreSQL -> Hobby Dev
  - 會幫忙建立一個 `DATABASE_URL`，要另外建立環境變數 `DATABASE_URI` 給 parse server 使用

但原本的網址只換乘 DATABASE_URI 會無法使用，需要參考 parse server 官方文件下的 PostgreSQL 說明

> 1. SSL with verification - postgres://localhost:5432/db?ca=/path/to/file
> 2. SSL with no verification - postgres://localhost:5432/db?ssl=true&rejectUnauthorized=false

如果你的 DB 是需要簽證(CA)以確保安全，就使用第一行；而這次因為求快速部署，因此選擇第二行先不執行認證(但有 SSL)。

## Parse Server 環境變數

![](https://nijialin.com/images/2022/parse-server/1.png)

在讀 parse-server 文件以及 Getting Start 可能會很疑惑現在到底要用什麼樣的環境變數，需要 prefix？那要加什麼？其實會看不太懂，以下透過 parse-server-example 做範例
以 parse-server-example 裡面的範例來說

# 結論
