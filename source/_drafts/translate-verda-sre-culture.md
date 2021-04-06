---
title: 【翻譯】 [團隊 & 專案] 介紹 Site Reliability Engineering 團隊在 Verda platform 中所扮演的角色
categories: 翻譯
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

> 翻譯文章來自 LINE Engineering Blog - [[Team & Project] Introducing the team in charge of Site Reliability Engineering for the Verda platform](https://engineering.linecorp.com/en/blog/team-project-introducing-the-team-in-charge-of-site-reliability-engineering-for-the-verda-platform/)

在團隊與專案裡，每個部門與專案在 LINE 裡面都被介紹的很詳細，包含他們的職責、結構、技能樹、future issues 以及 roadmaps。本篇我們將會邀請負責 LINE 私有雲 - Verda 的 Site Reliability Engineering (SRE) 團隊成員 - Park Youngwoon、Hideki Yamada 以及 Kang Moon Joong 來做介紹。

![](https://nijialin.com/images/2021/translate/sre/1.png)

<!-- more -->

## 首先，請各位自我介紹自己吧！

**Park**: 大家好，我是 Verda 的 Site Reliability Engineering(簡稱 VRE) 主管，團隊位於來自韓國與日本，主要任務就是執行在 Verd 上的 SRE 相關任務。

**Yamada**: Hi，我是 VRE 團隊的資深工程師，平時在團隊中長處理 low-layer 層級的部分，包括 Server 以及 OS 相關的故障排除。由於**雲端基礎架構**的開發和營運中使用到許多技術，因此日常工作也會涉及管理雲端資源以及評估實體資源採購相關的作業。

**Kang**: 我在 2019 年畢業之後加入了位於韓國的團隊。在加入公司之前，我曾在大學實驗室中負責過系統監控相關工作，現在我也利用我學到的經驗來開發和營運整個 Verda 的系統。

## 為什麼你們想加入 LINE 呢？

**Park**: 在上一份工作中，我在一家提供公有雲服務的公司中擔任 IaaS 的開發和營運主管。但是因為前公司的策略關係讓我覺得與用戶距離越來越遠，且我想繼續增加更多 IaaS 領域的開發經驗，因緣際會下我決定加入 Verda 團隊，並為為內部開發人員提供更多私有雲層級的服務。

**Yamada**: 在上一份工作中，我主要負責為公司行號(或集團)尋找與開發雲端服務的解決方案，在這份工作中我無法親身經歷整個雲端的交付與營運週期。因此我決定加入Verda團隊，除了與我自身的專業能力相符之外，團隊提供我有許多開發以及營運的空間，並且讓我能夠開發出與使用者息息相關的平台。

**Kang**: My major at university was cloud computing, and I had been eyeing LINE as a company in Korea that would allow me to work in that field. In particular, the work of the VRE team aligned with my specialty, so I decided to join the company after my internship. What impressed me most about my internship experience was that I was able to take the initiative in discovering and solving problems. I received a lot of feedback from the team members on my efforts, and I felt engaged at work, which was key to my decision to join the company.

# 結論
