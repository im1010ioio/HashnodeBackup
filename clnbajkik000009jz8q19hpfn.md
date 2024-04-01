---
title: "#18 CSS Flex 彈性盒子：網頁排版的超級寵兒"
datePublished: Wed Oct 04 2023 05:11:16 GMT+0000 (Coordinated Universal Time)
cuid: clnbajkik000009jz8q19hpfn
slug: css-flex
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696255821865/3e1037ec-2b08-4a9d-bce7-6114e10637bc.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696255866302/fb13fb07-8694-4591-ab44-0117af6bf6cd.png
tags: css3, css, css-flexbox

---

> #### ↓ 今日學習重點 ↓
> 
> * 了解 Flex 的主軸線與交錯軸、flex-wrap（容器）
>     
> * 了解 flex-grow、flex-shrink、flex-basis、align-self、order（Flex item）
>     

Flex 又稱彈性盒子，是目前學習 CSS 必學的排版方式之一，有了它幾乎 80% 的版面都可以排出來。過去 `block`、`inline`、`inline-block` 都不是專為排版而生的 CSS 屬性，導致修改排版會變得不方便，於是後來有了 `flex` 與 `grid` 的出現，讓現在的大家可以很輕鬆地安排版面。

`flex` 是單向的排版，而 `grid` 是雙向的排版，今天先讓我們來了解 `flex` 的用法吧！

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696256417180/cd9e8c25-ebca-4bfb-b011-e0c6f103054e.png align="center")

---

## 一、Flex 容器

要使用 flex，首先要準備一個容器，將其設為 `display: flex;`，接著裡面的子層就是 flex 的 item。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696257726796/9f16a902-d7c5-4510-bee1-5a842961dcf7.png align="center")

### 1\. flex-wrap：折行設定

如果 flex 容器裡的 item 超出父層容器，我們可以設定要不要折行，預設是 `nowrap` 不折行。詳細設定如下圖：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696265613940/e18ff9d5-deab-49ab-8ab4-db5c964f9268.png align="center")

### 2\. flex-direction：主軸線 (main axis) 與副軸線 (cross axis)

flex 容器裡面會有 2 個方向可以設定，分別是主軸線（main axis）與副軸線（cross axis，又稱交錯線）。主軸線與副軸線的方向會依據 `flex-direction` 屬性走，預設會是 `row`，可設定 4 個方向：

* `row`
    
* `row-reverse`
    
* `column`
    
* `column-reverse`
    

其中 `row-reverse` 與 `column-reverse`，反轉的只有主軸線，副軸線並沒有反轉。

4 個方向的軸線如下圖所示：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696259840411/1f0b6f1b-37a3-4ee7-8e85-cfde0dac4f34.png align="center")

我們可以進一步設定主軸線、副軸線的排列方式：

#### (1) justify-content

**主軸線**可使用 `justify-content` 屬性設定排列方式，  
常用的設定有：`flex-start`、`center`、`flex-end`、`space-around`、`space-between`、`space-evenly`。

#### (2) align-items

**副軸線**可使用 `align-items`、`align-content (多行情況)` 屬性設定排列方式，  
常用的設定有：`flex-start`、`center`、`flex-end`、`stretch`。

實際舉例，如下圖：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696321449288/8e265efe-c922-4b15-a7dd-2eee2abdd8c0.png align="center")

依據 `flex-direction` 屬性的不同，軸線不同，排版結果會不同。

#### (3) Chrome 開發者工具：flex 工具

如果很難想像軸線會如何變化，可以試玩看看 Chrome 的開發者工具中的 flex 小工具（其實不只 Chrome，各個瀏覽器都有類似功能），可以有更深入的認識喔！

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696312306770/44e22618-236f-4e6d-b582-53743973ce7c.png align="center")

> 其他小工具：[flexbox playground](https://codepen.io/frank890417/pen/ayLvRp)

### 3\. 簡寫：**flex-flow**

上述介紹的 `flex-direction` 與 `flex-wrap` 可以簡寫為 `flex-flow` ：

```css
.flex-container {
    /* flex-flow: flex-direction | flex-wrap; */
    flex-flow: row wrap;
}
```

### 4\. 間距：gap

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696444499800/5af802c5-0e86-4f1a-a630-257a36366ae7.png align="center")

`gap` 是 `row-gap` 與 `column-gap` 的縮寫，可以設置 item 間的間距，可用在 `flex` 與 `grid` 排版上。

```css
.flex-container {
    /* 單值: 上下左右 */
    /* 雙值: 上下(row-gap) | 左右(column-gap) */
    gap: 2rem 1rem;

    /* 等同於：
    row-gap: 2rem;
    column-gap: 1rem; */
}
```

> 延伸閱讀：[gap - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/gap)

---

## 二、Flex item

在容器內的 flex item，我們也可以額外設定許多排版方式。

### 1\. align-self：可蓋掉爸爸的 align-items

`align-self` 可以覆蓋其父容器的 `align-items` 設定。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696267828526/32cabc03-9e32-474a-a9c5-8e04ec3fc204.png align="center")

### 2\. flex (flex-grow、flex-shrink、flex-basis)

flex 屬性是縮寫，可以根據剩餘的空間自動調整大小，其實它是由三個屬性組成：

* `flex-grow`：有多的空間時，依照設定的比例長大，預設為 0（不會自動長大）。
    
* `flex-shrink`：空間不足時，依照比例縮小，預設為 1，設為 0 就不會縮小。
    
* `flex-basis`：縮放的基準值，可以使用不同單位。
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696269219346/54e7615c-fb76-4068-b9bf-66a2e9fa51c0.png align="center")

`flex` 簡寫：

```css
/* 單值，只寫數字時是 flex-grow（flex-basis 此時等於 0） */
flex: 2;

/* 單值，寫成寬高時是 flex-basis */
flex: 10em;
flex: 30px;
flex: min-content;

/* 雙值：flex-grow | flex-basis */
flex: 1 30px;

/* 雙值：flex-grow | flex-shrink */
flex: 2 2;

/* 三值：flex-grow | flex-shrink | flex-basis */
flex: 2 2 10%;
```

> 延伸閱讀：  
> [flex - CSS：层叠样式表 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex)、  
> [Flex 空間計算規則 | 卡斯伯 Blog - 前端，沒有極限](https://www.casper.tw/css/2020/03/08/flex-size/)

### 3\. 使用 margin: auto 可推開兄弟，推去去角落

flex 內的 item 還有一個特性，就是使用 `margin: auto` 時可針對某個方向推開兄弟，上下左右都可以，如下圖所示：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696339333092/037ee0ad-5490-441d-95e5-cdd61aba8e28.png align="center")

這個特性非常實用，最常使用在 navbar 上，左右兩區的連結排列。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696320433466/9331212f-78a9-4fa3-953d-1292c0ab14d3.png align="center")

### 4\. order

這個屬性可以重新排序，預設值為 0，讓 flex item 不再照著原本 html 的順序排序。

```css
.item {
    order: -1;
}
```

---

## 三、Flex 練習小遊戲

網路上有一些練習 CSS 的小遊戲，這些是關於學習 Flex 的，能從遊戲中學習感覺很棒，分享給大家來玩玩看！

### 1\. **六角學院-Flex Pirate 擊倒海盜**

> 連結：[Flex Pirate - 擊倒海盜，獲得網頁排版寶藏](https://hexschool.github.io/flexbox-pirate/index.html#/)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696338638373/f24ade17-e9ea-4baf-ad1e-e32a7f15ee60.png align="center")

### 2\. FLEXBOX FROGGY

> 連結：[Flexbox Froggy - A game for learning CSS flexbox](https://flexboxfroggy.com/)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696338657400/211c2990-168a-4c26-a90c-240974ea9b36.png align="center")

---

好的！今天就先到這裡了。  
大家可以來練習看 flex 排版，很實用，多練幾次就熟了。

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")