---
title: 如何在 PyCharm 幫 Python 除蟲(Debug)
tags:
  - Python
  - Pycharm
categories: Python
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

從我開始工作時，因為**動態語言**方便且快速上手，因此我就選擇動態語言作為我吃飯的工具。隨著時間的推進我寫過了 Python、Ruby、JavaScript，由於大多都使用 Vscode 撰寫程式，對於環境設定不是很熟捻的我設定相關東西就很困擾，因此大多數都是用 `print`(Python)、`console.log`(JS) 或是 `puts`(Ruby) 直接印在終端機上來除錯腳本或是網站。

在過去這些日子中最有印象的就是使用 Ruby 的 `byebug` 套件來幫我除蟲，它是個可以在終端機透過快捷鍵讓你取得想除錯的地方開始進行除錯，對於當時的我來說簡直是福音，也讓我在那段日子中非常的快樂ＸＤ

<!-- more -->

由於現在轉戰 Python 
In this article, I will take you to know how to debug Python apps by Pycharm which was I learn recently...😆

1. Open your project and click the dropdown button

![](https://nijialin.com/images/2021/debug-python/0.png)

2. Select `Edit Configurations`.

![](https://nijialin.com/images/2021/debug-python/1.png)

3. Click `＋` ➡️ Select `Python` ➡️ Choose your `script` or `web entrance file` ➡️ Set `Environment Variables` if your app needs ➡️ `Apply` and `OK`.
![](https://nijialin.com/images/2021/debug-python/2.png)

4. Click `+` adding a variable, fill the variable key and value column.

![](https://nijialin.com/images/2021/debug-python/4.png)

5. The name would map your task name.

![](https://nijialin.com/images/2021/debug-python/3.png)

6. Finally, you will get a task which like following name `api debug`(It's my task name).

![](https://nijialin.com/images/2021/debug-python/6.png)

7. Put red icon in a line(or two red icon become a scope), Click the `bug button` to start the debug mode🎉

![](https://nijialin.com/images/2021/debug-python/5.png)

8. Then you can see code information(variables, library...) at IDE. 

> If you run web app, you need to give API a action, then debug mode will be trigger.

# Conclusion

This is my first time using debug mode in dynamic languages by Python. Write down my experience when I forgot steps on another day... XD