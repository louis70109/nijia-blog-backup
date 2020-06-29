---
title:
  "[object Object]": null
categories: 學習紀錄
abbrlink: 60549
tags:
---

![](https://i.imgur.com/0QAGPDc.png)

# 前言

當前專案規模若是不大時，其實不管怎麼`上版`、`關閉`、`重開服務`其實對於客戶來說影響並不大，但隨著服務日漸壯大後，想輕易關閉或重啟服務時若沒做好相對應措施可能會導致災情四起，例如 Redis 被清空、 DB transaction 到一半被關掉導致毀損...諸如此類的問題，因此 Graceful Shutdown 這機制就日漸被重視，主要是在當服務在接收關閉訊號之前，先`處理完`或`備份`資料後才讓服務關閉，如此一來就可以最大幅度的降低問題的產生，讓服務能夠可平滑的關閉、重啟。

概念上就會像 Rails 上的 `before_action` 一樣，在任何事件觸發前做些什麼事，猶如這邊文章提到的在斷開服務前要做些什麼事這樣，接著以下就使用 python 來做範例囉！

<!-- more -->

# 使用 atexit 來做 graceful shutdown

## 介紹

atexit 有記載在[官方文件](https://docs.python.org/3/library/atexit.html)中，在 stackoverflow 中[也有提及](https://stackoverflow.com/a/30739397)，文件中說明這個模組(Module)可以去定義 `函式們`(functions) 去`註冊`或`反註冊`清除函式，並且它的優先權會在程序終止之上。開發者需預先在程式中註冊中事件(Event)，若同時註冊多個事件時，順序則是反向執行，舉例來說，當前註冊 A、B、C 三個事件，當程序意外終止時，執行的順序則會是 C、B、A，推測會反執行的原因是模組將註冊事件放進一個暫時 堆疊(stack) 中，當觸發後就會照著堆疊的方式去執行，若還是不懂[可參考](https://zh.wikipedia.org/zh-tw/%E5%A0%86%E6%A0%88)。

官方中有記載：

> Note: The functions registered via this module are not called when the program is killed by a signal not handled by Python, when a Python fatal internal error is detected, or when os.\_exit() is called.

當遇到以下事件時無法觸發:

- 被外部清除程序，而 python 無法 handle
- Python 內部錯誤
- 執行到 `os_exit()`

不過除了第二項以外目前都會觸發 flask 中註冊的 atexit，以下就介紹一下如何在 flask 上使用並實測。

## 實測

建立一個 `app.py` 然後貼下以下程式碼:

```python
import os
from time import sleep
from flask imporㄓt Flask
import atexit

app = Flask(__name__)


@atexit.register
def shutdown():
    print('----------------------------------')
    print("Ready to close...")
    sleep(1)
    print("You can doing some action in here.")
    print('----------------------------------')


@app.route('/')
def hello():
    return 'Hi'


@app.route('/user/<username>')
def user(username):
    if username == 'Tom':
        return f'Hello {username}'
    else:
        print('I will use OS EXIT!! Hahahaha')
        os._exit(0)


if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000, debug=True)
```

以下就帶幾個範例並且實測無法觸發的事件。

### 範例一 - 外部清除

這裡使用 `ps aux | grep python` 以及 `kill -9 PID` 來實測。

首先執行程式 `python app.py`:
![](https://i.imgur.com/o1bryC2.png)

---

接著使用 `ps aux | grep python` 找出我們的程序，以下圖例子而言，`第一段`與`第三段`是我們執行 app.py 這個檔案相關的程序，在 nijia 這個使用者後面接的數字就是 PID(13642 & 13641)：
![](https://i.imgur.com/OEcY3Kf.png)

---

#### 刪除不同的 PID 會有不同的結果 

##### 刪除第一個 PID - 13642

使用 `kill -9 13642` 時刪除它會觸發 atexit:
![](https://i.imgur.com/aLTyhC8.png)

具體原因是因為刪除的事 `app.py` 本身而不是對於 `python app.py` 這整件事，也由於不是針對 python 本身處理，因此會觸發 graceful shutdown 也是合情合理。

##### 刪除第二個 PID - 13641

> 若是照步驟來這部分可能已經沒有 PID，需要再重新執行一次程式。

一樣使用 `kill -9 13641` 會得到如下圖所示:
![](https://i.imgur.com/wDDKCE1.png)

在這個實測中他不會觸發 graceful shutdown，因為它刪除了 `python app.py` 的執行程序，也因為連同 python 的處理程序也一併刪除讓 python 無法觸發事件導致沒有 graceful shutdown。

在這個例子中就體驗到官方文件說的：「when the program is killed by a signal not handled by Python,」

### 範例二 - 使用 os.\_exit(0)

在一開始的程式碼中我已加入 `@app.route('/user/<username>')` 這個路由，若帶入 username 不等於 Tom 實則會使用 `ox._exit(0)`。

這裡一樣先執行 `python app.py`，這邊可以使用 Postman、curl 都行，而我是使用 Python Command 搭配 requests 來測試，在呼叫 `http://localhost:5000/user/Amy` 後會收到出錯訊息：
![](https://i.imgur.com/u5y3wRh.png)

這裡一樣有觸發到 graceful shutdown，推測在範例中應該是被 flask 攔截下來才導致有觸發到。

### Event 3 - Reverse

在 `def shutdown()` 下面直接加上以下的 code:

```python
@atexit.register
def shutdown2():
    print('--------------Second start-------------')
    sleep(1)
    print('--------------Second end---------------')


@atexit.register
def shutdown3():
    print('-----------Third Start-----------------')
    sleep(1)
    print('-----------Third end-------------------')
```

直接多註冊兩個 atexit 的函式，接著一樣執行 `python app.py` 後可以透過 python command 下一個錯誤 username 的路由觸發 graceful shutdown：

```
r = requests.get('http://localhost:5000/user/amy')
```

實測結果 atexit 果真是會倒轉著執行 function，如堆疊(stack)般的一個一個拿出：
![](https://i.imgur.com/tRLTzCt.png)

# 結論

使用 atexit 可以在 python 中簡單的實現 Graceful Shutdown，需要注意的是若在 atexit 中一樣需要 try catch 去`抓取錯誤`以及設定`時間長度`(太久了一樣要關閉)，畢竟需要透過這個機制去降低`重開`/`關閉成本`，希望能藉由這個機制讓各位的服務們可以安全下莊重新上功能 🙂。

# 參考

- [[Go 教學] 什麼是 graceful shutdown?](https://blog.wu-boy.com/2020/02/what-is-graceful-shutdown-in-golang/)
- [Graceful Shutdown：盡 Server 最後的義務 — 以 Node.js 與 Kubernetes 為例](https://medium.com/@chentsulin/graceful-shutdown-%E7%9B%A1-server-%E6%9C%80%E5%BE%8C%E7%9A%84%E7%BE%A9%E5%8B%99-%E4%BB%A5-node-js-%E8%88%87-kubernetes-%E7%82%BA%E4%BE%8B-cb7f519389ea)
- [Python Flask shutdown event handler](https://stackoverflow.com/questions/30739244/python-flask-shutdown-event-handler)
