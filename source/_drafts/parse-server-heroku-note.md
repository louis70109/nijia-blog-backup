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

# Parse Server

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


# Parse Server Dashboard

範例專案：https://github.com/louis70109/parse-dashboard-example

## 如何部署

這邊透過 Heroku 來協助部屬測試環境，如果有需要部署到其他地方可以參考 Dockerfile。

```
git clone https://github.com/louis70109/parse-dashboard-example.git
cd parse-dashboard-example
heroku create
git push heroku master
```

部署好之後需要進去環境變數設定：

![](https://nijialin.com/images/2022/parse-server/heroku-env.png)


主要對接 Parse Server 的六個參數需放入環境變數，做些最基本的權限控管([參考 app.json](https://github.com/louis70109/parse-dashboard-example/blob/master/app.json)):

```
"env": {
    "APP_ID": {
      "value": "myAppId"
    },
    "MASTER_KEY": {
      "value": "myMasterKey"
    },
    "SERVER_URL": {
      "value": "http://yourappname.herokuapp.com/parse"
    },
    "APP_NAME": {
      "value": "myAppName"
    },
    "USERNAME": {
      "value": "example@gmail.com"
    },
    "PASSWORD": {
      "value": "parse"
    }
}
```
## 測試


Dashboard 方便點在於除了可以像 Firebase 一樣在網頁上放資料，另外還能有個介面直接測試 API，只要把該有的條件放好按下 `Send Query`，就能看測試資料如何囉！

![](https://nijialin.com/images/2022/parse-server/pd4-test.png)

如果你是 command line 愛好者，也可以參考 [parse-server 的範例](https://github.com/parse-community/parse-server#saving-an-object)去找：

```bash
$ curl -X GET \
  -H "X-Parse-Application-Id: APPLICATION_ID" \
  http://localhost:1337/parse/classes/Items
```

> objectId, createdAt, updatedAt, ACL 皆是 parse-server 預設管理欄位，看到他們別覺得驚訝，把你需要的欄位新增放在後面即可喔！

## 測試資料想刪除怎麼辦

要先刪掉所有資料(Row)，才可以刪 Class (保護機制避免亂刪)

## 小結


# 結論
