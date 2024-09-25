---
title: "#44 CSS 邊框 border 與各種花式邊框的小技巧：borde-image、outline、box-shadow"
datePublished: Wed Sep 25 2024 09:17:38 GMT+0000 (Coordinated Universal Time)
cuid: cm1hnjhxp001y09jthv696xkk
slug: css-border-style
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1727255762271/f19bf159-75db-45c3-bb5c-bd3e307613c8.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1727255850355/7d8f584b-8bc5-46ce-bbd7-06a8d6ca88df.png
tags: css3, css, 2articles1week, border

---

> #### **↓ 今日學習重點 ↓**
> 
> * 學會 CSS 基本邊框 `border` 的用法
>     
> * 了解 `border-image` 的原理與用法
>     
> * 了解如何繪製多重邊框：`outline` / `box-shadow`
>     

前幾篇我們使用CSS 邊框 `border` 畫了很多圖形，但是好像還沒有正式來好好畫邊框。XD今天，讓我們來研究邊框與各種花式邊框。

---

## 一、基本邊框：`border`

`border` 是一個基本的 CSS 屬性，用來設定元素的邊框。它可以定義邊框的寬度、樣式和顏色。

### 基本語法

```css
div {
    border: 寬度 樣式 顏色;
    border: 2px solid #ff6600;
}
```

* **寬度**：例如 `1px`、`2em` 等等，定義邊框的厚度。
    
* **樣式**：常見的樣式有：
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727164006400/e9403843-b322-4f0b-a7a5-1b9e27283227.png align="center")
    
    * `solid` 實線
        
    * `dashed` 虛線
        
    * `dotted` 點線
        
    * `double` 雙線
        
    * `groove` 凹槽效果
        
    * `ridge` 突起效果
        
    * `none` 無邊框
        
* **顏色**：可以使用任何有效的 CSS 顏色值，例如 `#000`、`rgb(255, 0, 0)` 等。
    

> DEMO: [CSS border style](https://codepen.io/im1010ioio/pen/ZEgEMxm)

---

## 二、圖像邊框：`border-image`

如果想要邊框更花俏，`border-image` 可以將圖片設定在邊框上，而不是普通的顏色線條。

### 基本語法

`border-image` 有以下幾種簡寫：

```css
/* source | slice */
border-image: linear-gradient(red, blue) 27;

/* source | slice | repeat */
border-image: url("/images/border.png") 27 space;

/* source | slice | width */
border-image: linear-gradient(red, blue) 27 / 35px;

/* source | slice | width | outset | repeat */
border-image: url("/images/border.png") 27 23 / 50px 30px / 1rem round space;
```

* `source`：  
    是 `url(圖片路徑)` ，指定要使用的圖像。
    
* `slice`：  
    定義如何切分圖像，用以適應邊框的四個方向，建議是準備的圖片寬高的 1/3。
    
* `width`：  
    邊框的寬度，與 `border` 的寬度概念相似。
    
* `outset`：  
    定義邊框超出元素邊界的距離。
    
* `repeat`：重複的方式，選項有 :
    
    * `stretch`（延伸，預設值）
        
    * `repeat`（重複平鋪圖片）
        
    * `round`（平鋪圖像。當無法整數平鋪時，視情況放大或縮小影像）
        
    * `space`（平鋪圖像。當無法整數平鋪時，會用空白間隙填滿在影像周圍（不會放大或縮小影像））
        

### 九宮格縮放的基本原理

當使用 `border-image` 時，我們可以用 `border-image-slice` （即剛剛簡寫中的 `slice`）來告訴瀏覽器如何將圖片劃分成九個部分。

#### 九宮格縮放示意圖

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727171413934/5c750c5c-5c91-494e-98d4-9d9d94648cf3.png align="center")

* **四個角區域**：區域 **1、3、7、9** 是圖像的四個角，通常保持原樣。
    
* **四個邊區域**：區域 **2、4、6、8** 是邊緣，根據 `repeat` 的設定會被水平或垂直延伸（`stretch`）、重複（`repeat`）。
    
* **中間區域**：區域 **5** 是中心區域，如果沒有指定邊框中間部分應該如何處理，則通常不會顯示該部分。
    

### DEMO 1: 餅乾邊框

例如，這樣就能做出像餅乾般的邊框，我準備了一張這要的圖：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727255456319/7fdecc32-639d-4485-bc48-34fb52b40746.png align="center")

結果如以下 DEMO（順便給大家看看不同種 `repeat` 的效果））：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727190867929/14b94d75-13f2-4dc1-aff1-44ce526b2e80.png align="center")

```css
div{
    border-image: url('border-image.png') 50 / 30px / 30px repeat;
}
```

> DEMO: [CSS cookie border](https://codepen.io/im1010ioio/pen/MWNWzyj)

### DEMO 2: 漸層邊框

另外，也可以直接在 `border-image` 上設定漸層喔！只不過這種方式需要設定 border 寬度，還有 `border-image` 內的 `slice` (剛好為)。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727191896043/bea1ed58-63af-40ae-8d03-edb142fa6d5b.png align="center")

```css
div {
    width: 200px;
    height: 100px;
    border: 30px solid;
    border-image: linear-gradient(#eeaeca, #94bbe9) 30;
}
```

> DEMO: [CSS gradient border](https://codepen.io/im1010ioio/pen/wvVvLWV)

### DEMO 3: 美式信封條紋邊框

既然都能繪製漸層邊框，我們也可以繪製條紋邊框，記得前篇繪製的條紋邊框嗎？

> 延伸閱讀：[#39 CSS 幾何背景：條紋、格子、點點、棋盤格子背景 (CSS background)](https://ithelp.ithome.com.tw/articles/10354663)

我們也可以應用到 `border-image` 上，做出一張美式信封。  
跟剛剛一樣的漸層邊框一樣，需要設定 border 寬度，還有 `border-image` 內的 `slice` (剛好和 border 寬度一樣，條紋才會順暢)。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727254135479/a740e6de-ca18-478e-b694-fc9334e6e260.png align="center")

```css
div {
    border: 20px solid transparent;
    border-image:
        repeating-linear-gradient(
            -45deg, 
            #4849b2 0 15px,
            #ffffff 0 30px,
            #e66959 0 45px,
            #ffffff 0 60px) 20;
}
```

> DEMO: [Striped border on envelope](https://codepen.io/im1010ioio/pen/XWvJNZb)

---

## 三、外框：`outline`

`outline` 與 `border` 相似，都是用來描繪元素的框線。但 `outline` 的繪製位置不同，它位於元素的外部邊緣。他同樣也吃 border-radius，可以支援圓角。

### 基本語法

```css
div {
    outline: [寬度] [樣式] [顏色];
}
```

`outline` 的寬度、樣式和顏色設定方式與 `border` 相同，但有兩點不同：

> 1. `outline` 位於元素的外部，不會影響排版，所以這在設計 focus 狀態時特別有用。
>     
> 2. `outline` 只能整體應用於元素四邊，無法像 `border` 一樣針對每一邊單獨設置。
>     

### DEMO

#### 基本用法

例如，當 input focus 時，會有一個 0.25em 寬的藍色虛線外框。：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727235653598/40fc2c9c-ac7a-4d05-a605-71ca8cf890ad.png align="center")

```css
input[type="text"]:focus {
    border-color: #ccc;
    outline: .25em solid #d5e3ee;
}
```

> DEMO: [CSS Border & Outline](https://codepen.io/im1010ioio/pen/jYNwRe)

#### 小技巧：內縮的 `outline`

`outline` 還可以使用 `outline-offset` 屬性內縮，在使用虛線，就會像縫補的補丁一樣：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727192800489/4e88b601-391a-449d-8c22-09730b7e3953.png align="center")

> DEMO: [Patch](https://codepen.io/im1010ioio/pen/wpweqq)

---

## 四、多重邊框：`box-shadow`

如果我的邊框除了 `border`、`outline` 以外，還想要第三層怎麼辦？這時候我們可以利用 CSS 的 `box-shadow` ，使用多重背景一層層疊起來，就能有很多層邊框的感覺了，想要畫幾層都可以。

不過，他與 `outline` 有一樣的性質：

> 1. `box-shadow` 位於元素的外部，不會影響排版，所以這在設計 focus 狀態時特別有用（例如，[Bootstrap 5 的 input focus 效果](https://getbootstrap.com/docs/5.3/forms/form-control/)就是使用 `box-shadow` 做的）。
>     
>     不過，與 `outline` 不同的是：如果你希望使用 `box-shadow` 製造出的框線位於元素內部的話，可以使用 `box-shadow` 的 `inset` 屬性。
>     
> 2. `box-shadow` 只能整體應用於元素四邊，無法像 `border` 一樣針對每一邊單獨設置。
>     

### DEMO

我們可以利用這些性質繪製出位於圓形內部的彩虹邊框：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727192858815/feedc0e5-f3c8-4d1d-b040-83734188a7ee.png align="center")

```css
div {
    padding: 70px;
    height: 80px;
    width: 80px;
    border-radius: 50%;
    box-shadow:
	    0 0 0 15px #F59C82 inset,
	    0 0 0 30px #FDB9FD inset,
	    0 0 0 45px #AAE7FE inset,
	    0 0 0 60px #C3FEB3 inset,
	    0 0 0 75px #FEF6A0 inset;
}
```

> DEMO: [Multiple Borders Rainbow](https://codepen.io/im1010ioio/pen/vpBxyW)

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")