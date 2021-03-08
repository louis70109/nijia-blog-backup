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

Example: https://github.com/louis70109/prometheus-grafana-py-demo

<!-- more -->

# 介紹

首先在這個範例中的檔案結構有三個主要功能：

- `Flask app`: 展示範例的一個簡易 web app

  - app.py: 主要做事的檔案
  - Dockerfile: 負責將應用程式編譯完後做成 Docker Container
  - requirements.txt: Python 套件檔

- `prometheus.yaml`: 設定 Prometheus 需要做的事情
- `docker-compose.yaml`: 負責將 `Flask app`、`Prometheus`、`Grafana` 透過 Docker 一次部署起來並相互扶持(?)

- [Environment variables rule](https://grafana.com/docs/grafana/latest/administration/configuration/#configure-with-environment-variables)
  - Rule: `GF_<SectionName>_<KeyName>`
- [Grafana database properties](https://grafana.com/docs/grafana/latest/administration/configuration/#database)
- Run another `Postgresql container` in Docker.
  - I use [Kitematic](https://github.com/docker/kitematic/releases) to assist me to install the container.

<script src="https://gist.github.com/louis70109/5df4a4c46f852a13ca4f94e9b07c5d26.js"></script>

# 結論

# 參考

- [使用 Prometheus 和 Grafana 打造 Flask Web App 監控預警系統](https://blog.techbridge.cc/2019/08/26/how-to-use-prometheus-grafana-in-flask-app/)
- [Grafana 環境變數規則](https://grafana.com/docs/grafana/latest/administration/configuration/#configure-with-environment-variables)
- [Grafana database 參數設定](https://grafana.com/docs/grafana/latest/administration/configuration/#database)
