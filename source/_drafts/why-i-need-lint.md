---
title: 【Lint】寫程式為什麼要 Lint
categories: 學習紀錄
tags:
---

![](https://i.imgur.com/0QAGPDc.png)

# 前言

從前我在改以前寫程式時都會有幾個問題，『排版好亂』、『這變數(a1)是？』諸如此類的問題，但就在加入社群後認識很多圈內的朋友並與之討論後才體悟到 Lint 的重要性，首先在跟人家解釋程式時從`變數`、`函式`名稱時就能讓對方更快速知道用途，不用解釋 a1 a2 個別代表什麼，大大的降低溝通成本，但一個工具總會有優缺點

<!-- more -->

## 優點

- 開發風格統一
- 不會有 tab、space 的問題
- 後續接手的人心力可以放更多在商業邏輯上
- 培養命名習慣，更謹慎地處理

## 缺點

- 容易打擊剛加入開發領域的朋友
  - Ａ：明明邏輯是對的但怎麼紅字一堆？
- 設定太嚴謹時會為了修問題延誤邏輯開發時間
  - 時程很趕但 CI 一直擋住

# 介紹

## SonarQube

SonarQube 是我在之前的公司時所使用的 Lint，裡面的功能真的很完整，除了一些基本檢查以外，最有印象的就是它會找出`淺在風險`、`Code 品質`、`花多久時間可以看懂`...很多很特別的部分，也許這些功能可能只是參考，但看著數字很淒慘時工程魂就會上身，想要把它數值降低點別出現這麼可怕的數字 😅。
![](https://i.imgur.com/PDyOvLF.png)

> Azure + Sonar 參考[董老師的影片](https://www.facebook.com/DotNetWalker/posts/3277105698995647?__xts__[0]=68.ARBkAILNJPiUfPxM6Prkqnc5a38h0vuBEmxvcb8WQRW1xbbJnMhddEwi7Lj2OudXHSJ2hrZ4jGtMMKEYzbF7GcdcZ0CoglZWSiexYSjlseEXBnReh6OoE5ZGIhlGTh75wVn5mHQ2B-bkTfatl-vIP-k83-G6yeoXm0ZcboLrq_e0gZqQLLTY0FPsbB_ROKWvYuYBbxY5-Vj2kpvVBU528mFDTCKDGTk5ih16hbuzlrxY0boNZUVuIcaT4zdnHBaAUFTminhF03jkys7pSpDeiBVz_A6z3jjPJChlAI9pZzZTrlmupgRR6yDzzQrjZ2CR6R2kWOZi5Liz7RfO9GkxZz4G6g&__tn__=-R)

值得花錢買的 Lint，而 SonarQube 應該是我目前遇到數一數二真的是在鞭打我 code 的一個凶狠 Lint 工具...

## ESLint

當初我初學 Vue 時，在初始化專案時覺得是工程師就是要 Lint，就直接選 ESLint，且當時對於 config 設定檔一竅不通，因此除了執行時滿滿的錯字以外，也讓我對於寫 code quality 的成就感大大折損，對於 coding 年紀還年輕的朋友可以先養成對於 coding 有興趣後再來使用 Lint 我認為對於整個發展會比較健全(但還是看人)。

接著過了一陣子後，我開始修改一個 side project - [Twitch-Bot](https://github.com/louis70109/Twitch-Bot)，這時期因參加社群一陣子也得知 Bottender 這個使用 Javascript 開發 Chatbot 框架，就依照 [Bottender 的初始化](https://bottender.js.org/docs/en/getting-started)方式加上 ESLint，並且搭配 TypeScript 動態檢查所有 code。

在一開始因為還不熟悉 Javascript 相關開發風格，而我使用很多 pythonic 的方式撰寫 Bot，導致整個專案被狠狠教訓了一遍，但帶來的好處是透過 Lint 校正後讓我再隔一段時間回來時修改 issue 時不會因為 coding style 不統一而引發的問題，只要遵守 Lint 的規則整份 code 沒有被標記起來就覺得神清氣爽 😆。

以下節錄我的 VSCode ESLint 相關設定：

```javascript
{
  // 儲存時 format
  "editor.formatOnSave": true,

  // 單引號設定
  "javascript.preferences.quoteStyle": "single",
  "typescript.preferences.quoteStyle": "single",

  // ESLint 設定
  "eslint.autoFixOnSave": true,
  "eslint.enable": true,
  "eslint.validate": ["javascript", "typescript"],
  "eslint.format.enable": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

> [參考我的 Gist](https://gist.github.com/louis70109/8ea88b9b26570d521c81922572f8309d)

### Bonus - VSCode settings

開啟編輯器後的左上角按下`喜好設定`，英文則是 `Performance`
![](https://i.imgur.com/01XOZHL.png)

接著右上角有個`轉換檔案的圖案`按下去就可以看到 setting.json 囉！
![](https://i.imgur.com/ut4sH60.png)

## Flake8

以我前一陣子的寫的 [Lotify](https://github.com/louis70109/lotify#contributing) 來說，在每次的上版前都一定要跑 flake8 檢查：

```python
python -m pytest --flake8 tests/
```

透過 flak8 的檢查讓我在 CI 環境時就可以檢查出錯誤，規範貢獻者們的開發風格(包含自己)，如此一來再之後回來看 Lotify 時就不會措手不及了 😆。

# 結論

Lint 是集結各方工程師們的血汗結晶所產生的規則，在這開源的時代跟著大家的規則走能減少溝通成本，讓心思可以在(商業、工程)邏輯上。另一部分我則認為是對我的要求，透過固定的格式再過了 `N 週/月` 後會來看 code 時不會因為一直在轉變的 coding style 而導致連自己都看不懂的程式碼窘境，因此適當地遵循也是會對以後開發更有幫助喔！

> 我認為適當的遵循是好的，但別一昧的堅持才能開發出好的程式碼。
