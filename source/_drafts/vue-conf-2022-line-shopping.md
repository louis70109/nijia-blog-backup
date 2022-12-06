---
title: 【標題】題目
categories: 學習紀錄
tags:
---


![](https://nijialin.com/images/2022/)
![](https://nijialin.com/images/common.jpeg)


# 前言

<!-- more -->

- [活動簡報](https://speakerdeck.com/line_developers_tw/line-shopping-vue-conf-sharing)

# 介紹

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/85764f222cc34173bd4c0054a833f922?slide=5" title="那些我們在LINE購物中自行打造的輪子" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

[LINE 購物](https://buy.line.me/) 是 2018/01 上線，當時 Vue 主流都還是在使用第二版，許多現在的新功能在當時都只能團隊來實作，如當時的 SSR 也是使用 Vue2 自行實作(弱勢現在當然就會用 Nuxt)。而在前端上也分成兩層，一個是 Web App、另一邊則是 API 層。

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/85764f222cc34173bd4c0054a833f922?slide=8" title="那些我們在LINE購物中自行打造的輪子" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

在上述的 tech stack 中，團隊也有導入 GraphQL，在眾多套件下就選擇引入 Vue-Apollo-3.0.0 Beta，由於它在使用上定義實作內容相當簡潔方便，程式碼也不至於太混亂，但一個套件有方便的地方也會有需要考慮的地方，如 Prefetch XSS(#158) 與 SSR issue(#329) 等等的問題需要解決，因此團隊上就須依照這兩個 issue 去針對解決。

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/85764f222cc34173bd4c0054a833f922?slide=10" title="那些我們在LINE購物中自行打造的輪子" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

如前面所說，網站主要分為 SSR 與 CSR 來負責不同的邏輯，

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/85764f222cc34173bd4c0054a833f922?slide=14" title="那些我們在LINE購物中自行打造的輪子" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

而在一個平台當中當然會有廣告來吸引不同的用戶客群，因應不同的步驟需要展示的廣告也都不同(對應各種 Component)，對應 Vue 渲染週期中都會需要知道之前的步驟是否完成，也有可能遇到先前步驟還沒完成就需要執行的挑戰。

~~放上廣告範例影片

> Page 16~26 可參考 LINE 購物 xxx 的週期

## History state

- Form Inputs
- Popup/Tab State
- Infinite Scrolling


- 使用下面參考的內容來對應 router 上操作
  - https://github.com/vuejs/vue-router/blob/dev/src/util/state-key.js
  - window.history.state.key
  - history.pushState({ key })

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/85764f222cc34173bd4c0054a833f922?slide=30" title="那些我們在LINE購物中自行打造的輪子" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

為什麼不用 keep-live 實作？

## 開發小技巧分享
<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/85764f222cc34173bd4c0054a833f922?slide=33" title="那些我們在LINE購物中自行打造的輪子" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>

這邊講者提到，通常開發者可能 80% 都使用 Mac 做開發，但實際市場上市 80% 用戶在使用 Windows，因此開發上也需要模擬一般用戶會遇到的體驗問題，除了可以從 Mac 的設定上操作，也可以透過 CSS 的方式處理這個問題：

<iframe class="speakerdeck-iframe" frameborder="0" src="https://speakerdeck.com/player/85764f222cc34173bd4c0054a833f922?slide=34" title="那些我們在LINE購物中自行打造的輪子" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true" style="border: 0px; background: padding-box padding-box rgba(0, 0, 0, 0.1); margin: 0px; padding: 0px; border-radius: 6px; box-shadow: rgba(0, 0, 0, 0.2) 0px 5px 40px; width: 560px; height: 314px;" data-ratio="1.78343949044586"></iframe>


# 結論

感謝這次來自研討會的邀約，讓同仁有機會可以到年度的研討會上分享 LINE 購物上前端開發的經驗，若以上的內容對於各位開發上有幫助，也歡迎大家分享出去喔！
# 活動小結

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：@line_tw_dev
![](https://www.evanlin.com/images/2020/line-tw-dev-qr.png)

# 關於「LINE 開發社群計畫」

LINE 於 2019 年開始在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來查看最新的狀況。詳情請看:

- [2021 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2021-line-tw-devrel/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)


<style>
  section.compact {
    font-size: 150%  
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
</style>