---
title: 【在 LINE 中用語音訂飲料】串接 Google STT 前置作業
categories: Google
tags:
---


![](https://nijialin.com/images/2022/)

# 前言


- 串接 STT 的前置作業 (IAM and Bucket)
- STT 串接說明
  - 細節調整
- LINE Bot 語音檔案處理與分析
- Firebase IAM role setting
- Firestore setting and upload data
  - Python code
- Local testing
  - 一般開發方式
  - k3d
- Deploy to GKE
- gcloud install
  - Download: https://cloud.google.com/sdk/docs/install

```
gcloud config set project PROJECT_ID
```

<!-- more -->

使用 GCP 建立 Speech-to-Text(語音轉文字)時有三個步驟需要執行

- 建立專案
- IAM Role(權限申請)
- Cloud Bucket(音檔儲存空間)
- Speech-to-text(服務本身)

接下來為大家介紹

## 1. 建立 GCP 專案

![](https://nijialin.com/images/2022/speech-1/create-project.png)

想使用 Google Cloud 服務時，都是以一個 Project 為單位來使用各種服務，因此可以參考圖片來建立一個 Project，名字以好辨別為主，後續再追朔費用時才會知道是誰花的錢(笑)。

> 如果讀者有遇到費用超標問題，可以參考我之前寫的文章：[【GCP】忘記關服務產生費用該怎麼辦？](https://nijialin.com/2020/08/17/gcp-billing-support/)

## 2. 申請 IAM & Admin

使用各種 Public/Private Cloud 時，都需要申請金鑰才有權限透過機器去訪問各種服務的 API 們。

因此我們先到 GCP 的任意頁面中，點選左上角的`漢堡`後選擇 `IAM & Admin`，接著裡點到分頁中的 `Service Accounts`

![](https://nijialin.com/images/2022/speech-1/iam1.png)

來到這裡之後，因為可能之前什麼都沒建立，請選擇 `CREATE SERVICE ACCOUNT`
![](https://nijialin.com/images/2022/speech-1/iam2.png)

把當中內容填寫完送出之後，點選剛剛你建立的 Service account，並看到畫面中有出現 `KEYS` 的子頁面，給他大力的點下去，並接著看到 `ADD KEY` 的地方，透過它來建立一個可以訪問服務的 JSON 檔。
![](https://nijialin.com/images/2022/speech-1/role.png)

### 影片

<iframe width="560" height="315" src="https://www.youtube.com/embed/EODGZnE8eUI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## 設定 Service Account

![](https://nijialin.com/images/2022/speech-1/iam1.png)

到 GCP 左上角的漢堡中可以點選，找到 IAM & ADMIN 的地方，點進去後就進到管理頁面。

![](https://nijialin.com/images/2022/speech-1/iam2.png)

進入後點到左邊的 Service Account，上方的 `Create Service Account` 給他按下去後，照著步驟把相關的內容填完(如影片)。

<iframe width="560" height="315" src="https://www.youtube.com/embed/EODGZnE8eUI?start=302" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

建立完後要到 `KEYS` 的 tab，按下  `ADD KEY` 的按鈕後， `Create new key`，最後就能拿到我們今天要的 JSON 金鑰，把它存在接下來要使用的專案位置上即可。

## 建立 Cloud Bucket

如果有使用 AWS 的朋友應該會知道，這個功能相當於 S3，讓大家有個儲存的空間，並且可以做檔案的權限控管，並可以透過 API CRUD，

# 結論

下一篇將開始介紹如何使用剛剛拿到的 JSON Key，進一步開始實測建立 Bucket 的步驟。