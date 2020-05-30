---
title:
  "[object Object]": null
categories: 學習紀錄
tags:
---

![](https://i.imgur.com/0QAGPDc.png)

# 前言

<!-- more -->

# 從輸入`https://www.google.com`之後發生了什麼事?

首先須了解`https://www.google.com`這樣的網址是如何組成:

1. https: 通訊協定，其他常見如: tcp、udp、websocket、mqtt...
2. www: 常聽到的 sub domain 就指這個部分，也會聽到 host 的名稱，意指在一個 Domain 下若有多個主機時則用這個部分來指定名稱為特定主機，一般預設進入點為 `www`。
3. .google: 這部分學名為 `Second Level Domain`(SLD)，在 Top level domain 搜尋完後接著搜尋的層級，通常為個人品牌、公司行號為名稱。
4. .com: 這層名為 `Top Level Domain`(TLD)，常見為 com、org、gov、edu、io，較好理解的方式我認為就是把當前進入點判斷為何種`組織`，再以此分類下去找 SLD，有點二元搜尋的概念 😁。
5. root: 一開始我看到這部分也覺得霧煞煞，簡單來說每個域名(Domain)的結尾都會有 `.` 這個小數點，它是指域名(Domain)的進入點，所有上的 Domain 都會從這個地方開始判斷。

> 上述是照著網址由左而右寫，實際上則是從右往左判斷

上面步驟已經說明清楚每個部分了，接下來就說明從瀏覽器輸入網址後的步驟吧！

## 向 DNS 要 IP

![](https://i.imgur.com/8IUwjtr.png)

> 參考[六角學院](https://w3c.hexschool.com/blog/8d691e4f)

DNS 全名為 Domain Name Server，主要職責是幫忙把 網域名稱(Domain Name) 轉成 IP，因為網域名稱是人才看得懂而機器只認得 IP，因此需要 DNS 來幫忙轉譯。

### Name Server

藉由上圖最終 DNS 會收到每個單獨的 Name Server 回傳後的值並組成 IP 回傳給瀏覽器。

## 跟 IP 請求資源

待瀏覽器收到 IP 後去請求資源，而 IP (資源方)那一般來說都會有個 Web Server 擋在前面(Nginx、Apache)，若是有前端頁面則是讓瀏覽器下載靜態檔案(static)，而若只是單純導向至 API 的話就直接回傳定義的資料格式(JSON、XML...)。

## 快取

此時瀏覽器下載完後則會存到快取(Cache)裡，加速下次載入。

## 渲染

![https://i.imgur.com/ddrEQxs.png](https://i.imgur.com/ddrEQxs.png)

> 參考[六角學院](https://w3c.hexschool.com/blog/8d691e4f)

這邊就簡單敘述一下前端渲染發生的經過，HTML 會產生出一個 `DOM Tree`，CSS 會有一個 `CSSOM Tree`，在各別產生完後會合併成一個 `render Tree`，最後經由 `layout` 的步驟讓瀏覽器將 Tree 渲染至畫面上，完成畫面顯示的步驟。

- 上述的 DOM 就是寫 jQuery 時呼叫的那個 DOM 元素

以上就是當你輸入一個網址後會遇到的事情經過～

# 輸入網址後，你怎能不知道 HTTP 呢？

## 準備連線 - 三方交握 (Three-Way Handshake)

![](https://i.imgur.com/9pRGWnc.png)

這邊我用最簡單的表示，`SYN`在三方交握會是一個帶有序列號(n)的請求，而`ACK`則是代表回應對方我們這邊收到的訊號，會帶有 n+1 的數字回傳。

在三方交握中，會先由 Client 告訴 Server 現在它要連線並給一個數字，回傳時會送 n+1 的原因是避免在請求的過程中因各種因素導致回來的值錯誤時的一個防範機制，用 `+1` 這個做法來確保對方給的回傳值是我剛剛送出去的值 +1，避免連線過程中混亂。

簡單的記法就是從 Client 先送一個數字 N 給 Server，而回傳時一定是給 N+1 並且帶著一個 M，Client 收到後確認完則在回傳 M+1 讓 Server 也確定 CLient 收到了，完成三次連線。

### Bonus - 為什麼不兩次獲四次交握呢？

經過上述的流程，一定是一個發(SYN)，一個收完後告訴對方它收到(ACK)，那

## 斷開連線 - 四次揮手

# SSL

# OAuth

讓客戶端能以 OAuth 開放標準在第三方應用程式上透過授權(Authorization)的方式取得在服務提供商(LINE、Facebook、Google...)的資料(檔案、照片、影片...)。

## 四種角色

- Resource Owner(簡稱 RO)：可以授權於`終端用戶`存取受保護之資料。
- Resource Server(簡稱 RS)：存取受保護資料的地方，根據 Access Token 之權限處理請求。
- Client：代表使用者去存取受保護資料的應用程式。Client 指任何在 Server 端、桌面或設備上執行的應用程式。
- Authorization Server(簡稱 AS)：職責為認證過使用者的身份，且經由使用者許可後，就會簽發 Access Token 的地方。

# 流程

以下為一個 OAuth 的流程:

```
+--------+                               +---------------+
|        |--(1)- Authorization Request ->|   Resource    |
|        |                               |     Owner     |
|        |<-(2)-- Authorization Grant ---|               |
|        |                               +---------------+
|        |
|        |                               +---------------+
|        |--(3)-- Authorization Grant -->| Authorization |
| Client |                               |     Server    |
|        |<-(4)----- Access Token -------|               |
|        |                               +---------------+
|        |
|        |                               +---------------+
|        |--(5)----- Access Token ------>|    Resource   |
|        |                               |     Server    |
|        |<-(6)--- Protected Resource ---|               |
+--------+                               +---------------+
```

以下會分別用四個角色代替他們：
Client = A 員工、RO = 大樓警衛、AS = 公司櫃檯、RS = 倉庫

並用小故事說明，情境是員工假日需返回公司倉庫拿取零件，但是卻沒帶公司的證件，而公司是在商業辦公室中，大樓警衛認不得這麼多間公司的人，因此需要按照基本流程才能進公司拿取資料，A 員工抵達商辦大樓後：

1. A 員工拿證件出來並填寫基本資料的單子給警衛 (發送請求)
2. 警衛確認完後拿了一個暫時性的鑰匙(`code`)給 A 員工
3. A 員工拿著暫時性鑰匙(`code`)跟公司櫃檯
4. 櫃檯將臨時鑰匙(`code`)換成公司的門禁卡(Access Token)
5. A 員工去倉庫使用門禁卡(Access Token)開倉庫門
6. 倉庫門打開後 A 員工從裡面拿取自己需要的零件(Protected Resource)

> 透過這樣的解釋應該比較好懂吧 ❓

# OpenID

# 結論
