---
title: "#11 開始寫 Css 或程式必須知道的 3 個原則：Dry & Kiss & Yagni"
datePublished: Wed Sep 27 2023 05:00:32 GMT+0000 (Coordinated Universal Time)
cuid: cln1a2sqv000009l7dqrna37b
slug: css-dry-kiss-yagni
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1764820375489/46c2ca08-6de0-4cd6-9dc0-5a83d4343055.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1764820361224/23ef3490-5a3a-456d-a2f8-7ffaba424e3b.png
tags: css3, css

---

> #### ↓ 今日學習重點 ↓
> 
> * 了解開發的三大原則：DRY & KISS & YAGNI
>     

在進入寫 CSS（或其他程式碼）的世界之前，有幾個重要的原則值得我們了解和牢記。這些能夠提高 code 的品質，讓他們未來容易維護和擴增。以下將介紹三個重要的原則：

* DRY（Don't Repeat Yourself）、
    
* KISS（Keep It Simple, Stupid）和
    
* YAGNI（You Aren't Gonna Need It）。
    

---

## **DRY（不要重複自己）**

> Don't Repeat Yourself.

DRY 原則是程式設計中的一個基本原則，也適用於 CSS 的撰寫。這個原則的核心思想是盡量避免 code 中的重複部分。當你在不同地方多次使用相同的片段時，不僅會讓 code 變得難以維護，還容易發生錯誤。

在 CSS 中，可以透過使用 class 和 tag 選擇器，設定重複的樣式，來實現 DRY 原則。這樣一來，如果要修改，只需在一個地方修改，不用在整個專案中搜索和替換。

### 例子 1：善用 class

```css
.list-A {
    background-color: #f5f5f5;
    color: #aaa;
}
.list-B {
    background-color: #f5f5f5;
    color: #888;
}

/* 可以再多使用一個 class 設定共用的樣式，變成： */
.list {
    background-color: #f5f5f5;
}
.list-A {
    color: #aaa;
}
.list-B {
    color: #888;
}
```

### 例子 2：善用逗號（**群組式宣告**）或巢狀 CSS

```css
li:before{
    content: "";
    display: block;
    background-color: pink;
}
li:after{
    content: "";
    display: block;
    background-color: cyan;
}

/* 可以使用逗號與巢狀 CSS，同時選取兩個元素寫共用的部分，變成： */
li{
    &:before, &:after{
        content: "";
        display: block;
    }
    &:before{
        background-color: pink;
    }
    &:after{
        background-color: cyan;
    }
}
```

---

## **KISS（保持簡單）**

> Keep It Simple, Stupid.

KISS 原則的目標是保持 code 的簡單。寫 CSS 時，盡量要避免過度複雜。越簡單就越容易理解、測試和維護，減少你的工作量。

比如說，選擇適合的選擇器，避免不必要的巢狀結構，並且選擇有意義的 class 或 id 命名。

### 例子 1：巢狀太多層

巢狀太多層了，會不好管理。如果未來要改裡面的樣式，會記不得上面寫了幾層爸爸。如果是 Sass (SCSS) 檔案，可能會造成編譯的 loading，建議在三層內為佳。

```css
/* 巢狀態多層的例子 */
#col-main {
    background-color: white;
    .main-content {
        margin: 1.5rem;
        .step-content {
            ...
            .title {
                ...
                .img { ... }
            }
        }
    }
}

/* 可以改成： */

/* 分為大範圍容器的部分 */
#col-main {
    background-color: white;
    .main-content {
        margin: 1.5rem;
    }
}
/* 與獨立內容的部分 */
.step-content {
    ...
    .title {
        ...
    }
    .title .img {
        ...
    }
    /* 雖然這裡 .title 重複了，不符合 DRY，但是比較好讀 */
    /* 原則有時也會有互斥的時候，這時候優先選擇較好維護的 */
}
```

### 例子 2：命名語意衝突

命名與內容不符，會讓接手人或未來的自己頭暈。

```css
/* 會發生這個狀況通常可能是，主要按鈕本來是藍色的，後來改成了橘色的 */
.button-blue {
    background-color: orange;
}

/* 可以改成： */
.button-primary {
    background-color: orange;
}
```

```css
/* 這個發生狀況可能也與上面雷同，原本側邊欄在左側，後來改為右側 */
.menu-left {
    float: right;
}

/* 可以改成： */
.side-menu {
    float: right;
}
```

### 例子 3：謹慎使用數字

```css
/* 不 OK 的情況：過多或隨意的數字，未來絕對會忘記 27 是什麼意思，與其他 1 - 26 又有何不同 */
.title-27 { ... }

/* OK 的情況：於團隊內部定義好標題分為六級 */
.title-1 { ... }
.title-2 { ... }
.title-3 { ... }
.title-4 { ... }
.title-5 { ... }
.title-6 { ... }
```

---

## **YAGNI（你現在不需要它）**

> You Aren't Gonna Need It.

YAGNI 指的是不要過度設計，或添加不必要的功能。和 KISS 一樣，也是為了保持 code 的簡單，並減少不必要的工作量。

在 CSS 中，YAGNI 原則建議你只加上目前需要的樣式就好了，而不是為了未來可能的變化寫過多的 CSS。讓 CSS 更輕巧一些，瀏覽器的載入速度能更快，使用者體驗就會更好。

### 例子 1

整個網站的 CSS，每一頁建議有一份共用的 CSS 和一份屬於這個頁面的 CSS，而不是將整個網站的 CSS 全部寫成一大包。index 頁面不需要 about 頁面的樣式，就不需要載入。

![YAGNI](https://cdn.hashnode.com/res/hashnode/image/upload/v1694508598331/4e8f834c-a1f2-4780-8ece-9b7242b596c4.png align="center")

### 例子 2

使用 CSS 各種框架時，雖然有點不符合這個原則，但是講究的話可以研究該框架的結構，獨立引用需要的部分就好。以 Bootstrap 為例，若我的網頁不需要 table、forms 等相關樣式，就不要載入就好：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694457657154/ca2d6eb0-a46d-4c65-9cfb-a34eae7f590d.png align="center")

---

## 結論

總之，這三個原則（DRY、KISS 和 YAGNI）是寫 code 時的大方向，當然依據實際情況可以再做微調。如果有互斥的時候，以好維護的、好懂的為優先。

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")