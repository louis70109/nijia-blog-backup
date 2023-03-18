---
title: 【標題】題目
categories: 學習紀錄
tags:
---

![](https://nijialin.com/images/common.jpeg)

# 前言

近年來，隨著雲端計算的普及和發展，越來越多的企業和開發者正在尋找一種更簡單、更高效的方式來佈署和運營應用程式。而 Severless 技術正是一種流行的解決方案。Google Cloud Run 是一個強大的 Severless 平台，可以幫助開發人員快速地佈署和運營。接著，本文將介紹 Google Cloud Run 的優點和如何在其中佈署。

<!-- more -->

# 介紹

## 為什麼我們需要使用 Severless 佈署我們的應用程式呢？

傳統的佈署方式需要管理和維護運行應用程式的基礎架構，包括服務器、網絡、資料庫等。這需要耗費大量時間和資源，並且需要購買硬體和安裝軟體環境。此外，當應用程式的流量遇到高峰時，需要擴展基礎架構以處理更多的請求，這也需要額外的投資人力和支援來完成。

而使用 Severless 佈署，開發者可以完全不必考慮基礎架構的維護和擴展，只需專注於撰寫應用程式。當使用者發送請求時，Severless 會自動處理應用程式的擴展性和可用性，以應對流量高峰。因此，Severless 佈署不僅更省時、省力，也更加彈性和可靠度。

由於 Severless 模型僅計費實際使用的計算資源和服務，因此在閒置時不會產生額外的成本，這對開發者和企業而言都是非常有利的。

### 御三家比較

以下是 GCP、AWS、Azure 三家 Severless 服務的比較表。這裡僅列舉了一些常見的計算資源和服務，如有其他需求，請參考各家雲服務商的官方文檔。

| Cloud Provider | 計算資源 | 代價單位 |  最小費用   |                其他服務                 |
| :------------: | :------: | :------: | :---------: | :-------------------------------------: |
|     Google     |   CPU    |   每秒   |   0.0001    |                   GCS                   |
|   Cloud Run    |  Memory  | 每 GB 秒 |  0.0000028  |      Pub/Sub, Firestore, BigQuery       |
|                |   vCPU   |   每秒   |  0.0000240  |                                         |
|                | 網路傳輸 |  每 GB   |    0.12     |                                         |
|                | 空間儲存 |  每 GB   |   0.0260    |                                         |
|                |          |          |             |                                         |
|      AWS       |   CPU    |   每秒   | 0.00001667  |                   S3                    |
|     Lambda     |  Memory  | 每 GB 秒 | 0.000000208 |       DynamoDB, API Gateway, SNS        |
|                | 網路傳輸 |  每 GB   |    0.09     |                                         |
|                | 空間儲存 |  每 GB   |   0.0230    |                                         |
|                |          |          |             |                                         |
|     Azure      |   CPU    |   每秒   |  0.000016   |              Blob Storage               |
|   Functions    |  Memory  | 每 GB 秒 |  0.0000016  | CosmosDB, Event Grid, Notification Hubs |
|                | 網路傳輸 |  每 GB   |    0.08     |                                         |
|                | 空間儲存 |  每 GB   |   0.0217    |                                         |

以上價格僅供參考，具體的費用和條件可能會因各家雲服務商的不同而有所不同。建議使用者在選擇之前，要詳細閱讀各家雲服務商的條款和費用結構，以選擇最適合自己的服務。

## GCP 介紹

Google Cloud Run 是 Google Cloud Platform (GCP) 的一個 Severless 平台，可讓開發人員在無需管理基礎設施的情況下輕鬆地佈署容器化應用程式。它支援多種程式語言和框架，包括 Node.js、Python、Go、Ruby、Java 和 .NET 等，因此開發人員可以選擇他們最熟悉的工具和框架來構建應用程式。

Google Cloud Run 的一個主要優點是它的彈性和可擴展性。它可以自動擴展 Instance，以滿足尖峰期流量需求；而在低流量時自動縮小 Instance，以節省資源和成本。此外，Google Cloud Run 支援快速啟動和停止容器，以縮短應用程式啟動時間和降低成本。

Google Cloud Run 還具有高可用性和可靠性。它使用 Google 的基礎設施和負載平衡，可以輕鬆地將流量轉發到全球各地的 Instance，從而實現全球性的高可用性和可靠性。此外，Google Cloud Run 提供了多種安全機制，包括網路隔離、身份驗證和授權等，可以幫助開發人員保護其應用程式免受攻擊和潛在漏洞的影響。

## 為什麼要使用 Google Cloud Run 作為 Severless 的優先選擇？

Google Cloud Run 具有以下優點，使其成為開發人員選擇 Severless 技術的優先選擇：

1. 自動擴展和縮小容器 Instance，以適應流量需求。
2. 快速啟動和停止容器，縮短應用程式啟動時間和降低成本。
3. 高可用性和可靠性，使用 Google 的基礎設施和負載平衡。
4. 多種安全機制，包括網路隔離、身份驗證和授權等。
5. 支援多種程式語言和框架，可滿足開發人員不同的需求。
6. 無需管理基礎設施，開發人員可以專注於應用程式的開發和佈署，而不是基礎設施的管理。

## 如何佈署到 Cloud Run 上

以下是將 FastAPI 佈署到 Google Cloud Run 上的執行指令的步驟：

### 1. 建立 Dockerfile

當你需要在不同的環境中運行 FastAPI 應用程式時，Docker 提供了一種簡單而有效的方式。以下是一個基於 Python 3.9、使用 Uvicorn 和 Gunicorn 作為伺服器的 FastAPI Dockerfile 範例：

```
FROM tiangolo/uvicorn-gunicorn-fastapi:python3.9

# 將專案複製到容器中
COPY ./app /app

# 安裝必要的套件
RUN pip install --upgrade pip
COPY requirements.txt .
RUN pip install -r requirements.txt

# 開放指定的埠號，讓容器外的系統能夠訪問應用程式
EXPOSE 80

# 啟動 FastAPI 應用程式
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "80"]

```

這個 Dockerfile 使用 tiangolo/uvicorn-gunicorn-fastapi 映像檔作為基底，並將應用程式碼複製到容器中，並安裝必要的套件。最後，使用 CMD 指令啟動 FastAPI 應用程式。

> 請注意，上述的 Dockerfile 需要依照您實際上的程式進行修改，以符合您的需求和環境。

### 2. 建立 requirements.txt 檔案

```
fastapi
uvicorn
```

### 3. 使用 Dockerfile 建立 Docker 映像檔

```
docker build -t my-fastapi-app .
```

### 4. 將 Docker 映像檔上傳到 Google Container Registry

```
docker tag my-fastapi-app gcr.io/[PROJECT_ID]/my-fastapi-app
docker push gcr.io/[PROJECT_ID]/my-fastapi-app
```

### 5. 佈署到 Google Cloud Run

```
gcloud run deploy --image gcr.io/[PROJECT_ID]/my-fastapi-app --platform managed
```

這樣就可以將 FastAPI 應用程式成功佈署到 Google Cloud Run 上了。

#### 測試是否正常運行

```
gcloud run services describe [SERVICE-NAME] --platform managed
```

上述指令中的 [SERVICE-NAME] 需要替換為您的服務名稱。成功運行後，您應該可以看到類似以下的輸出：

```
status:
  conditions:
  - lastTransitionTime: '2022-04-01T01:23:45Z'
    status: 'True'
    type: Ready
```

# 結論

Google Cloud Run 是一個功能強大的 Severless 平台，可以幫助開發人員快速地佈署和運行容器化應用程式，同時提供高可用性、可靠性和安全性。使用 Google Cloud Run，開發人員可以專注於應用程式的開發和佈署，而不必擔心基礎設施的管理和維護，因此是 Severless 技術的優先選擇之一。
