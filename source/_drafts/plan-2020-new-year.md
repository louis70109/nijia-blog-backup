---
title: recap serverless
tags:
---

2019 的鐵人賽中我寫了使用 [serverless 串接 LINE API 的三十天文章](https://nijialin.com/categories/2019%E9%90%B5%E4%BA%BA%E8%B3%BD/)，最近有些使用上的心得就想說來寫一篇來表達一下

裡頭提到很多使用 flask + WSGI 去建立 RESTful API，雖然這樣架起來之後很方便，也可以把其他服務(IoT、SQS、SNS...)透過`yaml`設定就能啟用 

但我私心認為 API 應該要獨立開來去建立成一個 container 或是在 Server 上，因為當所有關聯服務都在同一個資料夾下時都服務越來越複雜時會導致整體服務被雲平台綁架走，而導致裡頭服務不敢更動

因此我認為若有使用 AWS 服務的話用 serverless 寫`yaml`去控制裡頭的相依設定以及調用`Lambda`來觸發任務會是比較好的選擇

而將 API 轉換成 container 之類的則可以更有彈性的切換到各個雲平台上(AWS、Google、Azure...)，只需要一個 container 就能解決這個問題

雖然 AWS Lambda 有 Auto-scaling 的服務，但在整個服務綁在一起之後就會一直依賴雲平台而沒辦法自己控制整體狀態
