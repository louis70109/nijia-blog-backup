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

<!-- more -->

# 介紹

# Clone 特定資料夾

許多 Open Source 專案當中都會放 examples 相關範例的資料夾，但是整包 Clone 下來又太大包

參考這個 [stackoverflow 這個解答](https://stackoverflow.com/questions/651038/how-do-you-clone-a-git-repository-into-a-specific-folder)

```
git clone git@github.com:whatever.git folder-name
```

以 [kustomize](https://github.com/kubernetes-sigs/kustomize) 這個專案為範例，專案 git 有兩個：

- HTTPS 版本： `https://github.com/kubernetes-sigs/kustomize.git`
- SSH 版本： `git@github.com:kubernetes-sigs/kustomize.git`

擇一使用就好，若你的 git 有使用 ssh 相關的操作則下方指令建議使用第二個。

```
git clone https://github.com/kubernetes-sigs/kustomize.git examples
```
