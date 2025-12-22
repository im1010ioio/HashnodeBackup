---
title: "#35 圖片的 1x, 2x, 3x 是什麼？關於網頁上圖片解析度的處理：HTML <img> srcset、CSS image-set() 與 @media resolution"
datePublished: Wed Jan 17 2024 16:47:18 GMT+0000 (Coordinated Universal Time)
cuid: clri0n3p9001709l0hu4rbz0z
slug: image-1x-2x-3x-srcset-resolution
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766407025782/fbe1d25e-71f5-4a36-bfc6-11e6886a056e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766407034086/205a6cca-dba5-4419-abc9-c0e1758ac9e9.png
tags: css3, css, html, images, html5, 2articles1week, resolution

---

為什麼我的圖片明明大小沒錯，在較好的螢幕上（例如 apple retina 螢幕）卻顯得糊糊的？

這些都是因為「像素密度 (Pixel Density) 」的緣故，我們在第 15 天的時候有稍微提過，只不過沒有深入探究，今天我們就來好好了解一下，並且學會 HTML 與 CSS 上的處理方法。

> 延伸閱讀：[#15 網頁使用的單位大解析：px、rem、em、%、vw、vh (dvh, lvh, svh)、vmin、vmax](https://ithelp.ithome.com.tw/articles/10332412)

---

> #### **↓ 今日學習重點 ↓**
> 
> * 了解向量圖、點陣圖是什麼？
>     
> * 了解像素密度 (Pixel Density) 的原理
>     
> * 使用 HTML `<img>srcset` 屬性處理圖片
>     
> * 使用 CSS `background-imageimage-set()` 處理圖片
>     
> * 使用 CSS `@media-resolution` 處理圖片
>     

---

## 一、向量圖 vs. 點陣圖

![向量圖 vs. 點陣圖](https://cdn.hashnode.com/res/hashnode/image/upload/v1705507214898/0701bdf8-97ce-469b-a4c0-da988afa9707.png align="center")

在開始優化圖片前，我們需要了解電腦中圖片檔案的基本知識。  
圖片檔案分為 2 種，分別為向量圖與點陣圖。

### 1\. 什麼是向量圖？

> 常見網頁檔案格式：`svg`  
> 繪圖軟體檔案格式：`esp`、`ai`

![向量圖](https://cdn.hashnode.com/res/hashnode/image/upload/v1705290036639/2902b638-bfb4-403b-89e3-f455d668e71a.png align="center")

向量圖片是由路徑組成，紀錄點與點之間的座標，如有曲線的話會使用貝茲曲線計算。在繪圖軟體中會有控制桿可以控制曲線的彎曲方式。

向量圖背後記錄的是各種點座標的數學運算，所以它放大縮小都不會失真，檔案大小通常也比較小，但缺點是比較難繪製出較細緻的筆觸或材質紋理等。

在網頁上，像 LOGO 與 icon 這種簡易的圖形通常都建議儲存為這種格式。

### 2\. 什麼是點陣圖？

> 常見網頁檔案格式：  
> `jpg (等同 jpeg)`、`bmp`、`png` (可透明)、`gif` (可透明，可含動畫)、`webp` (可透明，可含動畫)、`avif`

![點陣圖](https://cdn.hashnode.com/res/hashnode/image/upload/v1705507190130/7fd6bd1f-c8db-488a-8972-93021cbb7517.png align="center")

螢幕的顯示是由很多格子組合起來的，在早期的螢幕上，眼睛湊很近看都能看到一格一格的格子，1 像素 (pixel) 就代表螢幕上的一個格子。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705504112985/159d8bfb-7d25-4edb-aa01-174609dec497.gif align="center")

點陣圖片就是由像素組成，將圖片拉大就會看到許多由格子組成的色塊。照片或電腦繪圖因為有大量影像細節，難以用座標與數學運算紀錄，所以通常會儲存為點陣圖，使用許多像素色塊堆疊出整體樣貌。

點陣圖的缺點是當圖片的尺寸放大超過自己本身的大小時，會出現許多格子，明顯看到畫質不好。

> BUT！我們開頭說過：  
> 「明明大小沒錯，為何在較好的螢幕上（例如 apple retina 螢幕）卻顯得糊糊的？」
> 
> 接下來，我們要來了解螢幕上的「像素密度 (Pixel Density) 」，就能解決這個問題了。

---

## 二、像素密度 (Pixel Density) ：1x、2x 與 3x

隨著螢幕面板的科技發展，螢幕能顯示的畫面越來越好，除了顯色能力變好外，解析度也變高了。原本螢幕上的一個格子只能放 1 x 1 個像素（pixel），現在一個格子能夠放入 2 x 2 個，甚至是 3 x 3 個以上。

換言之，像素的密度變高了，所以呈現出來的畫面更細緻，舉個例子：

![像素密度 (Pixel Density) ：1x、2x 與 3x](https://cdn.hashnode.com/res/hashnode/image/upload/v1700533171924/9ff8b800-5e7d-43fa-9e3d-b87654184103.png align="center")

在 App 與網頁設計中，為了不同「像素密度」會準備不同的圖檔，讓高解析度裝置的使用者下載高解析度的圖片，而低解析度裝置的使用者下載低的就好，這樣可以讓下載速度快一點，達到最佳體驗。

這些圖檔通常稱之為 1x、2x、3x 的圖檔，1x、2x、3x 是 `dppx` 這個單位的簡寫。目前常見的裝置解析度是 2x，最高能到達 4x。

> 延伸閱讀：  
> [Resolution by iOS device — iOS Ref](https://iosref.com/res)  
> [重新認識 Pixel、DPI / PPI 以及像素密度 | INFOLINK Blog](https://blog.infolink.com.tw/2021/rediscover-pixel-dpi-ppi-and-pixel-density/)  
> [现在手机分辨率这么大，如何写响应式布局？ - 知乎](https://www.zhihu.com/question/35221839)

---

了解這點，我們就可以知道開頭的問題是為什麼發生了。

如果我在 2x 的螢幕上放了 1x 的圖，就會像下面這樣，顯得有點模糊，尤其是文字邊緣（不過這要使用 2x 以上的螢幕才看得出來）：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701839688544/366c1569-4687-4653-81a5-46bf11b7e13c.png align="center")

如果想要知道自己的螢幕解析度是多少，可以開開看下面網友做的 Code Pen DEMO 連結：

> 連結：[DPI check](https://codepen.io/pixelthing/pen/apweQB)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701840347442/9c830c56-ff13-4569-8969-1d8f5635c8c3.png align="center")

關於螢幕像素密度的相關單位 `ppi` 、 `dpi` 、 `dppx` 的換算關係如下：

> 1. `ppi`（Pixels Per Inch） = `dpi`（Dots Per Inch）
>     
>     * `ppi` 代表每英寸的「像素」數量。  
>         `ppi = pixels / inch (對角線)`
>         
>     * `dpi` 代表每英寸的「點」數量。  
>         在螢幕上「點」代表像素，所以等於 `ppi`，但是在印刷中由它的機械結構決定的。  
>         `dpi = ppi = pixels / inch (對角線)`
>         
> 2. `dppx`（Dots Per Pixel）
>     
>     * `dppx` 代表每 CSS 像素中包含的物理像素數量。  
>         `dppx = pixels / CSS pixel`
>         

如果覺得算數很麻煩，沒關係。  
在 CSS 中，我們只要知道 1x、2x、3x 的觀念，使用 `dppx` 這個單位就足夠了！

---

## 三、HTML/CSS 實作 DEMO

### 1\. HTML `<img>srcset`

使用 HTML 的 `<img>srcset` 屬性就能很輕易地依據使用者裝置切換對應像素密度的圖片，不同密度的圖片使用逗號隔開，語法如下：

```xml
<img srcset="1x圖檔連結 1x,
			 2x圖檔連結 2x,
			 3x圖檔連結 3x">
```

> DEMO：[1x vs. Current dppx: HTML srcset](https://codepen.io/im1010ioio/pen/GRzPqOm)
> 
> 我發現使用這種方式，圖片比較容易被瀏覽器快取住（瀏覽器為了讓讀取速度快一點，存下之前載過的圖片，不重新再拿一次圖片），所以如果你使用雙螢幕測試，直接來回切換螢幕可能不會馬上變化。

> 延伸閱讀：[\[教學\] 如何使用 img srcset 讓圖片在 RWD 網頁顯示適當解析度 - Shubo 的程式開發筆記](https://www.shubo.io/responsive-image/)

---

### 2\. CSS `background-image` 的 `image-set()`

還有一種方法，那就是 CSS 中 `background-image` 的 `image-set()` ，詳細語法如下：

```css
.img-set{
	background-image: image-set(
		url("1x圖檔連結") 1x,
		url("2x圖檔連結") 2x,
		url("3x圖檔連結") 3x);
}
```

> DEMO：[1x vs. Current dppx: CSS image-set()](https://codepen.io/im1010ioio/pen/wvNRWjm)

---

### 3\. CSS `@mediamin-resolution` / `max-resolution`

最後一種方式，是使用 CSS Media Queries 的新屬性：`min-resolution` 或 `max-resolution` ，語法如下：

```css
.img-set{
    @media screen and (min-resolution: 1x) {
        background-image: url("1x圖檔連結");
    }
    @media screen and (min-resolution: 2x) {
        background-image: url("2x圖檔連結");
    }
    @media screen and (min-resolution: 3x) {
        background-image: url("3x圖檔連結");
    }
}
```

> DEMO：[1x vs. Current dppx: CSS @media resolution](https://codepen.io/im1010ioio/pen/XWGMZOP)

Media Queries 的 `resolution` 屬性，除了使用 1x、2x、3x 作為單位，也可以使用 `dppx`、`dpi`、`dpcm` 作為單位。此外，除了運用在螢幕上，也可以運用在列印上。

> 延伸閱讀：[resolution - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/resolution)

> 另外，還有一個寫法是 `-webkit-device-pixel-ratio` ，它也可以達到一樣的效果，但是它並非標準寫法，MDN 建議還是使用 `resolution` 的寫法。
> 
> 延伸閱讀：[\-webkit-device-pixel-ratio - CSS：級聯樣式表 |MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/-webkit-device-pixel-ratio)

---

## 四、DEBUG

### 1\. 使用 JS 取得像素密度 (Pixel Density)

如果想要知道自己的螢幕解析度是多少，還可以使用 JS 取得當前裝置的 `dppx`，語法如下：

```javascript
window.devicePixelRatio;
```

> 延伸閱讀：[Window: devicePixelRatio property - Web APIs](https://developer.mozilla.org/en-US/docs/Web/API/Window/devicePixelRatio)

最快的實測方式，就是打開瀏覽器的開發者模式，在 console 面板把這行打上去，以 Chrome 為例：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705508054760/f29ff35e-e647-4a2d-a9bc-792c772a4bca.png align="center")

---

### 2\. 使用開發者工具查看實際下載的圖片

如果想要知道網頁實際下載的是哪一張圖片，可以打開瀏覽器的開發者模式，切到 Network 頁籤，然後清除紀錄，再重新整理頁面（在重整按鈕上按右鍵可清除快取），觀察總共載入了哪些東西。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705508887324/d650e317-c81f-4582-a71a-8b2b58b53cc5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705508892298/6ab683e2-c331-4cf9-9ba1-8998b900a4e3.png align="center")

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")