---
title: "#34 CSS 讓圖片填滿容器的各種方法，以圓形大頭貼為例：object-fit 與 background-size，搭配 aspect-ratio"
datePublished: Thu Jan 11 2024 15:49:15 GMT+0000 (Coordinated Universal Time)
cuid: clr9dxcg500020ajt7t196cy3
slug: css-object-fit-background-size-aspect-ratio
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704951919247/46afcb4a-ee12-4263-8faa-8fb8769d8b75.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1704951935564/4b9de93b-8403-4912-96bf-fb0274c9a113.png
tags: background, css, images, 2articles1week, css-object-fit-property

---

> #### **↓ 今日學習重點 ↓**
> 
> * 在 HTML 加入圖片
>     
> * 使用 `object-fit` 讓圖片填滿容器
>     
> * 使用 `background` 讓圖片填滿容器
>     

## 在 HTML 加入圖片

我們可以使用 HTML 的 `<img>` 標籤在網頁中放入圖片：

```xml
<img src="圖片的路徑" alt="圖片的敘述文字，圖片失效的時的替代內容">
```

在 `<img>` 的 `src` 屬性中放上圖片的路徑，就能顯示圖片。  
關於如何填寫路徑，可以參考這系列之前的文章：

> 延伸閱讀：[#06補充 網頁的根、絕對路徑、相對路徑，那些關於路徑的小知識](https://im1010ioio.hashnode.dev/html-file-paths)

另外，`<img>` 的 `alt` 屬性是圖片的敘述文字，是圖片失效的時的替代內容，也是搜尋引擎搜尋圖片的依據，能夠提高圖片被搜尋到的機率與排名。

如果沒有填寫，對電腦與搜尋引擎來說，表示這張圖片可能沒有意義，會被當成裝飾性圖片，所以建議養成填寫的習慣喔！

> 延伸閱讀：[Img Alt是什麼？好的替代文字怎麼寫？SEO專家教你7秘訣！](https://welly.tw/serp-rank-optimization/what-is-img-alt)

---

## 直接設定寬高，圖片會被壓扁

但是直接設定他的寬高時，如果拿到的圖片比例，與我們設定的寬高比例不同時，圖片就會因此變形。以設定大頭貼照片為例，全部照片都壓扁了這怎麼行？

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703730370345/d83a5457-52c1-4da6-8ee0-62f8ed77690c.png align="center")

<s>咦？變瘦了，好像可以？誒，不對...</s>

```css
img {
    width: 200px;
    height: 200px;
    border-radius: 50%;
}
```

> 圖片來源：[圖片1](https://unsplash.com/photos/woman-on-wheat-field-during-daytime-R1Ku62Z7zqE)、[圖片2](https://unsplash.com/photos/woman-standing-near-body-of-water-dcZsxUAAJXs)、[圖片3](https://unsplash.com/photos/woman-in-blue-sleeveless-dress-standing-near-wall-rpeJciNPeOg)

要解決這個問題，有些網頁會設計在上傳圖片時，提供裁切功能，於後端存下正確比例的圖片，使照片比例與顯示比例一致。只不過這需要使用到 HTML Canvas 與 JS 操作，暫時不在我們這次的討論範圍中。

如果要在不修改原圖的情況下，讓照片比例不要失真，我們還可以使用 CSS 製作一個相框，假設照片的重點物在中間，不論橫向與直向照片皆擷取中間的畫面，就會像下面這樣：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704904069468/a0cab3a4-9e26-4d11-849b-9cf06d005904.png align="center")

要達到這個效果，有兩種做法：

* 一是使用 `object-fit: cover;`，
    
* 二是使用 `background-size: cover;` 加 `background-position: center;`，
    

詳細做法與優缺點請往下看。

---

## 解決方法：使用 CSS 製作一個相框

### 1\. object-fit: cover

#### (1) 父層 (相框)

首先我們先在一個 div 中放入照片，父層的 div 當作相框，設定 `border-radius: 50%;` 變為圓形，接著使用 `overflow: hidden;` 讓超出的圓形範圍的部分被隱藏起來。

#### (2) 子層 (圖片) `<img>`

在裡面的圖片，將其寬度設為 `100%`，並使用 `aspect-ratio: 1 / 1;` 讓他的比例為一比一。父層的會被裡面的 `<img>` 撐高，不過 HTML `<img>` 預設的 display 為 inline，所以它的 line-height 會造成與父容器高度略有不同，可以將父層 line-height 設為 0，或是將 `<img>` 設為 block。

> 延伸閱讀：[#17 CSS block、inline、inline-block：網頁排版的御三家](https://im1010ioio.hashnode.dev/css-block-inline-inline-block)

最後再在 `<img>` 上加上 `object-fit: cover;` 就能貼合父層相框了。

> 關於 `object-fit` 的值除了 `cover` 外，還有很多種值可以設定，如 `fill` 與 `contain`，詳細請看：[object-fit - CSS：层叠样式表 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/object-fit)

#### (3) HTML 實作

```xml
<div class="avatar-frame">
    <img src="images/avatar.jpg" alt="使用者大頭貼">
</div>
```

#### (4) CSS 實作

```css
.avatar-object-fit{
    width: 200px;
	border-radius: 50%;
	overflow: hidden;
/* 	line-height: 0; */
	> img{
	/* 	HTML <img> 預設為 inline, 
		它的 line-height 會造成與父容器高度略有不同,
		可以將父層 line-height 設為 0, 
		或是將 <img> 預設為 block */
		display: block;
		width: 100%;
		aspect-ratio: 1 / 1;
		object-fit: cover;
	}
}
```

#### (5) 優缺點

**優點：**

* 使用 `<img>` 標籤，使用者可以按右鍵存檔
    
* 對於瀏覽器搜尋 SEO 比較好
    
* 不用另外設定就能列印
    

**缺點：**

* 當圖片不想給使用者按右鍵就可存檔時，不適合使用
    
* 如果內部有其他裝飾性元素要用絕對定位 `position: absolute` 超出相框時，`overflow: hidden` 會將其擋住，所以不適用。所謂超出相框的元素，比如說 FB 在大頭貼旁的這種圖示：
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704984049822/1ebe8679-8944-46d5-867a-476713ef49ec.png align="center")
    
    當然如果一定要使用這種方式寫，也可以在最外面再多包一層，改讓圖示定位在祖父的那一層上，就解決這個問題了。
    

---

### 2\. background

還有另外一個方法是使用 CSS 中的 `background` ，讓圖片變為背景圖，其中有許多細部屬性可以使用，例如：

* `background-color`
    
* `background-image`
    
* `background-size`
    
* `background-position`
    
* `background-repeat`
    
* `background-attachment`
    

這系列的屬性也能夠簡寫為 `background`，簡寫的順序是：

```css
div{
    background: color image attachment repeat poition / size;
}
```

> 更多屬性與變化請參考：[background - CSS：层叠样式表 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background)

這次製作大頭貼，我們先學習使用：`background-color` 、 `background-image` 、 `background-size` 與 `background-position` 。

#### (1) [background-color](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-color)

設定背景色，可以使用 CSS 各種設定顏色的方式。

> 延伸閱讀： [#31 CSS 顏色設定：基本的 hex、rgb()、cmyk()、hsl()、hsb() 、hwb() 與明日之星的 lch()、oklch()](https://im1010ioio.hashnode.dev/css-colors-hex-rgb-hsl-lch-oklch)。

#### (2) [background-image](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image)

使用 `background-image: url("圖片路徑")` 可以載入圖片，作為背景圖片。另外，也可以使用這個語法來繪製漸層色，之後的文章我們會再解說。

`background-image` 設定了後會蓋過 `background-color` ，不過還是可以設定 `background-color` 作為圖片載入前預設顏色。

#### (3) [background-size](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-size)

這個屬性用來設定背景圖的大小，可以使用寬度單位（如百分比），也可以設定關鍵字：

* `cover` 保留固定比例，圖片填滿容器，符合我們這次的需求。
    
* `contain` 保留固定比例，圖片最長的那一邊與容器同高。
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704986635740/17d810eb-c64a-46f3-b6f2-9f4d483738c9.png align="center")

#### (4) [background-position](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-position)

這個屬性用來設定背景圖的位置，預設值會是左上 ( `background-position: top left;` )，我們希望照片擷取中間，所以這次會設定為 `background-position: center;` 。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705028057533/cb29fa6c-ef5a-4f8a-ad91-82ef81f948f4.png align="center")

#### (5) HTML 實作

```xml
<div class="avatar-frame"></div>
```

#### (6) CSS 實作

```css
.avatar-frame{
    width: 200px;
	border-radius: 50%;
	aspect-ratio: 1 / 1;
	background-color: #eee; /* 可以做為預設的顏色 */
	background-image: url("images/avatar.jpg");
	background-size: cover;
	background-position: center;
	
	/* 需要列印必須要加上 */
	print-color-adjust: exact;
    -webkit-print-color-adjust: exact; /* for Chrome, Edge, Opera */
}
```

> 要注意的是：  
> background 預設是無法被列印的，如果需要列印必須要加上 `print-color-adjust: exact;`，而目前 Chrome, Edge, Opera 需要加上前綴 `-webkit-`。
> 
> 延伸閱讀：[#25 CSS 列印的小技巧：@media print、break-before/after/inside、@page](https://im1010ioio.hashnode.dev/css-media-print)

#### (7) 優缺點

**優點：**

* 當圖片不想給使用者按右鍵就可存檔時，適合使用
    
* 不需要另外使用 `overflow: hidden` 遮住圖片超出部分，所以內部可以放絕對定位 `position: absolute` 的裝飾元素，超出外框也沒問題
    

**缺點：**

* 使用者無法按右鍵存檔
    
* 對於搜尋引擎 SEO 不好
    
* 要列印，要再加上 `print-color-adjust` 的設定
    

---

## DEMO

兩者的 DEMO 實作請參考下面，大家可以比較看看：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704964875276/ef5e6b0e-892a-48e4-a845-2139b4593264.png align="center")

> DEMO：[object-fit vs. background-size](https://codepen.io/im1010ioio/pen/bGZwpRL)

---

本篇雖然是以 1:1 的大頭貼為範例，這個方法當然也適用於其他的比例。  
固定圖片比例，可以讓版面變得整齊，例如 [Dribbble](https://dribbble.com/)：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704906909542/ac437cc0-59fa-4b49-885e-f38fe6fc2159.png align="center")

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")