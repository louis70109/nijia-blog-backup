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

健康檢查：https://DOMAIN.herokuapp.com/parse/health

```
{
"status": "ok"
}
```

## [PostgreSQL](http://docs.parseplatform.org/parse-server/guide/#postgres)

官方文件會主推 MongoDB 來做，但因為 Heroku 現在已經不支援 mLab 的 MongoDB，因此在這環境下就得使用 PostgreSQL，但這邊有些需要注意的東西

- SSL with verification - postgres://localhost:5432/db?ca=/path/to/file
- SSL with no verification - postgres://localhost:5432/db?ssl=true&rejectUnauthorized=false

- Heroku PostgreSQL -> Hobby Dev
  - 會幫忙建立一個 `DATABASE_URL`，要另外建立環境變數 `DATABASE_URI` 給 parse server 使用

# 結論

