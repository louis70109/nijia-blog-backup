---
title: 'TECHPULSE 2020 - Keynote'
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

![](https://nijialin.com/images/2020/techpulse/1.JPG)

# 前言

各位好，我是 LINE TAIWAN 的技術推廣工程師 - NiJia Lin，很開心這次能以不同的身份(LINER)來參加於南港展覽館二館舉辦的一年一度 LINE 技術大會 - TECHPULSE，雖然今年很可惜的因為疫情關係無法邀請海外講者來台灣與各位分享，但同時也讓大家了解到 LINE Taiwan 工程團隊實力也是深不可測，這次我也將透過這篇文章讓你了解 LINE 所帶來的魔力吧！

> 在此之前也有分享一篇詳細的文章 - 歡迎大家參考 [您不能錯過的 LINE TAIWAN TECHPULSE 2020 年度盛會](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-techpulse-2020/)

<!-- more -->

# 焦點回顧 1 - [Keynote](https://speakerdeck.com/line_developers_tw/line-techpulse-2020-keynote) / Marco Chen

![](https://nijialin.com/images/2020/techpulse/keynote-4.jpg)

## New Norma(新常態)

<script async class="speakerdeck-embed" data-slide="7" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

今年因為疫情，從全球、地區、公司、甚至到你我的生活中皆被影響。而 LINE 是以網路服務為基礎的通訊軟體也因為大家使用網路的需求量變多，在平台上也獲得了成長，整理如下：

- 官方帳號上`三月與四月`相比成長了 `140%`
- 視訊電話`二月到五月`上漲 `235%`
- LINE TODAY 的`中華職棒(CPBL)`一度閉門比賽，讓線上直播成長了 `74%`
- 因為藝人們紛紛尋找線上直播的解決方案，因此直播的人數也是大大的提升
- 國內旅遊一度被影響到相當嚴重，但適逢疫情舒緩以及連假，LINE TRAVEL 一度成長了 `24 倍`之多！

## 台灣工程團隊的考量點

<script async class="speakerdeck-embed" data-slide="9" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

雖然 LINE 時常應付大流量在各服務間均已經有相對應的策略，但隨著公司的成長同時 LINE 工程團隊也需要優化基礎設施，讓平台在接受這麼大的流量可以更`有效地使用資源`，並且提供更穩定的基礎設施來增加`彈性`與`可用性`。

過往大多以`虛擬主機(VM)`為基礎設施去部署服務，但今年在策略上開發團隊需要更著重於`使用效率`與`維護性`，而在每個服務為了應付`流量高峰`而事先準備了許多資源(機器)，並會相依不同的技術元件，導致無法經驗交流分享。在這之後我們意識到只有`作業系統虛擬化平台`還不夠，我們需要一個`執行環境虛擬化平台`，把應用程式與其相依性資源封裝起來。才能完全解決應用層與執行環境的區隔，讓應用程式可以任意的被部署在不同地方，而不會有資源相依性與版本衝突的問題。

<script async class="speakerdeck-embed" data-slide="12" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

與此同時，LINE 總部正在著手建立 `Verda Kubernetes Service`(`VKS`)，提供一個平台讓全球服務能夠使用，雖然這時 Container-based 的架構熱度非常高，但要建立一個平台絕對是有所考量，在開發時則考量以下三個部分：

- `靈活性`: 需要能夠自由擴充管理功能。
- `易用性`: 擁有許多生態系資源與 Open Source Software 可以使用。
- `維護成本`: 開發社群的活躍度，如果有 Bug 需要能很快被修復。

<script async class="speakerdeck-embed" data-slide="13" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

而在總部建置 VKS 時，台灣的工程部門團隊因為流量上升而收到很多新專案的開發需求，為了有效利用人力資源，我們正在研究如何強化開發與部署的效率，並在研究如果更好運用 Kubernetes。

當給台灣工程團隊有二個中長期目標：

- 部署效率
- 自動擴展(Auto-Scaling)

## 策略

<script async class="speakerdeck-embed" data-slide="15" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

在有一定規模下要引入一個新技術，許多東西需要持續優化改進，因此在這次的引入中組成了專案小組(Task Force)，讓原本服務間無法有效共用元件的問題逐一排除。首先，須先讓各個團隊對於 Kubernetes 有一定的認知，因此從`讀書會`-`準備教材`-`課程訓練`，經由一個這樣的週期讓學員可以對於技術有一定的掌握度，與此之後並成立了 SRE 團隊，協助排除日後專案中所遇到的問題，記錄下來讓經驗得以傳承，並與海外同事一同合作讓這平台更穩定。

## 成果

<script async class="speakerdeck-embed" data-slide="18" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

除了原先預定的兩個方向`部署效率`以及`Auto-Scaling`以外，我們又額外獲得了兩個好處，不僅擁有更多的監控、追查問題工具，也讓系統微服務化，協同開發時相互影響的問題也降低了。

## 小結

在有規模的企業中導入任何技術都不容易，需要制定一定的策略才有辦法應付過程中的挑戰，如果讀者們也在嘗試導入的話，不如參考看看吧！

> 如果你對於 DevOps 或容器化相關技術有興趣可以前往這兩個社團：

- [Cloud Native Taiwan User Group](https://www.facebook.com/groups/cloudnative.tw)
- [DevOps Taiwan](https://www.facebook.com/groups/DevOpsTaiwan/)

# 焦點回顧 2 - [Life on LINE CLOVA](https://speakerdeck.com/line_developers_tw/line-techpulse-2020-life-on-line-clova) - Aaron Wu / Cid Chang

![](https://nijialin.com/images/2020/techpulse/clova-aaron.jpg)

<script async class="speakerdeck-embed" data-slide="8" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

經過了一年的努力，將旗下兩大 AI 主力的品牌 LINE BRAIN 與 LINE Clova 整合成 LINE CLOVA，統整出 AI 產品與兩大解決方案：

## 三大產品

1. Chatbot

讓用戶可以在很短的時間內建造出一隻 LINE AI Bot，除了有基礎的樣板之外，還能夠客製化調整調整內容格式，並同時支援六種以上的功能。

在 2019 的 TECHPULSE 中也有提到這部分，想了解更多可以參考以下簡報：

<script async class="speakerdeck-embed" data-slide="6" data-id="20a06fe07ac74222ac6aa754110b0043" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

2. Face(臉部辨識)

<script async class="speakerdeck-embed" data-slide="25" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

相信在大家於報到時，在報到處櫃檯就已經有體驗到`臉部辨識`的技術，讓有註冊的朋友可以在**非常短**的時間內就能入場，在研討會中有這個功能是不是很讚呢？

![](https://nijialin.com/images/2020/techpulse/face-sign-3.jpg)

3. OCR(Optical Character Recognition)

OCR 能用在什麼地方呢？透過這張簡報應該就有想法了：

<script async class="speakerdeck-embed" data-slide="19" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這次大會中各個攤位都有一個錦旗讓大家上傳體驗 CLOVA OCR 的技術。

![](https://nijialin.com/images/2020/techpulse/lae_ocr.jpg)

## 兩大解決方案

1. eKYC

結合 Face 與 OCR 打造的解決方案，例如：用戶持有健保卡想看診，透過此解決方案可以讓系統自動填入一些基本資訊，減低手動輸入的成本

<script async class="speakerdeck-embed" data-slide="22" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

2. AiCall 可以看以下影片，會讓你更有感喔！

<iframe width="560" height="315" src="https://www.youtube.com/embed/x5gt2sjnfh4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## 使用 CLOVA 技術開發活動頁面分享 - Cid

![](https://nijialin.com/images/2020/techpulse/clova-cid.jpg)

<script async class="speakerdeck-embed" data-slide="28" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

這部分就由 Cid 說明這次 TECHPULSE 2020 的報到流程究竟是怎麼快速實現的。在大會前相信大家都有收到資訊並上傳自己的人臉，Server 這邊則會將資訊轉交給 CLOVA 做訓練，並於大會當天讓大家可以在櫃檯掃描並達到快速入場的效果。

<script async class="speakerdeck-embed" data-slide="33" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

由於 LINE 有許多相關的活動有入場的需求，當我們只要開發一個即可使用到各個場域，降低開發成本同時也提升使用者入場的消化速度。

> 若讀者對於成為「合作夥伴」的話，可以使用[這個表單](https://tw.linebiz.com/contact-us/inquiry-partner)來申請。

<script async class="speakerdeck-embed" data-slide="41" data-id="0280751f2565451c9c8c920208fec132" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

## 小結

![](https://nijialin.com/images/2020/techpulse/photowall.JPG)

其實在現場中的相片牆也有使用到 LINE CLOVA 的辨識技術，更多活動內容可以參考:

- [您不能錯過的 LINE TAIWAN TECHPULSE 2020 年度盛會](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-techpulse-2020/)

# [Platform API Update](https://speakerdeck.com/line_developers_tw/line-techpulse-2020-platform-api-update) - Evan Lin

今年的這部分則使用與以往不同的風格來講解 2020 平台更新的資訊

## Narrowcast

<script async class="speakerdeck-embed" data-slide="5" data-id="73943b1c8b0f4dde9a81fd856cf4ab24" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

> 「我們不是不喜歡廣告…… 我們只是不喜歡與我們無關的廣告。」

許多使用者在使用官方帳號時，經常會忽略用戶的感受，因此可以藉由 Narrowcast 將可以讓你收斂用戶的條件，選出更加適合此封訊息內容的用戶並推送給他，說不定還可以藉此降低官方帳號的封鎖率喔！

> Narrowcast 相關文章請參閱[透過 Narrowcast API 在 LINE Chatbot 上發送 "精準" 且 "討喜" 的訊息](https://engineering.linecorp.com/zh-hant/blog/narrowcast-api-on-line-chatbot/)

## Icon Switch

<script async class="speakerdeck-embed" data-slide="6" data-id="73943b1c8b0f4dde9a81fd856cf4ab24" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

而今年初 LINE 開放了這個強大的 API 給各位開發者，讓大家可以更靈活地使用它來讓你的 Chatbot 更生動！

講者在這部分使用一個例子來說明用途：「經常大家在經營許多店家官方帳號的時候，在一些程式中條件無法正確判斷時，就需要讓客服人員透過官方帳號來回覆使用者的問題，此時使用 Icon Switch 這個 API 即可快速切換身份也同時讓使用者能夠在視窗內快速辨別身份。」

> 「藉由這個 API 也讓使用者可以感覺到 chatbot 不再是個冷冰冰的機器，而是有溫度的互動。」

你可以透過以下範例程式快速實踐 Icon Switch：

- Golang: https://github.com/kkdai/line-bot-icon-switch
- Python: https://github.com/louis70109/line-icon-switch-python
- [使用 Icon Switch 來變更聊天機器人的暱稱與圖示](https://engineering.linecorp.com/zh-hant/blog/chatbot-icon-switch/)

## 其他 Messaging API 更新

- [Emojis](https://developers.line.biz/en/reference/messaging-api/#wh-text): 讓你可以使用 API 的方式使用 LINE 的表情符號
  - [表情符號清單](https://d.line-scdn.net/r/devcenter/sendable_line_emoji_list.pdf)
- 取得使用者語系([get user profile](https://developers.line.biz/en/reference/messaging-api/#get-profile)): 除了讓你能取得使用者的基本資訊以外，今年更增加了語系的欄位，讓你可以依照所屬區域去對應前端語系喔！

> 上述兩項的相關文章介紹:
>
> 1. [LINE 開發社群計畫: 2020/04/21 Chatbots#18 online](https://engineering.linecorp.com/zh-hant/blog/2020-04-21-chatbots18/)
> 2. [關於 LINE Emoji 的一些細節（以 Golang 為例)](https://engineering.linecorp.com/zh-hant/blog/line-emoji-with-golang/)

- Group/Chatroom API

  - [2020 六月 LINE 平台更新整理與 LINE Group/Room Chatbot 的展示](https://engineering.linecorp.com/zh-hant/blog/2020-june-update/)

  | Event        | Group                                                                                     | Chatroom                                                                                 |
  | ------------ | ----------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
  | 取得資訊     | [Link](https://developers.line.biz/en/reference/messaging-api/#get-group-summary)         |                                                                                          |
  | 人數         | [Link](https://developers.line.biz/en/reference/messaging-api/#get-members-group-count)   | [Link](https://developers.line.biz/en/reference/messaging-api/#get-members-room-count)   |
  | 用戶 IDs     | [Link](https://developers.line.biz/en/reference/messaging-api/#get-group-member-user-ids) | [Link](https://developers.line.biz/en/reference/messaging-api/#get-room-member-user-ids) |
  | 取得人員資訊 | [Link](https://developers.line.biz/en/reference/messaging-api/#get-group-member-profile)  | [Link](https://developers.line.biz/en/reference/messaging-api/#get-room-member-profile)  |
  | 離開         | [Link](https://developers.line.biz/en/reference/messaging-api/#leave-group)               | [Link](https://developers.line.biz/en/reference/messaging-api/#leave-room)               |

- [Unsend Event](https://developers.line.biz/en/reference/messaging-api/#message-event): Chatbot 可收到使用者回收訊息的 Event，並作出對應的回饋(但目前僅限於`群組`以及`聊天室`)
- [Video viewing complete](https://developers.line.biz/en/reference/messaging-api/#video-viewing-complete): 感官接受度普遍來說會是 影片 ➡️ 圖片 ➡️ 文字，但使用者看完影片若沒有回饋是否少了點什麼呢？你可以使用這個 API 讓 Chatbot 發送的訊息

- [Share Target Picker 已經公開，透過 LIFF 來分享訊息將更加的便利](https://engineering.linecorp.com/zh-hant/blog/liff-share-target-picker/)
- [Share Target Picker: LIFF（LINE Frontend Framework）中的新功能](https://engineering.linecorp.com/zh-hant/blog/share-target-picker-liff/)
- [開啟 LINE LIFF v2 的無限潛力 — liff.shareTargetPicker](https://engineering.linecorp.com/zh-hant/blog/start-liff-v2-sharetargetpicker-power/)
- [LINE 開發社群計畫: 2020 九月 LINE 平台更新整理與 LIFF ShareTargetPicker 案例分享](https://engineering.linecorp.com/zh-hant/blog/line-api-platform-update-202009/)
- [在 Vue3 中引入 LIFF 的 ShareTargetPicker 分享 FlexMessage 訊息給 LINE 好友](https://engineering.linecorp.com/zh-hant/blog/how-to-use-liff-in-vue3/)
- [梅竹黑客松賽前企業工作坊 – LIFF shareTargetPicker](https://engineering.linecorp.com/zh-hant/blog/meichu-liff-share-target-picker-workshop/)

# MLOps

<script async class="speakerdeck-embed" data-slide="6" data-id="822ff17fcd0b4a468ee1f275711b14f3" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

當一個團隊要擴大時，在職責中也都需要劃分清楚，並會遇到許多挑戰，

# Security

最後一定要提到資訊安全相關的議題，在日常對話中其實 LINE 就透過許多加密手段來確保資料，讓每位使用者在使用 LINE 時可以更安心的使用，

<script async class="speakerdeck-embed" data-slide="34" data-id="e69b000e4fe6410e9d062f1f5584c276" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

而在近日推出的生物辨識登入，目的就是讓使用者可以不透過密碼靠特徵或指紋即可登入，降低輸入被竊取的風險，更詳細內容可以參考這篇：[不怕忘記密碼了～ LINE 開放「生物辨識」登入，iPad 用戶搶先體驗！](http://official-blog.line.me/tw/archives/84191413.html)

# 結論

![](https://nijialin.com/images/2020/techpulse/see-you-next-year.jpg)

# 活動小結

立即加入「LINE 開發者官方社群」官方帳號，就能收到第一手 Meetup 活動，或與開發者計畫有關的最新消息的推播通知。▼

「LINE 開發者官方社群」官方帳號 ID：@line_tw_dev
![](https://www.evanlin.com/images/2020/line-tw-dev-qr.png)

# 關於「LINE 開發社群計畫」

LINE 今年年初在台灣啟動「LINE 開發社群計畫」，將長期投入人力與資源在台灣舉辦對內對外、線上線下的開發者社群聚會、徵才日、開發者大會等，已經舉辦 30 場以上的活動。歡迎讀者們能夠持續回來察看最新的狀況。詳情請看:

- [2019 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019-plan/)
- [LINE Taiwan Developer Relations 2019 回顧與 2019 開發社群計畫報告](https://engineering.linecorp.com/zh-hant/blog/line-taiwan-developer-relations-2019/)
- [2020 年 LINE 開發社群計畫活動時程表](https://engineering.linecorp.com/zh-hant/blog/2020-line-tw-devrel/)
