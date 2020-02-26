---
title: 如何在既有的機器人上增加 LINE Notify
tags:
---

之前寫了一個 flask 版本的 line notify [範例](https://github.com/louis70109/flask-line-notify)
這次就直接使用我之前的機器人 [Twitch Bot](https://github.com/louis70109/Twitch-Bot)上擴增綁定推播的功能
這次機器人初期預設是只有回覆功能，沒有綁定推播
但因為我時常沒跟到追蹤的直播主實況，憤而怒做 Notify 來消消氣 😆

新增 express
註冊 notify

藉由 LIFF 把 user id 放到 state 裡面（需要 state 使用說明）
在 notify callback 回來後會夾帶 code & state，而 state 是我們能控制的
將 user id 放在這的好處在於 Oauth 流程中這個 state 一般都會使用加密過的字串來
剛好 LINE user id 就很適合做這樣的使用
而我們順便藉由 callback 特性讓最後的頁面可以接收到 user id，在藉此去 mapping notify token
最後功能只要倒到對應的使用者 id 就可以進行推播了

> 每個 provider 都會有不同的 user id，所以不用擔心同一個 user id 到別人的 chatbot 上會有外流的問題喔！
