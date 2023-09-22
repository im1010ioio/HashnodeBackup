---
title: "#06補充 網頁的根、絕對路徑、相對路徑，那些關於路徑的小知識"
datePublished: Fri Sep 22 2023 05:21:25 GMT+0000 (Coordinated Universal Time)
cuid: clmu5me18000b08me3mya23lf
slug: html-file-paths
tags: html, html5

---

HTML 的屬性 `href`、`src` 都需要指定檔案路徑才能載入進來，
所以這邊補充個關於路徑的小知識。

----

#### 何謂網頁的根（root）？

指的是網域底下第一層的檔案，例如：`https://test.com/favicon.ico` ，`https://test.com/` 就是網頁的根，`favicon.ico` 就是一個放在根底下的檔案。

而路徑分為兩種：

#### 絕對路徑

無論檔案位於這個網頁的何處，這個路徑都不會改變，這就叫做絕對路徑。

* 常見的網址，如 `href="https://test.com/index.css"` 是絕對路徑；
    
* `href="/css/index.css"` ，當連結由斜線開頭，路徑是由從網頁的根開始找尋，所以也是屬於絕對路徑。
    

#### 相對路徑

路徑是由檔案自身相對位置開始找尋，自己的位置改變了，找到的結果也會不同，這就是相對路徑。

* `href="index.css"` 如果連結前面什麼都沒寫，找到的是與自己同層的檔案；
    
* `href="./index.css"` 如果連結前面寫了一個點 `./`，找到的也是與自己同層的檔案；
    
* `href="../index.css"` 如果連結前面寫了兩個點 `../`，就會找到上一層的檔案。這個可以連續接起來使用，例如：`../../`，就是找到上上層的檔案，以此類推。
    

在 VS Code 中，在連結處只要打了 `./` 或 `../` ，預設就有快捷選單讓你方便選取檔案，很貼心！

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693929878376/74ab1155-975f-42e2-b159-26473dd24cb9.png align="center")

---

如果你的網頁 CSS、JS、連結、圖片等檔案全部都不見了，或是，按右鍵&gt;檢查，開啟開發者工具，出現許多找不到檔案的錯誤訊息，這種時候可以去查查看是否路徑有跑掉。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695359908225/ed16eb41-269b-4a27-8b1c-c91a7e7d7593.png align="center")