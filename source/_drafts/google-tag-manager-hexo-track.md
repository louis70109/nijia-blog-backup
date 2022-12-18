---
title: 【標題】題目
categories: 學習紀錄
tags:
---


![](https://nijialin.com/images/2022/)
![](https://nijialin.com/images/common.jpeg)


# 前言

- Google Tag Manager 以下簡稱 GTM
- Google Analytics 簡稱 GA
<!-- more -->

# 流程圖

TBC

# 介紹

# Hexo 中怎麼放入 GTM?

themes > next > layout > _partials > head > head.swig

在 `<meta>` 前後放上，官方文件上有寫要放在 <head> 附近，讓 GTM js code 可以預載入

```
...
<meta name="theme-color" content="{{ theme.android_chrome_color }}">
<meta name="generator" content="Hexo {{ hexo_version }}">

<!-- Google Tag Manager -->
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-YOUR_GTM_CODE');</script>
<!-- End Google Tag Manager -->

{%- if theme.favicon.apple_touch_icon %}
  <link rel="apple-touch-icon" sizes="180x180" href="{{ url_for(theme.favicon.apple_touch_icon) }}">
{%- endif %}
...

```

## 針對特定按鈕想追蹤怎辦？

## Q&A

### 以前我都要放 UA-xxx，那現在我GA要放哪？(G-xxxx)

只要 GTM 裡面有設定觸發之後打到對應的 GA後，就不用管現在的G-xxx 追蹤碼了，因為當GTM 觸發之後他就會把相關流量打給GA，因此給工程師 GTM 追蹤碼之後就可以開始進後台做事啦：）
# 結論

# 參考好文

- [GTM是什麼？入門必看的Google Tag Manager 代碼管理工具設定教學！](https://doordata.tw/blog/gtm-tutorial-for-beginner)
