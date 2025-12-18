---
title: "#26 CSS Container Queries 容器查詢：讓 CSS 的計算以容器自身為依據"
datePublished: Thu Oct 12 2023 16:01:58 GMT+0000 (Coordinated Universal Time)
cuid: clnndb6hj000b09lfficwhmku
slug: css-container-queries
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697045470904/1623366a-0166-454f-a715-0cbf0f4592ef.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1697045515099/4fbf749e-e257-4c7e-9be9-1a791542dc3b.png
tags: css3, css, container-queries

---

> #### **↓ 今日學習重點 ↓**
> 
> * 了解 Container Queries 的用法
>     
> * 了解 Container Queries 特有的單位
>     
> * 了解 Container Queries 的使用情境
>     

前幾篇我們學習了 Media Queries，是針對裝置的屬性、大小變化；現在，CSS 新推出了 Container Queries（容器查詢）讓我們可以針對 HTML 元素大小變化，進而改變元素自己的樣式。

改變元素自己是什麼意思呢？讓我們來看看網路上國外大神 [Jhey Tompkins](https://twitter.com/jh3yy) 的可愛 DEMO 就能快速了解了，他用了 CSS 的 Container Queries 加上 Resize 達到了有趣的互動效果：

![CSS Container Queries demo by Jhey Tompkins](https://cdn.hashnode.com/res/hashnode/image/upload/v1697035915314/5f373203-50de-44f5-a927-ab6e21e44261.gif align="center")

> 詳細請看：[Can We Create a "Resize Hack" With Container Queries? | CSS-Tricks](https://css-tricks.com/can-we-create-a-resize-hack-with-container-queries/)

---

## 一、基本的 Container Queries

要使用 Container Queries，首先我們要先定義一個 container，並且設定它的 `container-type`，接著我們就可以使用 `@container` 設定 container 在某個條件下的樣式。

設定寬度的方式與 Media Queries 一樣：

* 可以使用 `max-width` 和 `min-width` 以及 `max-height` 和 `min-height`
    
* 可以使用普通的數學符號：`>`、`<`、`>=` 或 `<=`
    

```css
.container {
    container-type: inline-size;
    width: 30vw;
    .toolbar {
        display: flex;
    }
}

/* 當容器小於 150px， .toolbar 改為直式排列 */
@container (width < 150px) {
    .toolbar {
        flex-direction: column;
        width: 200px;
    }
}

/* 等同於： */
@container (max-width: 150px) { ... }
```

---

## 二、Container 的詳細設定

接下來，我們要詳細介紹 container 的詳細設定：

### 1\. `container-type`

有設定 `container-type` 的元素就會變成一個 container 元素，有兩種屬性可以設定：

* `inline-size`：左右方向，高度會被內容撐高。
    
* `size`：上下左右方向，我猜想是因為設定後它已被預期會改變高度，所以不會被內容撐高，會失去其高度，要再設定其高度。
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697043304830/ad1db53a-7957-48c3-978e-7bbe8f327eeb.png align="center")

### 2\. `container-name`

如果我們直接使用 `@container` ，所有有設定 `container-type` 的元素都會被選取到。這時候我們可以使用 `container-name` 區分不同的 container 元素，建議一定要設定這個屬性。讓我們來改寫最一開始的 code：

```css
.container {
    container-type: inline-size;
    container-name: toolbar;
    width: 30vw;
    .toolbar {
        display: flex;
    }
}

/* 當名為「toolbar」的容器小於 150px， .toolbar 改為直式排列 */
@container toolbar (width < 150px) {
    .toolbar {
        flex-direction: column;
        width: 200px;
    }
}
```

### 3\. 簡寫為 `container`

以上兩種屬性可以簡寫為 `container`：

```css
.post {
 /* container: <container-name> / <container-type>; */
    container: sidebar / inline-size;
}
```

---

## 三、Container Queries 特有的單位

Container Queries 有自己特有的單位，總共有以下幾種單位：

| 單位 | 說明 |
| --- | --- |
| `cqw` | 1% container 的寬度（`width`） |
| `cqh` | 1% container 的高度（`height`） |
| `cqi` | 1% container 的 `inline-size` |
| `cqb` | 1% container 的 `block-size` |
| `cqmin` | `cqi` 與 `cqb` 的最小值 |
| `cqmax` | `cqi` 與 `cqb` 的最大值 |

這些單位也結合了我們之前提過 CSS 邏輯屬性的 `inline-size` 與 `block-size` ，詳細請見之前的文章：

> 延伸閱讀：[#23 CSS 邏輯屬性 Logical properties 與 Writing modes](https://im1010ioio.hashnode.dev/css-logical-properties)

---

## 四、Container Queries 的應用

Container Queries 是針對「自己」容器大小變化，讓我們想想可以做什麼？既然是自己的變化，那就非常適合用在重用性高抽出來的 Component。

### 1\. 卡片資訊

比如說，用戶的資訊可能出現在很多地方，並且要適應不同尺寸，太小時隱藏詳細資訊：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697123664592/05bc18eb-4e7d-4aa2-a541-ce0cbbbd9219.png align="center")

> [DOMO 連結：User Info Card with Container Queries](https://codepen.io/im1010ioio/pen/RwEdLXx)

這邊我們使用了 `cqw` 單位，隨大小變更間距與陰影，搭配使用了 CSS 數學函式 `clamp()`、`min()` 控制字型大小、間距，並且練習使用了 CSS 邏輯屬性。

### 2\. 工具列

或者是也很適合用在工具列上，也許同個網站中會有很多地方都要使用工具列樣式，而且要因應不同大小調整，太小時不顯示文字：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697125844072/5d802bde-b568-40ce-aeaa-d3193e40e1d4.png align="center")

> [DOMO 連結：Toolbar with Container Queries](https://codepen.io/im1010ioio/pen/PoXgwpo)

使用的技術與第一點基本上差不多，總之使用起來很好用！

Container Queries 可以應用的範圍應該不只這些，大家可以一起來探索看看。

---

> 延伸閱讀：[\[譯\] CSS 容器查詢單位 - DEVLOG of andyyou](https://andyyou.github.io/2021/09/29/css-container-query-units/)

---

## 五、教學資源

另外，網路上六角學院的教學影片講解的也很詳細，大家可以參考看看。

%[https://youtu.be/IlzfVQmUjwM?si=w5uOPo6bzcpvNFdj] 

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")