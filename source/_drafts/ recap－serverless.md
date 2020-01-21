---
title: recap serverless
tags:
---

# 前言

這陣子在公司使用[Serverless](https://github.com/serverless/serverless)建立許多的服務在`AWS`上，而套件上也提供了[serverless-wsgi](https://www.npmjs.com/package/serverless-wsgi)這方便的的工具，讓需要快速上線一個 API 服務不再那麼難，同時也可以快速介接 AWS 的 API gateway 以及 Lambda 來實作`Serverless`架構的 API 服務。此外 Lambda 的另一個功能就是串接 AWS 上的各種服務，像是`SQS`、`SNS`、`IoT`..等等的服務，都需要在事件被觸發後有個實體(Lambda)來幫忙執行事件處理，總之講了這麼多就要來稍微抱怨一下 😆

2019 的鐵人賽中我寫了使用 [serverless 串接 LINE API 的三十天文章](https://nijialin.com/categories/2019%E9%90%B5%E4%BA%BA%E8%B3%BD/)，裡頭提到很多使用 flask + WSGI 並搭配 LINE API 去建立 RESTful API，雖然這樣架起來之後很方便，但如果串到其他服務時就會有所有東西綁在一起搞成一大包的困擾

所以我私心認為 API 應該要獨立開來去建立成一個 container 或是在 Server 上，因為當所有關聯服務都在同一個資料夾下時都服務越來越複雜時會導致整體服務被雲平台綁架走，而導致裡頭服務不敢更動

因此我認為若有使用 AWS 服務的話用 serverless 寫`yaml`去控制裡頭的相依設定以及調用 AWS 上各種服務與`Lambda`相依作用來完成觸發任務會是比較好的選擇
雖然 AWS Lambda 有 Auto-scaling 的服務，但在整個服務綁在一起之後就會一直依賴雲平台而沒辦法自己控制整體狀態

而將 API 轉換成 container 之類的則可以更有彈性的切換到各個雲平台上(AWS、Google、Azure...)，只需要一個 container 就能解決這個問題

使用 Serverless 專門來處理 AWS 上的各種應用服務可以讓這包程式不會因為加了 API 而讓整個專案耦合性暴增，彼此都用 call API 的方式互相溝通，達到微服務的開發方式，即便未來不想用 AWS 的服務時在切割專案時只需要換掉 Serverless 這包而不是將 container 刪除，如此一來 API 擁有 Docker 的靈活性並且擁有 Serverless 快速介接 AWS 的能力，
