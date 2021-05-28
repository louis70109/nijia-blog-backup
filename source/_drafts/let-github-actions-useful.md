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


# 前言

今天與大家分享一個 GitHub Actions 的小應用，由於 Hexo 是透過 JavaScript 撰寫，平時撰寫完 Markdown 文章之後，再透過編譯的方式編譯成 HTML 的靜態檔案到 [GitHub Page 上](https://github.com/louis70109/louis70109.github.io)，但是如果每次都要自己透過專案下 hexo 編譯指令的話會因為不同<mark>電腦環境</mark>關係導致部署上去版本有誤而出現部落格壞掉的狀態。

經過了一些時日我將手動下指令的部分改成透過 GitHub Actions 來代替我下編譯的指令，雖然要透過 Git push 才會觸發(Trigger)，至少環境是 fix 的狀態且是透過機器下固定指令，也不會遇到版本以及環境問題而導致部落格直接炸掉的狀態
😆

那我在先前都有寫過相關的內容，除了提供一個 LINE Notify 的 GitHub Actions 套件之外，也有一篇帶大家建立處於自己的服務於市集中，大家可以參考：

- [line-notify-action](https://github.com/louis70109/line-notify-action)
- [如何建置與使用 GitHub Actions 市集的 LINE Notify 套件](https://nijialin.com/2021/02/17/line-notify-in-github-actions/)
<!-- more -->

# 介紹

# 結論
