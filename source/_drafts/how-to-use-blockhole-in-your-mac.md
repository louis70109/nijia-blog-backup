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

![](https://nijialin.com/images/2021/)

# 前言

常常看著我的另外一篇設定直播的文章 - [如何只使用一台 Mac 進行直播 feat. SoundFlower, OBS, Youtube](https://nijialin.com/2020/11/29/mac-stream-soundflower/) 長期蟬聯本部落格的流量冠軍(感謝大家愛戴)，本次介紹的另一個直播方案是

實測 BlockHole 是從麥克風的方式把聲音打進去給電腦，SoundFlower 的方式則是從擷取輸出的地方把整個聲音拉走
結論：在 OBS 設定中要把 BlackHole 設定在麥克風選項，假日再來寫一篇ＸＤ

<!-- more -->

# 介紹

進入 OBS 右下角的設定中，在麥克風選項中選上 BlockHole16h 的選項
![](https://nijialin.com/images/2021/blockhole/set-obs-micro.png)

你可能會很困惑為什麼在用 SoundFlower 時是在`輸出時`選，但在這邊卻是在`輸入時`選，就目前實測起來時 SoundFlower 的做法是把輸出端的聲音全部接走，因此若你有參考此篇 [如何只使用一台 Mac 進行直播 feat. SoundFlower, OBS, Youtube](https://nijialin.com/2020/11/29/mac-stream-soundflower/) 的話，你會發現無法在電腦前聽到聲音，但在直播上聽得到聲音(記憶中直播機也無法打出麥克風)。

而這次使用 BlockHole 他則是透過`輸入`的方式進入，在 OBS 中可以同步設定你自己的麥克風，且兩個不會衝突，簡單說它的做法就是將**電腦桌面的聲音**透過**轉換成輸入**的方式，因此此種方式就不會讓直播機(筆電)聽不到聲音，就可以即時跟同個會議(對話群組)的人講話了。(~~雖然電腦會很燙~~)

# 結論
