---
title: '2019 LINE Dev Day - 議程心得(3)'
tags:
---


# Armeria: A Microservice Framework Well-suited Everywhere
![](https://i.imgur.com/MNnrFnm.jpg)

- [簡報連結](https://speakerdeck.com/line_devday2019/armeria-a-microservice-framework-well-suited-everywhere)
- [Github](https://github.com/line/armeria)
- [官網](https://line.github.io/armeria/)

# 前言
大家好我是 [Chatbot Developer Taiwan](https://www.facebook.com/groups/chatbot.tw/) - NiJia，很開心這次能夠以 LINE API Expert 的身份被邀請來參加 LINE Developer Day 2019。

今年參加八月舉辦的 COSCUP，並且在第一天的 after party 參加 LINE BoF 上就已經看到 LINE 開發的 Open Source - Armeria，它是使用 Java 所撰寫的一個非同步的專案，支援 Java8, Netty, HTTP/2, Thrift 以及 gRPC。

據之前的議程的以及講者的分享說這個服務已經被應用於很多 LINE 服務裡頭，因為覺得好用才推出來🤣

接下來就用 Java code 來簡單火力展示如何用一個串聯式寫法把服務互叫起來，不管是要用什麼服務只要用串接的方式加入即可，像是 gRPC、Thirft、annotation...等等如下面幾張圖所示。

![](https://i.imgur.com/Z9jfFkI.png)

---

![](https://i.imgur.com/6rAex3K.png)

---

![](https://i.imgur.com/mAKhwh4.png)

---

![](https://i.imgur.com/KKU0eXG.png)

# 為什麼要做成 async 以及 reactive
首先就先提到若 Queue 裡頭的東西若是都 sync 的話會有什麼問題，這邊就以一個 Call API 常遇到的問題 - Timeout，在大量的 Queue 在排隊時，以 sync 的方式存在時光遇到 Timeout 就會有服務器爆炸的問題，因為彼此不能影響彼此，且這件事會發生在真實世界的每個地方。
![](https://i.imgur.com/Telr7lG.jpg)

---

![](https://i.imgur.com/hkltFFS.jpg)

這邊講者提出的解決方案為：
- 增加執行緒的標記(#)並且減少呼叫堆疊(stack)
- 預準備 Tread pools 讓大家互相共享
- 少調用 points
- 使用非同步的好處就是能夠平行呼叫+較少的執行緒

現在他們能用非同步的方式解決系統被鎖住的問題，但今天若遇到一個很肥～的 payload 呢？以範例來說若一個用戶送他 10 MB 的大小，一次送給 100K 個用戶就相當於 1 TB 大小的流量。
這邊使用的方法是ˇ用不同的平寬 & 處理能力，並且只需要足夠的 buffer 來排除  Out of Memory 的錯誤