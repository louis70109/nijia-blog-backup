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

![](https://nijialin.com/images/1.png)

# 前言

梅竹官方為了讓學生朋友可以快速上手對應的廠商，因此在這天邀請我們去帶工作坊，我們則找到 UIT(a.k.a 前端)部門專業的同仁 - Coke 帶領學生們來做實作

<!-- more -->

# LINE Front-end Framework - Coke

<script async class="speakerdeck-embed" data-id="29f68cae8f9d4a80adde4ebf5a5fca5e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

<script async class="speakerdeck-embed" data-slide="4" data-id="29f68cae8f9d4a80adde4ebf5a5fca5e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

LIFF 是 LINE 提供的一個前端框架，主要是為了讓大家可以更快速的整合服務於 LINE App 身上，應用各種不一樣的場景在 LINE 上

<script async class="speakerdeck-embed" data-slide="6" data-id="29f68cae8f9d4a80adde4ebf5a5fca5e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

有效的整合讓大家可以快速應用以下的內容：

- LINE Login
- JavsScript SDK
- User Profile
- Message API

## Part 1 - liff starter

<script async class="speakerdeck-embed" data-slide="8" data-id="29f68cae8f9d4a80adde4ebf5a5fca5e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

首先從 LINE 官方的 repo - [line-liff-starter](https://github.com/line/line-liff-starter) Fork 至自己的 GitHub 帳號上，接著在 README 下方的 Heroku 部署按鈕會進入到 Heroku 的部署頁面

> 在按下這**部署按鈕**之前必須先註冊 [Heroku](https://www.heroku.com/) 的帳號，否則會在註冊完成後回來時已經遺失原先專案幫忙設定的 Config，因為註冊跳轉回來時 Config 已經被清除了。(當天許多同學有類似的問題)

<script async class="speakerdeck-embed" data-slide="12" data-id="29f68cae8f9d4a80adde4ebf5a5fca5e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

待建立完成後按下 `View` 進去後會看到錯誤訊息，代表這一步驟成功了。接著就是到 [LINE Developer Console](https://developers.line.biz/console) 註冊 LIFF 相關的 Channel。

<script async class="speakerdeck-embed" data-slide="15" data-id="29f68cae8f9d4a80adde4ebf5a5fca5e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

首先需要先建立 `Provider`，白話來說就是服務提供商的名稱，這邊就是讓同學們可以以自己的黑客松隊伍名稱取名。

<script async class="speakerdeck-embed" data-slide="17" data-id="29f68cae8f9d4a80adde4ebf5a5fca5e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

建立完 Provider 之後就要接著建立 LINE Login channel，因為 LIFF 是基於 LINE Login 所實作的一個整合服務應用的前端框架，讓大家可以在上面更有效的整合服務於 LINE 上。

這部分則是將`名稱`以及`描述`填寫清楚後即可建立 channel。(上面也會有敘述 `Provider` 是誰)

<script async class="speakerdeck-embed" data-slide="18" data-id="29f68cae8f9d4a80adde4ebf5a5fca5e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這邊 Coke 也詳細解釋剛剛所填寫的內容全都會在接下來使用者第一次使用時認證所需頁面會跳出來的資訊。

<script async class="speakerdeck-embed" data-slide="19" data-id="29f68cae8f9d4a80adde4ebf5a5fca5e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

接著來到 Login channel 裡面的 LIFF 頁籤中選擇 `Add` 建立第一個 LIFF 頁面(page)。

<script async class="speakerdeck-embed" data-slide="20" data-id="29f68cae8f9d4a80adde4ebf5a5fca5e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這一頁當中的需要打勾的 checkbox 一定要按照上面打勾，現場就有許多同學沒有打勾到 `chat_message.write` 導致訊息無法送出而找不出問題，這邊要詳細確認才行！

LIFF size 有分為以下三種：

- Full
- Tall
- Compact

<script async class="speakerdeck-embed" data-slide="23" data-id="29f68cae8f9d4a80adde4ebf5a5fca5e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

建立到下方之後會發現有個 `Bot link` 的選項，若你選擇 `normal` 時則會在下方看到有一個 **Add friend** 的按鈕，反之選擇 `aggressive` 實則會在 Allow 之後跳出一個加好友的選項讓使用者選擇。這邊就看各位開發者應用的場景去選擇囉！

<script async class="speakerdeck-embed" data-slide="25" data-id="29f68cae8f9d4a80adde4ebf5a5fca5e" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

畢竟這次 LINE 工作坊以 `shareTargetPicker` 這個強大且可以發送 Flex Message 的 API 作為主軸，因此這邊就提醒大家若要使用這個獨家功能的話，一定要打開按鈕才可以使用！

# 結論
