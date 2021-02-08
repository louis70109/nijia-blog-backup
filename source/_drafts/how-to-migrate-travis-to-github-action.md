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

![](https://nijialin.com/images/2021/action/)

# 前言

<!-- more -->

# 介紹

開個 branch

## 刪除 Travis CI

## 開始測試

一般專案設計都會依照環境去切割相依套件的檔案，例如 (**production** vs **develop**)，(**Production** vs **CI 環境**)，這[此次的範例中](https://github.com/louis70109/GitHub_Action_Python_Example)我建立的 `requirements-ci.txt` 來安裝在 CI 環境中會用到的工具。

## 檢查 tox.ini

這個檔案目的是為了讓你在跑 tox 這個指令時可以參考相關設定檔，讓開發者可以彈性的設定需求。

<script src="https://gist.github.com/louis70109/25c3f2fefc12a277ec97ae6aab25c915.js"></script>

- 第 2 行：在參考其他專案時複製過來，當中是 `py37-flake8-src`，但因為會測試多版本，因此這邊輸入 `py3-flake8-src` 就好。(少個 7)
- 第 11 行：執行環境中會相依套件(如：pytest、pytest-flake8、pytest-pep8、pytest-cov)，雖然在建立時已經有安裝 `requirement-ci.txt`，但這邊還是要修改避免其他人在本地端測試時無法啟動。

## 加入部署 Action

![](https://nijialin.com/images/2021/action/1.png)

進入專案後，點選到上面頁籤中的 `Action`，選取當中的 `Python Package`，

<script src="https://gist.github.com/louis70109/4f06b7fdfb2b4e89557cb04ce0f939c2.js"></script>

猶記得去年剛出時因為資源還不多，但現在有許多貢獻者已經幫我們寫好了許多內容，可以讓我們在當中直接點選引進 專案中，但要在 submit 前要注意當中跑的內容是甚麼才行喔！

## 設定 Secret 至單一專案中

- 先到 [https://pypi.org/](https://pypi.org/)
- 右上角 Your project
- 點選 Account Setting

![](https://nijialin.com/images/2021/action/token1.png)

因為我們還沒將專案上傳至 Pypi，因此在這裡設定權限時會先設定所有專案(Scope)，若在此之後會擔心權限問題，可在上傳完之後再回來更改喔！

![](https://nijialin.com/images/2021/action/token2.png)

最後會給你帳號 `__token__` 與密碼 `pypi-xxxoooo`，並有敘述說你在本地端如何操作，不過這邊因為要放在 GitHub Action 上，因此就不討論這部分。

![](https://nijialin.com/images/2021/action/token3.png)

接著開啟剛剛 Fork 的專案，並於 **Setting** 中設定剛剛建立的帳號密碼，並按第三步的建立，將 **PYPI_USERNAME** 以及 **PYPI_PASSWORD** 填入剛剛設定得對應值。

![](https://nijialin.com/images/2021/action/env1.png)

在 [加入部署 Action]() 環節中的圖片，會有 Publish Python Package 的按鈕，但若你不小心把網頁關掉了也沒關係，以下提供一份 gist，在 `.github/workflows` 裡建立一個 `publish.yml` 並貼上即可。

> 小技巧：用 Mac 開網頁我都會 Command + 左鍵 開新頁面，避免舊的頁面也需要但被刷掉。

<script src="https://gist.github.com/louis70109/a0d4ce1886f975552a096106bbf3c89a.js"></script>

稍微解釋一下這份 yaml 檔在這部分最重要部分

- **6~8 行**: 當在 GitHub 中 Release 新版本建立時(不清楚 Release [可參考](https://docs.github.com/en/github/administering-a-repository/managing-releases-in-a-repository))，自動觸發該腳本跑相對應功能。
- **27, 28 行**: 讀取專案中的環境變數，也就是剛剛在 **Secret** 輸入的 **PYPI_USERNAME** 以及 **PYPI_PASSWORD**，這兩行會自動去抓這兩個參數並放入。
- **30, 31 行**: 讀取專案套件中的 **setup.py**，透過設定值並編譯出一個 `dist/` 的資料夾，透過 twine 把 `dist/` 上傳至 Pypi 上。

## Testing

首先我們先任意改個 README 內容後，直接推送至 GitHub 上，應該會先看到 ✅ 的地方是個黃色圈圈 🟡，此時就是正在跑一開始設定的單元測試，可以點圖示進去看跑的過程。

![](https://nijialin.com/images/2021/action/test1.png)

接著我們點選 `Release` 後，會看到畫面上有 `Draft a new release` 的按鈕：
![](https://nijialin.com/images/2021/action/release0.png)

進入後輸入相關的資訊：

- 版號
- 標題
- 細節描述

![](https://nijialin.com/images/2021/action/release1.png)

輸入完之後點選 **Action**，就會看到相關觸發的流程開始執行了
![](https://nijialin.com/images/2021/action/release2.png)

想看更多執行細節就點入，會看到相關的執行 Action Task， 若有錯誤則在當中查看。(感覺可以在設定讓整個 Task 串在一起)
![](https://nijialin.com/images/2021/action/release3.png)

如上圖完成之後，至 [Pypi](https://pypi.org/) 上查看你的套件，以下圖來說我就釋出了 **0.2.0** 的版本囉！
![](https://nijialin.com/images/2021/action/release4.png)

# 結論
