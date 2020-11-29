---
title: How to delivery your Youtube streaming on Mac by SoundFlower
categories: 學習紀錄
abbrlink: 2051073782
tags:
---

若你跟我一樣手上只有一台 mac 加一台手機但又有直播需求的朋友，你很適合看這篇
本篇將已 MAC OS 為例
由於 MAC 沒有額外的音效卡可以輸出，因此需要用軟體來解決
![](https://nijialin.com/images/2020/OBS/os-version.png)

# 前言

<!-- more -->

Open Broadcaster Software(OBS): https://obsproject.com/download

系統偏好 -> 聲音
選擇聲音輸出 -> x64
OBS ->

## [SoundFlower](https://github.com/mattingalls/Soundflower/releases)

連結: https://github.com/mattingalls/Soundflower/releases

> 雖然最後一版 release 是 2014 年 12 月底，但截至目前為止都還能用，若有任何不同的解法歡迎 mail 我！

再 release 說明中有提到第一次安裝因為有權限問題而導致失敗，一樣到`系統偏好設定` -> 安全性與隱私 -> 允許安裝

通過隱私權後接著再安裝一次就可以看到安裝成功的畫面

## 多重輸出裝置

會需要這個部分是因為不希望當聲音只能輸出卻不能同步監聽，因此需要 Mac 的內建軟體幫忙脫重輸出。

> 首先先進 `啟動台` -> 點選`其他` -> 選擇 `音訊 MIDI 設定`

![](https://nijialin.com/images/2020/OBS/media-midi.png)
點選左下角的 `＋`，選擇 `製作多重輸出裝置`
![](https://nijialin.com/images/2020/OBS/add-milti-output.png)
出來之後將主裝置設定成`揚聲器`(或你的耳機)，並同步勾選 SoundFlower64，如此一來就可以做到同時輸出兩邊聲音的方法了。
![](https://nijialin.com/images/2020/OBS/multi-output.png)
最後點選聲音選項，將輸出聲音選擇`多重輸出裝置`的選項。
![](https://nijialin.com/images/2020/OBS/select-output.png)

> 重要：藍芽耳機(Airpods)目前測試起來是不行的！

# 輸入裝置

![](https://nijialin.com/images/2020/OBS/input.png.png)
一般來說若是要擷取的話輸入輸出皆會選擇 `SoundFlower64`，而因為有稍後介紹的 OBS 幫忙，因此這邊輸入裝置選擇`內建麥克風`來收自己講話的聲音即可。

# OBS 輸出設定

![](https://nijialin.com/images/2020/OBS/obs-media-config.png)

從 OBS 的主界面右下角點選 `設定` 進入後，左側欄選擇 `音效`，接著按造以下項目實作：

- 桌面音效選擇： SoundFlower64
- 麥克風/輔助音: SoundFlower64
- 麥克風/輔助音 2: Macbook Pro 內建麥克風 <mark>(重要！否則在直播時你只能聽人家講話！)</mark>

為何會有上述這樣的設定呢？`桌面音效`與第一個`輔助音`一定都是選擇 SoundFlower64，讓軟體幫你把音效收音轉打出去(因為 Mac 只有一個介面卡)，而 OBS 的好處就是它可以整合兩個麥克風收到的音訊一起打出去(最多`4`隻)，由於第一個麥克風已經去收電腦的聲音了，接著就是用`輔助音2`來收你講話的聲音，如此一來就可以邊直播邊聽邊說話啦，不用再用其他設備(手機、iPad)在旁邊監聽了。

## 告訴 OBS 要擷取誰輸出

雖然上述已經告訴 OBS 有哪些設備，但 OBS 還是不知道輸出誰好，因此就要按造以下步驟告訴他。

- 點選右下角的`＋`

![](https://nijialin.com/images/2020/OBS/obs-select.png)

- 選擇`擷取音效輸出`，下拉式選單選擇 `SoundFlower(64ch)`

![](https://nijialin.com/images/2020/OBS/obs-select-output.png)

# 如何看結果有沒有成功？

![](https://nijialin.com/images/2020/OBS/obs-output.png)
可以先隨意播放音樂測試，基本上看到上圖的音軌有正在動就代表成功了，以下就使用 Youtube 來進行直播測試。

![](https://nijialin.com/images/2020/OBS/yt-stream.png)
進入 Youtube 之後點選右上角`進行直播`，當進入後通常都需要等一段時間。

![](https://nijialin.com/images/2020/OBS/yt-monitor.png)
看到此畫面之後將金鑰複製起來，右上角的分享按鈕可以複製網址，原則上我都會先複製起來丟在 LINE 的任意視窗中，方便使用手機測試直播狀態。

![](https://nijialin.com/images/2020/OBS/obs-yt-key-set.png)
將 Youtube 的金鑰複製到這邊，即可讓 OBS 與 Youtube 串接，按下確定後就可以按 `開始串流` 測試直播啦！(建議先用`不公開`測試)

最後就是調整看希望收哪邊的音要多一點，看是桌面來的聲音(第三方通訊軟體)或是自己的外接的麥克風，就調整`輔助音1`或是`輔助音2`來控制大小聲。

# 介紹

# 結論
