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

故事是這樣的，前幾天好像有微軟的開發者日(❓)，因此同事在收看完線上影片後分享給我一篇關於在 VSCode 開發 [FastAPI+PostgreSQL 的影片](https://www.youtube.com/watch?v=FvUpjdWnibo)，內容主要在講解如何在 VSCode 中以 Container 模式做開發，詳細內容以下會提到。

而因為過往我因為很懶得處理環境問題，因此都快速安裝 Python 後在使用 PyCharm 來協助處理開發問題，在這次看了影片中的使用覺得整體效果非常讚(香 🥰)，以下就來介紹一下如何使用以及範例吧！

延伸閱讀：

- [如何在 PyCharm 幫 Python 除蟲(Debug)](https://nijialin.com/2021/05/03/how-to-debug-python-by-pycharm-tw/)
<!-- more -->

## TL;DR

- 環境孤立化(在容器中)，不會污染本機環境
- 該有的 VSCode Plugins 都在
- 不用再找 Container IP，直接 127.0.0.1
- Configuration Plugin 都幫你弄好了
- 本地開發+資料庫(介面)都弄好，很夠用(香)
- UI 感覺變直覺了? (以前不太會用 VSCode 寫 Python)

可能會遇到的問題:

- 硬碟空間不足(容器一多可能會炸)
- 有機會需要重開 Container
- 有些功能還是沒 PyCharm 方便(各有好壞)

# 介紹

> 本次範例專案： [fastapi-vscode-example](https://github.com/louis70109/fastapi-vscode-example)

首先在需要在 VSCode 中安裝兩個套件，Python 以及 Remote-Container，以下是 Remote-Container 的套件截圖(大家應該知道安裝哪個 Python?)

![remote container](https://nijialin.com/images/2021/fastapi-container/remote0.png)

接著 Clone 這次的範例專案 [fastapi-vscode-example](https://github.com/louis70109/fastapi-vscode-example)，以下我來跟大家稍微解釋一下資料夾結構：

- `.devcontainer/`: Remote-Container 使用時所需要的資料夾，下面會有三個檔案 Dockerfile、docker-compose.yml、devcontainer.json，前兩個為容器的設定檔，最後一個則是 Remote-Container 所需要的檔案。
- `.vscode/`: 在 VSCode 裡面執行相關操作時幫大家儲存下來的設定檔位置。
- `Container database.session.sql`: 在 VSCode 中透過介面來操作資料庫時會初始化跑的檔案。
- `main.py`: 主程式要跑的檔案。
- 其餘檔案則是專案在寫時所分類的資料夾以及 Heroku 設定檔。

大致了解架構後，接著按下 Command+Shift+p 開啟一個輸入框，並輸入 `remote container` 後找到 `Reopen in Container` 的選項，如下圖所示。

![remote container1](https://nijialin.com/images/2021/fastapi-container/remote1.png)

接著 VSCode 會開始幫忙在 Docker 中產生容器，需要稍等它 pull 以及建立容器，建立完後可以在裡面開啟終端機看一下(pwd)自己是否真的在容器(Container)裡面。
![open folder](https://nijialin.com/images/2021/fastapi-container/open1.png)

進來之後就要來啟動專案，按下畫面上執行的按鈕，而這個按鈕則會在 `.vscode` 中建立 `launch.json` 來幫忙放相關設定檔，裡頭就是設定要跑的相關指令。
![launch](https://nijialin.com/images/2021/fastapi-container/launch1.png)

# 結論
