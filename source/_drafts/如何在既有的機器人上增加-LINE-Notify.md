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
