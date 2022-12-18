---
title: 【標題】題目
categories: 學習紀錄
tags:
---


![](https://nijialin.com/images/2022/)
![](https://nijialin.com/images/common.jpeg)


# 前言

<!-- more -->

# 介紹

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
# 結論
