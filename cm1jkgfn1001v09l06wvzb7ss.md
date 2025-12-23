---
title: "#46 CSS 濾鏡 filter/ backdrop-filter：模糊、透明圖片加陰影、調色濾鏡、毛玻璃、漸進式模糊效果"
datePublished: Thu Sep 26 2024 17:26:48 GMT+0000 (Coordinated Universal Time)
cuid: cm1jkgfn1001v09l06wvzb7ss
slug: css-filter-backdrop-filter
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766469228027/8f55826e-df05-4dc3-abb1-3ae188bb159c.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766469217833/fd3064fb-1106-4a9f-8e16-394bdcecfd43.png
tags: css3, css, filter

---

除了用繪圖軟體在圖片上調整色調，CSS 內建的濾鏡效果也能讓我們做到這些特殊效果，例如：模糊、變亮、對比、色相、飽和度調整等等，甚至還可以做到毛玻璃效果！

今天，我們要介紹的是 `filter` 與 `backdrop-filter` 這兩個強大的 CSS 屬性。

> #### **↓ 今日學習重點 ↓**
> 
> * 學會 CSS 濾鏡 `filter` 的用法
>     
> * 學會 CSS 背景濾鏡 `backdrop-filter` 的用法
>     

---

## 一、濾鏡 `filter`

`filter` 屬性能讓你對 HTML 元素本身做一系列的圖像處理效果，讓我們能在不使用繪圖軟體的情況下實現各種特效，例如：模糊、明度、對比度等。

### 基本語法

`filter` 使用的語法很簡單，語法如下：

```css
div {
    filter: 方法(數值);
}
```

### 特效效果

而 `filter` 總共有以下幾種效果可以使用：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727352312516/afe5e033-3d58-40af-a63d-4f1ac08fe0da.png align="center")

> DEMO: [CSS filter](https://codepen.io/im1010ioio/pen/YzmPbMr)

* `blur`**：模糊**  
    需要填寫數值，單位可以是 `px`、`em`、`rem` 等。
    
* `brightness`**：明度**  
    調整亮度，需要填寫百分比值：100%為原本的明度，往下是調暗，往上是調亮。
    
* `contrast`**：對比度**  
    調整對比度，需要填寫百分比值：100%為原本的對比度，往下是減低，往上是增加。
    
* `grayscale`**：灰階**  
    轉為灰階，需要填寫 0 到 1 之間的值，1 代表完全灰階。
    
* `hue-rotate`**：色相**  
    調整色相環的位置，需要填寫角度，單位可以是 `deg`（度數）或 `turn`（圈數）。
    
* `invert`**：反轉**  
    轉為相反的顏色，會變成對比色，需要填寫 0 到 1 之間的值，1 代表完全相反。
    
* `opacity`**：透明度**  
    調整對比度，需要填寫百分比值：100%為不透明，效果等同於：`opacity: 數值;`。
    
* `sepia`**：棕褐色**  
    轉為懷舊的褐色調，需要填寫 0 到 1 之間的值，1 代表完全褐色。
    
* `saturate`**：飽和度**  
    調整飽和度，需要填寫百分比值：100%為原本的對比度，往下是減低，往上是增加。
    
* `drop-shadow`**：陰影**  
    在圖片中非透明的周圍加上陰影，這針對透明圖片超好用！  
    例如，如果單單為透明圖片加上基本的陰影 `box-shadow` ，會像下方圖片一樣悲劇，陰影沒有加在實際圖案的周圍，但用了 `filter` 的 `drop-shadow` 就能為實際圖案的邊緣加上陰影：
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727367155549/d4d5f2ff-fecd-4914-8f08-f8645e85ca50.png align="center")
    
    > DEMO: [CSS box-shadow v.s filter drop-shadow](https://codepen.io/im1010ioio/pen/XWvbbWG)
    

### 多重特效

你也可以使用多種特效在一個 HTML 元素上，只要簡單使用空格隔開就好了，例如：

```css
div {
    filter: contrast(175%) brightness(105%);
}
```

---

## 二、背景濾鏡 `backdrop-filter`

`backdrop-filter` 可以對 HTML 元素後面的背景製作濾鏡效果，影響的是背後的東西，而不是自己本身。最常見的是用來製作非常受歡迎的「**毛玻璃效果 Glassmorphism**」，利用模糊區隔出背景，製造出透明感的景深效果，最常見被用在 iOS 系統中、彈跳視窗光箱（lightbox）或是導覽列（Navbar）上等等。

在 Dribbble 上搜尋的 Glassmorphism 的話，會出現以下像這樣酷炫的 UI，給大家參考：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727368294436/12e6cbee-ef91-44e2-b981-7bd975e3284a.png align="center")

### 基本語法

`backdrop-filter` 語法的使用方式，基本上和 `filter` 一樣：

```css
div {
    backdrop-filter: 方法(數值);
}
```

### 特效效果

`backdrop-filter` 通常用在浮動的 HTML 元素上（如：絕對定位、固定定位、`sticky` 等等）。它可使用的效果和 `filter` 一樣，請參考上面 `filter` 所列出來的所有效果。

只不過經我實測，`opacity` 和 `drop-shadow` 不起作用，所以以下的 DEMO 範例沒有它們：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727355631001/0656962c-04f7-4090-a588-dd11c678e9f0.png align="center")

> DEMO: [CSS backdrop-filter](https://codepen.io/im1010ioio/pen/RwXNzOd)

剛剛說的「毛玻璃效果 Glassmorphism」就是使用其中的 `blur()` 效果。

### 多重特效

和 `filter` 一樣，你也可以使用多種特效在一個 HTML 元素上，只要簡單使用空格隔開就好了，例如：

```css
.element {
  backdrop-filter: blur(10px) brightness(60%);
}
```

上面的例子會將元素後面的背景模糊處理，並且使其稍微變暗（亮度調低至 60%）。這樣可以做出類似黑色毛玻璃效果。

---

## 三、漸進式模糊（Progressive blur）

會用 `backdrop-filter` 後，搭配昨天我們學到的 CSS `mask` 語法，我們還可以進一步製作漸進式模糊。

> 延伸閱讀：[#45 CSS 中的半透明遮罩 mask，實現各種模糊邊緣特效](https://im1010ioio.hashnode.dev/css-mask)

什麼是漸進式模糊呢？漸進式模糊（Progressive blur）就是 UI 中照片下半部會逐漸模糊，然後下方顯示其他文字資訊等。

![漸進式模糊 Progressive blur of Apple Invites](https://cdn.hashnode.com/res/hashnode/image/upload/v1739157604187/205dc809-1f0b-4422-b53e-bd82eac2a631.png align="center")

這種背景模糊的 UI，在 Apple 的 iOS UI 中很常出現這種效果（例如：[Apple Invites](https://www.apple.com/tw/newsroom/2025/02/introducing-apple-invites-a-new-app-that-brings-people-together/)），過去在網頁上很難做到，但是現在只要靈活運用這兩個語法就能做到囉！

### DEMO

這邊我們在有背景圖的 `div` 上，新增一個滿版的偽元素 `::before` 並且設定背景濾鏡 `backdrop-filter` ，然後再透過 CSS `mask` 線性漸層調整模糊的範圍，就可以做到啦！

![CSS Progressive Blur 漸進式模糊](https://cdn.hashnode.com/res/hashnode/image/upload/v1739169025582/2dce82ed-50e7-416b-a1d1-021c51bc554c.png align="center")

```css
.photo{
    position: relative;
    overflow: hidden;
    background-image: url("image.jpg");
    background-size: cover;
    overflow: hidden;
    &::before{
        content: "";
        display: block;
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        backdrop-filter: blur(10px);
        mask: linear-gradient(180deg, transparent 350px, #000 450px);
    }
}
```

> DEMO 連結：[CSS Progressive Blur](https://codepen.io/im1010ioio/pen/raBXezV)

---

## 四、固定定位（`fixed`）+ `filter`/`backdrop-filter` 的陷阱

如果 fixed 項目的父層上有 `filter` 或 `backdrop-filter` 屬性，該 fixed 項目就不會依據「瀏覽器的視窗大小」進行定位，而是依據「該 HTML 的父層」定位。

雖然我有點忘記當初是因為什麼版型，遇到這樣的陷阱，  
但我這邊可以做個實例給大家參考看看：

> [Conflict between fixed item and filter (backdrop-filter)](https://codepen.io/im1010ioio/pen/VwoLvey)

**解法：** 改變 `filter` 的元素，或是改使用 `sticky` 做到類似效果。

> 延伸閱讀：
> 
> * [#21 CSS Position：relative、absolute、fixed、sticky 找到適合的定位](https://im1010ioio.hashnode.dev/css-position)
>     
> * [filter与fixed冲突的原因及解决方案 - 掘金](https://juejin.cn/post/6844904117974859783)
>     

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")