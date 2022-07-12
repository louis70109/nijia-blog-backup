---
title: 【標題】題目
categories: 學習紀錄
tags:
---

![](https://nijialin.com/images/2022/)
![](https://nijialin.com/images/common.jpeg)

# 前言

<!-- more -->

# 介紹

## cloud run


參考文件：[Quick Start](https://cloud.google.com/run/docs/quickstarts/build-and-deploy/deploy-python-service)

參考指令：[【GDG】Google I/O 2022 Extended 線下活動分享](https://nijialin.com/2022/07/01/google-io-extended-2022/)

cloud build -> cloud storage 會開個資料夾 -> gcr.io 幫建立個 container image ->


> 需要 Dockerfile 才會部署成功。[文件](https://cloud.google.com/run/docs/deploying-source-code)

官方使用 flask，而我叫習慣使用 FastAPI，因此魔改了官方的範例，大家可以看看實際上有什麼差別～

```Dockerfile
# Use the official lightweight Python image.
# https://hub.docker.com/_/python
FROM python:3.10-slim

# Allow statements and log messages to immediately appear in the Knative logs
ENV PYTHONUNBUFFERED True

# Copy local code to the container image.
ENV APP_HOME /app
WORKDIR $APP_HOME
COPY . ./

# Install production dependencies.
RUN pip install --no-cache-dir -r requirements.txt

# Run the web service on container startup. Here we use the gunicorn
# webserver, with one worker process and 8 threads.
# For environments with multiple CPU cores, increase the number of workers
# to be equal to the cores available.
# Timeout is set to 0 to disable the timeouts of the workers to allow Cloud Run to handle instance scaling.
CMD exec gunicorn --bind :$PORT --workers 1 --threads 8 --timeout 0 main:app
```
### 設定 cloud run TRIGGER
這邊連動著 eventarc ，設定 cloud storage

### 測試上傳檔案

receive object by POST event:

```

{'kind': 'storage#object', 'id': 'my-nijia-bucket-2/27____5760_n.jpeg/1656782882137120', 'selfLink': 'https://www.googleapis.com/storage/v1/b/my-nijia-bucket-2/o/27___25760_n.jpeg', 'name': '2721___=___25760_n.jpeg', 'bucket': 'my-nijia-bucket-2', 'generation': '1656782882137120', 'metageneration': '1', 'contentType': 'image/jpeg', 'timeCreated': '2022-07-02T17:28:02.205Z', 'updated': '2022-07-02T17:28:02.205Z', 'storageClass': 'STANDARD', 'timeStorageClassUpdated': '2022-07-02T17:28:02.205Z', 'size': '78216', 'md5Hash': 'lP1zwjuWC5Ld7aMNkqHBIQ==', 'mediaLink': 'https://www.googleapis.com/download/storage/v1/b/my-nijia-bucket-2/o/27__25760_n.jpeg?generation=1656782882137120&alt=media', 'crc32c': 'Ce____==', 'etag': 'CKDI____EAE='}
```
## eventarc


quick start: https://cloud.google.com/eventarc/docs/workflows/quickstart-pubsub?hl=zh-tw
照著文件輸入這個啟動服務

```
gcloud services enable eventarc.googleapis.com pubsub.googleapis.com workfl
ows.googleapis.com workflowexecutions.googleapis.com
```

他會要求你登入，或是登入過就可以切帳號

```
$ gcloud auth login
$ gcloud config set account ACCOUNT
```

登入完後會跟你說，你現在登入帳號、使用哪個 project，以我來說就要切換，因此要先用第一個指令

```
You are now logged in as [louis70109@gmail.com].
Your current project is [nijia-test].  You can change this setting by running:
  $ gcloud config set project PROJECT_ID


Updates are available for some Google Cloud CLI components.  To install them,
please run:
  $ gcloud components update
```


set eventarc envs
```
export WORKFLOW_LOCATION=us-central1
export TRIGGER_LOCATION=us-central1
export PROJECT_ID=PROJECT_ID
gcloud config set project ${PROJECT_ID}
gcloud config set workflows/location ${WORKFLOW_LOCATION}
gcloud config set eventarc/location ${TRIGGER_LOCATION}
```

# 結論

# 活動小結

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：@line_tw_dev
![](https://www.evanlin.com/images/2020/line-tw-dev-qr.png)

# 關於「LINE 開發社群計畫」

LINE 於 2019 年開始在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來查看最新的狀況。詳情請看:

- [2021 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2021-line-tw-devrel/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)

<style>
  section.compact {
    font-size: 150%  
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
</style>
