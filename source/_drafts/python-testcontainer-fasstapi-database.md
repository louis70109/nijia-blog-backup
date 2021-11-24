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

這一陣子許多同事除了在內部分享會中分享 Testcontainer 的技術，也有到 JCConf 2021 上分享 - [Integration testing with Testcontainers](https://jcconf.tw/2021/)，過往我在寫單元測試(Unit)時，時常都把資料庫的函式都直接擋住(Mock)，假裝他是成功的情況下往下走，但在一個 API 中資料庫往往是最容易在緊繃時掛掉，亦或是工程是手癢去改了某個欄位，讓整個服務瞬間炸掉，這些問題都是我們無法控制的部分...因此實際讓資料庫跑在測試時可以有個真的環境可以使用是很重要的一環，雖然看專案規模，測試時間有多有少有長有短，但放著一個 Container/VM 在那邊沒用就是很浪費啊，因此就有本次要介紹的 Test Container。

> 把 Test Container 分開寫比較懂他是幹嘛的，但在找資料時請以 testcontainer 去找才找得到喔！

Test Container 是一個 Java 的函式庫，支援 JUnit 來做測試，在跑測試時可以幫忙起個容器(Container)，並可以放上各式資料庫、Selenium 瀏覽器...等等可以放在 Docker 上面跑的內容，那 Test Container 很好的地方就是他也提供 Python 的解決方案([testcontainers/testcontainers-python](https://github.com/testcontainers/testcontainers-python))，讓我這個 Python 開發者可以有機會在 Docker 裡面很快地起一個 Container 來跑資料庫相關的整合測試，接下來就讓我娓娓道來我踩坑的過程 🖌️

- [Test Container 官網](https://www.testcontainers.org/)

> 有支援各種程式語言的函示庫喔，大家可以去挖挖看

<!-- more -->

# Test Container - Python

由於我開發時習慣使用 PostgreSQL 來當資料庫(其他的也沒問題)，首先先到官方文件上看一下[相關的內容](https://testcontainers-python.readthedocs.io/en/latest/database.html)，首先先安裝 Test Container 之後，接著提供了以下的做法開場

```
pip install testcontainers # 安裝套件 || 放入 requirements.txt
```

```python
with PostgresContainer("postgres:9.5") as postgres:
    e = sqlalchemy.create_engine(postgres.get_connection_url())
    result = e.execute("select version()")
```

## 整合進 Global 宣告的 FastAPI 中

# GitHub Actions

因為本次是使用 GitHub Actions 作為 CI 工具，因此使用前要[先進文件](https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners#preinstalled-software)看一下使用的 Ubuntu 20 版是否有支援在裡面使用 Docker 的功能


其中遇到了以下的問題，環境上整個專案是 Frontend 為主，其中一個資料夾是後端程式
```
ERROR tests/test_main.py - AttributeError: 'NoneType' object has no attribute...
```

# 結論
