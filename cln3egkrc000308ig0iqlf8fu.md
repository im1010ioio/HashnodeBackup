---
title: "#13 CSS 盒子模型 (Box Model)：border-box & content-box"
datePublished: Thu Sep 28 2023 16:38:46 GMT+0000 (Coordinated Universal Time)
cuid: cln3egkrc000308ig0iqlf8fu
slug: css-box-model
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695657194704/449e8374-662c-4cbb-8897-0ac46449eaed.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695657236726/8838d4de-c8a1-4fe9-9cac-187aa6b761a4.png
tags: css3, css

---

> #### ↓ 今日學習重點 ↓
> 
> * 了解網頁上，構成一個 Box 盒子的內容
>     
> * 了解 CSS border-box & content-box 有何不同
>     

在網頁中，每個 HTML 元素都是一個方塊，我們又稱之為「盒子 Box」。

這個盒子包含了它的內容、內部間距、邊框線與外部間距，光用說的有點抽象，讓我們以 Facebook 的一篇貼文作為例子。FB 的貼文是卡片式設計，這個卡片 Box 裡面會有：

## 構成 box 的內容

### 1\. content (內容)

Box 的主要內容物的區域。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695653204247/913fb38f-c117-4e52-9888-af40fb07a06b.png align="center")

### 2\. padding (內部間距)

通常一張卡片會設定一些 padding (內部邊距)，讓畫面不要太緊迫。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695653221587/1c5cd531-6c41-4867-96d4-b836ff997c0a.png align="center")

Padding (內部間距) 共有四個方向：上、下、左、右，可以設定：

```css
.card {
    padding-top:    12px;
    padding-bottom: 12px;
    padding-left:   16px;
    padding-right:  16px;
}
```

不過這樣寫 CSS 會變得好長，我們可以寫成簡寫，一行解決它：

```css
.card {
    /* 1個值的簡寫是代表四個方向的數值都一樣 */
    padding: 16px;

    /* 2個值的簡寫順序是：「上下 / 左右」 */
    padding: 12px 16px;

    /* 3個值的簡寫順序是：「上 / 左右 / 下」 */
    padding: 12px 16px 12px;

    /* 4個值的簡寫順序是：「上 / 右 / 下 / 左」 => 是順時針 */
    padding: 12px 16px 12px 16px;
}
```

### 3\. border (邊框線)

Box 也可以設定他的 border (邊框線)，只不過 FB 這邊沒有設定。Border 是屬於這個 box 內最外面的元素。另外，圓角也是在 border 上設定的。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695653231057/04b46d1e-bc4c-4726-a24e-7df5ccc4e2ae.png align="center")

一個基本的 border (邊框線) 會有這幾個值可以設定：

```css
.card {
    border-width: 2px;   /* 邊框的寬度 */
    border-style: solid; /* 邊框的種類：直線、虛線、點點...等 */
    border-color: blue;  /* 邊框的顏色 */
}
```

> `border-style` 的全部種類請參考這裡：[CSS Borders](https://www.w3schools.com/css/css_border.asp)

當然，我們一樣也可以寫成簡寫：

```css
.card {
    border: 2px solid blue;
}
```

也可以分開四個方向設定，或只設定一邊有：

```css
.card {
    border-top:    2px solid blue;
    /* border-bottom: 2px solid blue; */
    /* border-left:   2px solid blue; */
    /* border-right:  2px solid blue; */
}
```

而圓角的語法是：

```css
.card {
    border-radius: 4px;
    /* 如果在正方形的情況下，設定 50% 就會變成圓形 */
    /* 如果是不是單純顏色，有圖片或背景圖等等，需要加上 overflow: hidden; 圓角才會出現 */
}
```

圓角也可以四個角分開設定：

```css
.card {
    border-top-left-radius:     4px;
    border-top-right-radius:    4px;
    border-bottom-left-radius:  4px;
    border-bottom-right-radius: 4px;
}
```

### 4\. margin (外部間距)

我們可以針對 Box 設定他的 margin (外部間距)，只不過 margin 已在 box 外面。Margin 會幫你把周圍的東西推開。

> 另外，值得注意的是：如果你的 box 的 display 是 block，margin 會互相重疊，這叫作「邊距重疊 (margin collapsing)」。詳細情況請看 [DEMO](https://codepen.io/im1010ioio/pen/jOXzyyN)。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695653243895/9e935d1d-85c5-4640-81e7-7fb3bbe5e2b8.png align="center")

Margin (外部間距) 和 padding 一樣也有四個方向：上、下、左、右，可以設定：

```css
.card {
    margin-top: 12px;
    margin-bottom: 12px;
    margin-left: 16px;
    margin-right: 16px;
}
```

其實寫法和 padding 一模一樣，簡寫的部分就不贅述了。

<s>好的，這樣你就已經學會如何用 CSS 畫一個 box 了⋯⋯</s>

### 不！！不！才沒有！

要掌握好 box 你必須要多了解一個概念：`box-sizing`。讓我們往下看下去。

---

## Box-sizing：設定計算 box 寬高的依據

CSS 的屬性 `box-sizing` 會決定元素的**寬度**及**高度**是用何種方式計算，他有兩種屬性：`content-box` 與 `border-box` ，也許你已猜到，他們分別是以剛剛上述所說 box 的 content 與 border 為基準而改變元素的大小。

我們用下面的圖片舉例說明會比較詳細，以寬度為例。  
假設我們將卡片寬度設為 600px，padding 10px，border 1px：

### 1\. `content-box`

使用 `content-box` 時，被設定為 600px 的地方會是卡片的 content 區域，不包含左右的 border 和 padding，所以要知道卡片最後實際的寬度，要再加回來，實際寬度會是 622px（600px + 10px\*2 + 1px\*2）。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695573302506/aac42030-cfdf-4444-b8a0-2ec78475bc8c.png align="center")

`content-box` 是瀏覽器的預設值，但是這會讓開發時變得不夠直覺，如果每次設定卡片寬度時，都需要去計算卡片、 padding 與 border 之間的數值，不是很麻煩嗎？

所以，我們通常在一開始就會把 `content-box` 給改掉，改成下面的 `border-box` 。

### 2\. `border-box`

使用 `border-box` 時，被設定為 600px 的地方會是卡片的 border 區域，border 區域剛好就是卡片最後實際的寬度。也就是說，我設定卡片寬度是多少他就是多少，不用再去計算 padding 與 border。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695573338080/5ba50472-48ba-450d-a60d-1b0960eecbcc.png align="center")

通常情況下，會建議全部都使用 `border-box` 進行開發，可以在一開始就使用 `*` 選擇器設定，這樣排版能夠更直覺、輕鬆。

```css
*, *::before, *::after{
    box-sizing: border-box;
}
```

---

## 結論

如果在開發上，你發現 HTML 元素大小有些怪怪的，可以找找看是不是 `box-sizing` 方面的關係。

另外，按右鍵&gt;檢查，可以開啟開發者工具，在左邊選取 HTML 元素，在右側可以查看這個元素的 CSS，在右邊往下滑到底，會出現這個元素所有的 margin、border、padding、content 示意圖。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695657062200/9c389100-f099-46c4-a1b1-8c2bb4079f9e.png align="center")

大家也可以透過這個方式觀察其他人寫的網頁，藉此熟悉 CSS 盒子模型 (Box Model)。

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")