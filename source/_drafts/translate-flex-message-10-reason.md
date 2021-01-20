---
title: '使用 2020 Flex Message 的 10 個新功能 - 讓你在 LINE 中設計的更自由'
categories: 翻譯
tags: ['LINE', 'Flex Message']
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

![](https://nijialin.com/images/2021/translate/flex2/1.png)

> [原文](https://medium.com/linedevth/10-%E0%B8%9F%E0%B8%B5%E0%B9%80%E0%B8%88%E0%B8%AD%E0%B8%A3%E0%B9%8C%E0%B9%83%E0%B8%AB%E0%B8%A1%E0%B9%88%E0%B9%83%E0%B8%99-flex-message-%E0%B8%9B%E0%B8%B5-2020-%E0%B8%AD%E0%B8%B4%E0%B8%AA%E0%B8%A3%E0%B8%B0%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B9%80%E0%B8%AB%E0%B8%99%E0%B8%B7%E0%B8%AD%E0%B8%81%E0%B8%A7%E0%B9%88%E0%B8%B2%E0%B8%82%E0%B8%AD%E0%B8%87%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%AD%E0%B8%AD%E0%B8%81%E0%B9%81%E0%B8%9A%E0%B8%9A%E0%B8%82%E0%B9%89%E0%B8%AD%E0%B8%84%E0%B8%A7%E0%B8%B2%E0%B8%A1%E0%B9%83%E0%B8%99-line-47d9ba2cf9ed)

經常許多開發人員會在 LINE 中設計 Flex Message，讓不同設備的使用者可以收到美美的訊息。在 2020 年也就是去年，Flex Message 開發團隊聽到各位開發者的聲音了，發布了比以往更輕鬆並能將您的想像力轉換成 LINE 樣式的版本。

若您對於 Flex Message 不熟悉，建議先了解[這篇文章](https://medium.com/linedevth/%E0%B8%89%E0%B8%B5%E0%B8%81%E0%B8%81%E0%B8%8E%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%AA%E0%B8%94%E0%B8%87%E0%B8%9C%E0%B8%A5%E0%B8%82%E0%B9%89%E0%B8%AD%E0%B8%84%E0%B8%A7%E0%B8%B2%E0%B8%A1%E0%B9%81%E0%B8%9A%E0%B8%9A%E0%B9%80%E0%B8%94%E0%B8%B4%E0%B8%A1%E0%B9%86%E0%B9%83%E0%B8%99-line-messaging-api-%E0%B8%94%E0%B9%89%E0%B8%A7%E0%B8%A2-flex-message-4ad4370562f)。

- [使用 Flex Message 打破 LINE Messaging API 中的傳統顯示規則](https://medium.com/linedevth/%E0%B8%89%E0%B8%B5%E0%B8%81%E0%B8%81%E0%B8%8E%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%81%E0%B8%AA%E0%B8%94%E0%B8%87%E0%B8%9C%E0%B8%A5%E0%B8%82%E0%B9%89%E0%B8%AD%E0%B8%84%E0%B8%A7%E0%B8%B2%E0%B8%A1%E0%B9%81%E0%B8%9A%E0%B8%9A%E0%B9%80%E0%B8%94%E0%B8%B4%E0%B8%A1%E0%B9%86%E0%B9%83%E0%B8%99-line-messaging-api-%E0%B8%94%E0%B9%89%E0%B8%A7%E0%B8%A2-flex-message-4ad4370562f)
<!-- more -->

這次有 10 個新功能，將有助於了解 2020 年 Flex Message 中訊息設計的延展性。

1. APNG Support
2. 內容排版
3. 字體大小和圖示大小（以 px 為單位）
4. Shrink-to-Fit
5. 漸層背景(Gradient Background)
6. 使用 px 來設定 Margin & Spacing
7. 圖片大小（以 px 和 ％ 為單位）
8. 內容可為空的 Box(Empty Box)
9. 增加了單一 Bubble 的 JSON Max size
10. 增加了 Carousel 的 Bubble 數量

您只需查看每個功能的名稱即可。我將會在你的查詢過程中告訴您～

# 1. APNG Support

當今天有任何開發者想在 Flex Message 中使用動畫(APNG)，只需在 "圖片" 的 Component 中加入名為 animation 的屬性即可。

- animated: `true`, `false`(default)

```json
{
  "type": "image",
  "url": "https://apng.onevcat.com/assets/elephant.png",
  "animated": true
}
```

![](https://nijialin.com/images/2021/translate/flex2/2.gif)

## 注意

- 需注意用戶是否有在 "設定 > 照片．影片" 中開啟 **" Auto-play GIFs"** 選項，否則 Animation 將會不能執行。
- 當前使用的圖片 URL 若大於 300KB，則動畫將無法使用，並且只會呈現第一張圖片。
- 每個訊息最多可以指定 **3 個動畫圖片** Component，超過則無法發送訊息。

# 2. 內容排版

當我們要對 Box 中的內容進行排序時，經常使用 flex、width 和 height 之類的屬性來劃分寬度（horizontal）和高度（vertical）的比例，藉此分配間距和邊距。 Box 裡的內容之間都會需要一定距離，讓整體內容看起來更舒適。
此時 Flex Message 團隊準備了 2 個新屬性，您只要在 Box 中使用它們，將能讓您的內容安排更加容易。

## 2.1 [justifyContent](https://developers.line.biz/en/docs/messaging-api/flex-message-layout/#justify-content)

該屬性讓我們能在父階層中設置幫助安排內容，且以下每個值具有不同功能屬性：

- `flex-start`：這將從起點開始對所有項目進行排序。如果是水平，則將基於 bubble 給出的方向：ltr(從左至右)或 rtl(從右至左)；反之若是垂直，則所有項目將從上至下進行排序。
- `center`：將所有項目排列在中心點
- `flex-end`：這將從終點開始對所有項目進行排序。如果是水平，則將基於 bubble 給出的方向：ltr(從左至右)或 rtl(從右至左)；反之若是垂直，則所有項目將從下至上進行排序。
- `space-between`：第一個與最後一個項目貼齊左右側的佈局，其餘項目平均分配到顯示畫面的中心。
- `space-around`：將每個項目之間的距離均勻地分配。
- `space-evenly`：平均劃分每個項目與訊息佈局的距離來進行排序

```json
{
  "type": "box",
  "layout": "horizontal",
  "justifyContent": "flex-start",
  "contents": [{}, {}, {}]
}
```

![](https://nijialin.com/images/2021/translate/flex2/3.png)

```json
{
  "type": "box",
  "layout": "vertical",
  "justifyContent": "flex-start",
  "height": "200px",
  "contents": [{}, {}, {}]
}
```

![](https://nijialin.com/images/2021/translate/flex2/4.png)

## 2.2 [alignItems](https://developers.line.biz/en/docs/messaging-api/flex-message-layout/#align-items)

該屬性能讓我們指定父階層中的項目更換排序方向，而每個值具有以下屬性功能：

- `flex-start`：如果父階層水平排列，則所有項目將自上而下；如果父母垂直排列，則所有項目將從一開始（取決於氣泡中的哪個方向）到 ltr 或 rtl）
- `center`：將所有項目排列在水平和垂直方向的中心
- `flex-end`：如果將父級水平放置，則所有項目將從下至上，並且如果將父級垂直排列，則所有項目將從末尾排列（取決於氣泡在哪個方向 ltr 或 rtl）

```json
{
  "type": "box",
  "layout": "horizontal",
  "alignItems": "flex-start",
  "height": "200px",
  "contents": [{}, {}, {}]
}
```

![](https://nijialin.com/images/2021/translate/flex2/5.png)

```json
{
  "type": "box",
  "layout": "vertical",
  "alignItems": "flex-start",
  "height": "200px",
  "contents": [{}, {}, {}]
}
```

![](https://nijialin.com/images/2021/translate/flex2/6.png)

# 3. 字體大小和圖示大小（以 px 為單位）

要通過指定屬性決定了字體的大小尺寸中的[文字](https://developers.line.biz/en/docs/messaging-api/flex-message-elements/#text) 部分，，[跨度組件](https://developers.line.biz/en/docs/messaging-api/flex-message-elements/#component)和[圖標](https://developers.line.biz/en/docs/messaging-api/flex-message-elements/#component)你的組件將通過預先定義的關鍵字來確定（xxs(11px)，xs(13px)，sm(14px)，md(16px)，lg(19px)，xl(22px)，xxl(29px)，3xl(35px)，4xl(48px)，5xl(74px)），以及這些組件的大小。像我以前那樣，只是一個夢想

但是現在每個人的夢想都實現了。因為所有給定的組件大小現在都可以以像素為單位設置。

- size: keywords, px

```json
{
  "type": "text",
  "text": "...",
  "contents": [
    {
      "type": "span",
      "text": "LINE",
      "size": "32px",
      "weight": "bold",
      "color": "#00ff00"
    },
    {
      "type": "span",
      "text": " Developers",
      "size": "24px"
    }
  ]
}
```

![](https://nijialin.com/images/2021/translate/flex2/7.png)

---

# 4. Shrink-to-Fit

如果文本的長度大於組件的寬度，則會發生這種情況。多餘的文本將被隱藏並顯示為...（點，點）。

以前，完全呈現長文本的方式是將名為 **wrap** 的屬性設置為 true，但這可能會使佈局變形，因為 Text 或 Button 組件的高度可能會受到影響。展開以顯示文本。

因此，Flex Message 2020 提供了 **adjustMode** 屬性，該屬性會自動減小字體大小以適合組件的寬度，從而使佈局保持與設計相同。

- **AdjustMode**：shrink-to-fit

```json
{
  "type": "button",
  "action": {
    "type": "uri",
    "label": "Buy a coffee to your friends anywhere",
    "uri": "http://line.me"
  },
  "style": "primary",
  "adjustMode": "shrink-to-fit"
}
```

![](https://nijialin.com/images/2021/translate/flex2/8.png)

## 注意

AdjustMode 可以在 LINE v10.13.0 應用程序之後顯示。

# 5. 漸層背景(Gradient Background)

去年 我們可以使用名為 **backgroundColor** 的屬性更改 Box 的背景顏色。具有支持 alpha（rgba）的十六進制顏色代碼。
今年，Flex Message 團隊使我們能夠設置漸變背景顏色，並具有一個稱為 **background** 的附加屬性。它包含以下子屬性：

- type：linearGradient（Required）
- angle：0deg — 360deg 漸變開始的度數。可以定義為十進制，例如 88.8deg（Required）
- startColor：任意十六進制顏色或八進制十六進制顏色代碼（Required）。
- endColor：十六進制顏色或八進制十六進制顏色代碼（Required）。
- centerColor：中心的顏色代碼，用於 6 或 8 個十六進製字符。
- CenterPosition：0 — 100%啟動的級配的位置 **centerColor** 在框中，這可以被定義為的地方，如 88.8％。

```json
{
  "type": "box",
  "layout": "vertical",
  "contents": [],
  "background": {
    "type": "linearGradient",
    "angle": "0deg",
    "startColor": "#ff4d79",
    "centerColor": "#ff0000",
    "endColor": "#ffdb2c",
    "centerPosition": "50%"
  },
  "height": "200px"
}
```

![](https://nijialin.com/images/2021/translate/flex2/9.png)

# 6. 使用 px 來設定 Margin & Spacing

先前定義的間隙間距和餘量通過在 Flex 消息的整個屬性將通過定義的關鍵字來確定，預先（none，xs，sm，md，lg，xl，xxl）而已。
但是為了提高消息設計的分辨率和準確性，今年 Flex Message 團隊現在已經能夠識別像素間隙。

- margin: keywords, px

```json
{
  "type": "text",
  "text": "Hello World!",
  "margin": "16px"
}
```

- spacing: keywords, px

```json
{
  "type": "box",
  "layout": "horizontal",
  "spacing": "16px",
  "contents": [
    {
      "type": "text",
      "text": "grape"
    },
    {
      "type": "separator"
    },
    {
      "type": "text",
      "text": "lemon"
    }
  ]
}
```

![](https://nijialin.com/images/2021/translate/flex2/10.png)

## 注意

從現在開始，Box 中每個由邊距指定的組件都可以用於間距。（以前這不會影響 Box 中第一個列出的組件）

# 7. 圖片大小（以 px 和 ％ 為單位）

以前設置圖像的大小。我們可以定義一個命名的屬性大小定義的關鍵字的，預（xxs，xs，sm，md，lg，xl，xxl，3xl，4xl，5xl，full），其中考慮到現實。這種大小確定仍然不是很獨立。
但是從現在開始，現在可以設置大小的的圖像分量中的像素和百分比單位，設定大小將決定的圖像的寬度（寬度）和高度將被自動計算。

- size: keywords, px, %

```json
{
  "type": "image",
  "url": "https://apng.onevcat.com/assets/elephant.png",
  "size": "80%"
}
```

![](https://nijialin.com/images/2021/translate/flex2/11.png)

# 8. 內容可為空的 Box(Empty Box)

Box 是提供 Flex Message 佈局的組件，類似於 Web 開發中的嵌套 <div> 層。

當我們設置它 我們還需要用內容名稱定義一個對象，其中包含一個項目數組，但是如果我們由於忘記在內容中指定該項目而偶然創建了一個 Box，即使只是一個盒子，我們也將無法發送消息。

```json
{
  "type": "box",
  "layout": "vertical",
  "contents": []
}
```

但是為了獲得更大的靈活性，這個 2020 Flex Message 團隊可以讓您發送消息。即使未在內容中指定項目

# 9. 增加了單一 Bubble 的 JSON Max size

曾經我認為 size 應該很夠用，但因為遇到了一些社群上的開發者將 Flex Message 作為單一 Bubble 創建，如此一來訊息的 JSON 的大小就會超過 10KB 的限制。

但是從現在開始，您將能夠在訊息中使用 3 倍的訊息量，因為單個 Bubble 的 Flex Message 中 JSON 的大小已經擴展到 30KB 囉！

# 10. 增加了 Carousel 的 Bubble 數量

很多人都知道，在 LINE 中以 Template Message 或 Flex Message 的形式創建 "Carousel Message" 時，每個訊息最多只能包含 10 個 Bubble。

而在讀過本篇的您將會很幸運，因為我會跟您說，一個 Flex Message 讓您的每條訊息**最多擁有 12 個 Bubble**。

# 結論

話雖如此，2020 年出現的所有功能都是由於 Flex Message 團隊已經聽取了開發人員的聲音並實際上改善了服務的事實。我要感謝泰國開發人員和 LINE API 專家組幫助我們提供反饋和請求新功能。最後，我想用一個漂亮的句子結尾這篇文章...

> A Technology without a Community has no Meaning.
