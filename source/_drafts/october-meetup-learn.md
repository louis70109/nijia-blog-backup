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

![](https://nijialin.com/2020/images/1.png)

# 前言

<!-- more -->

# 介紹

<script async class="speakerdeck-embed" data-id="309683770a504ecabd914ce256874ab7" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>

- eBPF（extended Berkeley Packet Filter）
- 介紹了 cilium code review
  - eBPF based networking

原本是 `封包過濾機制` 相關工具，因為擴增後則變成 Linux 核心內建的內部行為分析工具包含以下:

- 動態追蹤 (dynamic tracing);
- 靜態追蹤 (static tracing);
- profiling events;

在安全方面 BPF 的測試碼最終將執行在核心內部沙盒 (sandbox) 隔離環境 (虛擬機器) 內。

> [參考這邊](https://hackmd.io/@sysprog/linux-ebpf?type=view)

Google 了一下看到這邊才比較了解 eBPF 究竟在哪一層
![](https://nijialin.com/2020/images/cloud-native-33/eBPF-cilium-arch.jpg)

# 結論

# 參考

- [Google 新版 GKE 資料平面支援 eBPF 技術，增加容器可見性與安全性](https://www.ithome.com.tw/news/139519)
