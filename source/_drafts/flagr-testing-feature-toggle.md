---
title: 【標題】題目
categories: 學習紀錄
tags:
---


![](https://nijialin.com/images/2022/)

# 前言

<!-- more -->

# 介紹

> 官網: https://openflagr.github.io/flagr/#/README

執行

```
# Start the docker container
docker pull ghcr.io/openflagr/flagr
docker run -it -p 18000:18000 ghcr.io/openflagr/flagr

# Open the Flagr UI
open http://localhost:18000
```

預設是 sqlite3，

## Heroku 上操作(僅供試玩)

用 Container 的方式部署到 Heroku 上，可以參考官方的[這篇操作說明](https://devcenter.heroku.com/articles/container-registry-and-runtime)。

1. 先登入 Heroku 帳號
```
heroku login
```
2. 登入 Container 服務
```
heroku container:login
```

3. 把 Flagr 的專案 clone 下來：https://github.com/openflagr/flagr

```
git clone https://github.com/openflagr/flagr.git
```

4. 接著建立 Heroku 的專案。(如果加上 -a 放上自定義名字的話，後面的指令都需要加上 -a 喔！)
```
heroku create
Creating salty-fortress-4191... done, stack is heroku-20
https://salty-fortress-4191.herokuapp.com/ | https://git.heroku.com/salty-fortress-4191.git
```

5. 把剛剛 Clone 的專案推到 Heroku 的 Container Registry:
```
heroku container:push web
```

6. 最後把你剛剛的 Container image 推出:
```
heroku container:release web
```

在終端機上開啟瀏覽器:
```
heroku open
```

# 把東西方在 Postgres 中
建立 Postgres 的 add-on
![](https://nijialin.com/images/2022/flagr/1.png)

會在環境變數上幫忙放上一個預設的參數
![](https://nijialin.com/images/2022/flagr/2.png)

Flagr 預設吃的兩個參數：
```
FLAGR_DB_DBCONNECTIONSTR
FLAGR_DB_DBDRIVER
```

> [官方的範例](https://github.com/checkr/flagr/blob/master/integration_tests/docker-compose.yml)上用 docker-compose 會把 ssl-mode=false，因為這都是在本地端測試，在 Heroku 這邊要把 ssl-mode 移除。
# 結論