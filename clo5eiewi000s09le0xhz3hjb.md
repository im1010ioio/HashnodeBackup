---
title: "#31 CSS 顏色設定：基本的 hex、rgb()、cmyk()、hsl()、hsb() 、hwb() 與明日之星的 lch()、oklch()"
datePublished: Wed Oct 25 2023 06:55:26 GMT+0000 (Coordinated Universal Time)
cuid: clo5eiewi000s09le0xhz3hjb
slug: css-colors-hex-rgb-hsl-lch-oklch
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698128232494/47fae320-26bf-4689-a069-4b753053bacf.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1698166362907/344301fb-b0e1-4707-bded-730493747742.png
tags: css3, css, color, lch, oklch

---

> #### **↓ 今日學習重點 ↓**
> 
> * 了解 hex、rgb()、cmyk()、hsl()、hsb()
>     
> * 了解廣色域是什麼
>     
> * 了解 lch()、oklch() 與他們的優勢
>     

顏色在之前的範例中雖然有用到，但是一直沒有深入講解。

今天，我們就要來深入了解各種 CSS 設定顏色的原理及方式，我們要了解基本的 `hex`、`rgb()`、`cmyk()`、`hsl()`、`hsb()`、`hwb()`，與新推出、讓設定顏色更廣、更直覺、更符合人眼的 `lch()`、`oklch()`。

---

## 一、CSS Color Names（⭐️常用）

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698138008645/c2c6e214-a908-453b-85a4-dba47a278e63.png align="center")

CSS 中有 160 幾種顏色名稱，可以直接在 CSS 中指定 `white`、`black`、`red`、`blue`、`green` 等等，讓人可以很直覺設定基本的顏色。

```css
p {
    color: blue;
    background: white;
}
```

> 詳細所有顏色請參考：
> 
> * [&lt;named-color&gt; - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/named-color)
>     
> * [CSS Colors](https://www.w3schools.com/cssref/css_colors.php)
>     

---

## 二、RGB

色光是由三原色組成，也就是 R 紅色、G 綠色、B 藍色這三種，有了這三種顏色我們可以組合出各種顏色，而他們合在一起最後就是變成白色光。

在 CSS 中，我們可以透過 `HEX` 與 `rgb()` 兩種寫法來指定顏色，兩者都是使用 16 進位來計算 RGB 三種顏色。由於這是最早出現指定顏色的方法，所以非常常見。

### 1\. HEX（⭐️常用）

![CSS HEX Color](https://cdn.hashnode.com/res/hashnode/image/upload/v1698126670312/169aaf81-1af1-413d-8ca5-5630f22e5cc0.png align="center")

CSS HEX 寫法是使用升記號 `#` 寫在最開頭，接續用 6 個英數代表 RGB 三種顏色，每個數字由 0 到 f（共 16 個），代表了該色光的濃淡，0 是最淡，最淡時是沒有光，就是黑色；而 f 是最亮。

也就是說，`#000000` 就是指都沒有光，是黑色；而 `#ffffff` 就會是白色。另外，這種寫法也可以簡寫成 3 個英數，例如：`#000` 或 `#fff`。

如果要使用透明度，也是使用一樣的方式在後面再加 2 個英數，0 是透明，而 f 是不透明。

---

### 2\. RGB（⭐️常用）

![CSS RGB](https://cdn.hashnode.com/res/hashnode/image/upload/v1698163638635/aae4ddb7-4390-4875-a998-cf3c1f2c2ea3.png align="center")

CSS 中的 `rgb()` 或 `rgba()` 寫法，與 HEX 寫法概念相似，不過它將 RGB 分別變為單一數字，一樣也是使用 16 進位，一個值的濃淡是由 0 到 255（因為 16x16=256 個數值）。

這種寫法有兩種：

* 新的寫法是直接寫三個顏色的數值，無需逗號，透明度則是使用斜線 `/` 隔開，透明度使用百分比表示；
    
* 而舊的寫法是使用逗號隔開，如需透明度則要使用 `rgba()`，透明度使用小數點表示。
    

---

## 三、CMYK

![CSS CMYK](https://cdn.hashnode.com/res/hashnode/image/upload/v1698168923825/84b2ef12-b416-4b53-81df-0c6109157121.png align="center")

前面說到色光是由三原色組成，而在與之相對的印刷中，常見的是四色印刷，由四種顏色組成各種顏色：C 青色、M 洋紅、Y 黃色、K 黑色。理論上，前三種顏色 CMY 合在一起就會變成黑色。

雖然在網頁中使用的情境很少，但是在 CSS 中也可以設定 CMYK，使用百分比設定四種顏色的比例。

補個印刷小知識，`cmyk(0, 0, 0, 100%)` 會優於 `cmyk(100%, 100%, 100%, 0)`，印出來不僅省墨水，成色也比較不會濁，所以能使用 k 代表深色就使用 k。此外，為防止印刷機器不夠精準，數字建議為整數 0 或 5 結尾，成色會比較穩定，也比較不會濁。

再來，因為 CMYK 與 RGB 所能表現的顏色範圍不同，所以有些顏色四色印刷是印不出來的，尤其是螢光色，這時候可能會需要使用特殊色印刷。詳細的色域比較請參考下圖：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698073541444/b8fd0104-f77b-4c73-a0bb-1b96630841d0.png align="center")

---

## 四、由色相選擇顏色

開頭我們所介紹的 HEX 與 RGB，是針對螢幕硬體所設計的選色方式，對於人類其實並不是很直覺，我們很難在腦內中想像如何混合色光。於是，在數位世界中發展出使用「色相環 Hue」選色的選色方式，如「HSL 和 HSB (又稱HSV) 色彩空間」與「HWB 色彩空間」等。

> 延伸閱讀：  
> [HSL和HSV色彩空間 - 維基百科](https://zh.wikipedia.org/zh-tw/HSL%E5%92%8CHSV%E8%89%B2%E5%BD%A9%E7%A9%BA%E9%97%B4)  
> [HWB色彩空間 - 維基百科](https://zh.wikipedia.org/wiki/HWB%E8%89%B2%E5%BD%A9%E7%A9%BA%E9%97%B4)

### 1\. HSL 與 HSB (又稱HSV)

![HSL 與 HSB (又稱HSV)](https://cdn.hashnode.com/res/hashnode/image/upload/v1698169004281/919626f3-97df-4dbe-b6c8-db2098547235.png align="center")

HSL 與 HSB 將顏色分為三種數值：

1. **色相 Hue**：由 0 度到 360 度的彩虹圓圈，起始都是紅色。
    
2. **飽和度 Saturation**（又稱彩度）：由灰色到彩色，數值由 0% 到 100%。
    
3. **明度 Lightness/Brightness**：添加白色或是黑色，控制顏色的明暗，數值由 0% 到 100%。
    

CSS 中 HSL 和 HSB 的寫法，其實與 RGB 的設定方式大同小異，也是有新舊兩種寫法，區別在於有無逗號，與對於透明度的寫法。

#### (1) HSL（⭐️常用）

在 HSL 中，將明度（L，Lightness）的 0% 設為黑色，而 100% 則是白色，也就是說在明度上色彩最鮮豔處在 50% 的位置。

這樣添加黑白的方式很直覺，所以是滿多人推薦的選色方式。

#### (2) HSB（又稱 HSV）

在 HSB 中，將明度（B，Brightness）的 0% 設為黑色，而 100% 則是色彩最鮮豔處。

### 2\. HWB

![HWB](https://cdn.hashnode.com/res/hashnode/image/upload/v1698169867104/3e8029f5-025d-41b2-90b8-a42f25e2019a.png align="center")

HWB 雖然也是由色相出發，但是它沒有飽和度的概念，它僅用添加黑白來調整色彩，所以它有三種數值：

1. **色相 Hue**：由 0 度到 360 度的彩虹圓圈，起始都是紅色。
    
2. **白色 White**：由白色到彩色，數值由 0% 到 100%。
    
3. **黑色 Black**：由白色到彩色，數值由 0% 到 100%。
    

詳細的變化，可以玩玩看以下別人做的 Codepen Demo：

> [HWB color explorer](https://codepen.io/smashingmag/pen/xxLmOgV)

這樣添加黑白的方式雖然在明度方面很直覺，但是在調整飽和度時有些不便。在只調整單色調的明暗時或許可以考慮。而在繪圖軟體中，無法使用這種方式設定顏色，也沒有套件可以使用，所以與設計師合作時無法直接使用。整體來說有一點雞肋。

---

## 五、由色相選擇 + 廣色域的 LCH/OKLCH

![CSS LCH/OKLCH](https://cdn.hashnode.com/res/hashnode/image/upload/v1698179694864/66e4148b-313f-464a-bcac-b82b87f51042.png align="center")

LCH/OKLCH 是一種更符合人類感知的顏色表示方式。此外，LCH/OKLCH 還可以設定更寬廣的顏色範圍。

> 由於為了貼近人眼感知與支援廣色域，所以它們針對這三種變數做了很大的調整，並非單純線性結構，大家可以使用以下小工具玩玩看，就能明白了（詳細概念與數值設定，我們稍後會再解釋）：
> 
> 小工具：[LCH/OKLCH Color Picker & Converter](https://oklch.com/)

LCH/OKLCH 目前支援度已 100%，但是而在繪圖軟體中，還無法直接使用這種方式設定顏色，可以使用一些套件模擬，如：Figma 中的 [LCH](https://www.figma.com/community/plugin/969496279507778512)、[OkColor](https://www.figma.com/community/plugin/1173638098109123591)、[Perceptual Color](https://www.figma.com/community/plugin/1266828922235523696/perceptual-color)、[Chromatic Figma](https://www.figma.com/community/plugin/759433498184507623/) 等，但是它是使用一些數學運算 RGB 去模擬結果，本質依然沒有支援。

### 1\. 色相變化時，明度的修正

![CSS HLS vs. LCH vs. OKLCH](https://cdn.hashnode.com/res/hashnode/image/upload/v1701275453954/d5a851c7-88dc-4b1f-81f1-0bc8ae7766ae.png align="center")

舊有 RGB 中的 `hex`、`rgb()`、`hsl()`、`hsb()` 、`hwb()` 是為了系統運算而生，所以存在著不符合人眼視覺的問題：相同明度但是感覺起來不一樣亮。在 LCH/OKLCH 中修正了這個問題，如上圖所示。

如此一來，當我們需要改變色相時，就不必擔心顏色對比度會跑掉，例如：更改按鈕顏色，卻因為改為黃色調而看不清楚文字。在設計時，也能更輕鬆掌握色彩，建立色彩系統，真希望繪圖軟體盡快支援。

#### 可修正漸層的灰色死亡地帶

![CSS HLS, LCH, OKLCH 漸層比較 Color Space in Linear Gradient: sRGB vs. LCH vs. OKLCH](https://cdn.hashnode.com/res/hashnode/image/upload/v1718816705522/d94cc231-5c83-404f-8b85-7d1d2d8bd66b.png align="center")

延伸上一點，當我們在傳統 sRGB 描繪漸層時，由於不同色相間的視覺上的明度不一致，容易造成漸層顏色混濁。現在，使用 LCH/OKLCH 的色彩空間就可避免這個狀況，因為當色相切換時，明度的感知一致，飽和度也保留著，讓漸層能夠順順地過去。

> 延伸閱讀：  
> [設計女子艾瑪 - 為什麼我的漸層色髒髒的？運用 LCH 色彩升級你的漸層色](https://www.instagram.com/p/CvM9Ycgv9y2/)  
> [Better Gradients | Dan Hollick](https://typefully.com/DanHollick/better-gradients-ViH6Bu2kDRBJ)  
> [Non-Boring Gradients - A non linear CSS gradient generator](https://non-boring-gradients.netlify.app/)

#### 使用 CSS 設定漸層色彩空間（Interpolation color space）

這邊我們使用的是在 `background` 中的漸層色上加上指定的色彩空間，加上後瀏覽器會依據該色彩空間的方式混合顏色：

> DEMO 連結：[Color Space in Linear Gradient: sRGB vs. LCH vs. OKLCH](https://codepen.io/im1010ioio/pen/MWLwgMy)

```css
div {
    background: linear-gradient(135deg in lch, #b920f2 15%, #00FFD1 85%);
}
```

當然色彩空間不只這幾種可以設定，大家也可以去研究一下漸層的各種面貌：

> DEMO：[Gradient Color Spaces Exploration](https://codepen.io/argyleink/pen/OJObWEW)  
> 來源：[Color Spaces for More Interesting Gradients | CSS-Tricks](https://css-tricks.com/color-spaces-for-more-interesting-css-gradients/)

### 2\. 廣色域，接近人眼所能見的所有顏色

前面我們所介紹的顏色設定方式，除了 CMYK 外，其餘都是屬於螢幕中 sRGB 的色域，但是人眼能看到的色彩，比 sRGB 還要大上許多，sRGB 僅僅是人眼可見色彩的 35% 而已。

隨著液晶螢幕技術的進步，螢幕可顯示的顏色已大於 sRGB 的範圍，目前常見的背光源技術是「藍光 LED 搭配 RG 螢光粉」，它能凸顯分別代表長、中、短波長的RGB光譜分布，讓各頻帶能量更加集中，提高顏色的純度讓色域往外擴張，而這樣的技術稱為廣色域（wide color gamut，WCG），詳細請參考下圖：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698075985955/5cb5c82c-a18f-4510-98da-537a0d2539c6.png align="center")

> 延伸閱讀：[什麼是廣色域｜BenQ 台灣](https://www.benq.com/zh-tw/knowledge-center/technology/what-is-wide-color-gamut-tv.html)

例如，由 Apple 推出的 Display P3 色域，比起傳統 sRGB 的表現效果就鮮明許多：

![sRGB vs. Display P3](https://cdn.hashnode.com/res/hashnode/image/upload/v1698114882108/576ea323-8723-4471-9aca-63ca546ca945.jpeg align="center")

> 圖片來源 & 延伸閱讀：[Get Started with Display P3 - WWDC17 - Videos - Apple Developer](https://developer.apple.com/videos/play/wwdc2017/821/)

#### LCH/OKLCH 使用的色彩空間

LCH/OKLCH 使用的色彩空間是 CIELAB，是目前最大的色彩空間之一，它甚至比 Apple 的 Display P3 大一點。

> 延伸閱讀：[CIELAB色彩空間 - 維基百科](https://zh.wikipedia.org/zh-tw/CIELAB%E8%89%B2%E5%BD%A9%E7%A9%BA%E9%97%B4)

#### 廣色域之於網頁設計

這一點優勢雖然是項突破，但是在一般網頁設計上其實不是必須（尤其是面對只需要改背景、按鈕或文字顏色等基本需求時），因為網頁必須要向下相容各種用戶的螢幕，所以 sRGB 就很夠用了。

不過，如果我們是要使用 CSS 或程式創作圖像，如酷炫的互動設計、未來的生成式藝術（Generative Art ）等等，或許就很有幫助了，可以增加更多顏色變化的可能性。當使用者螢幕好時，可以盡可能呈現更好的色彩。

> 註：目前 CSS 率先支援了廣色域，但是 p5.js 還沒有，所以創作生成式藝術可能還要等等，詳情請參考：[Support for new high definition color spaces. · Issue #6190 · processing/p5.js](https://github.com/processing/p5.js/issues/6190)。（2023/11）

#### 如果使用者的螢幕無法顯示廣色域的顏色怎麼辦？

使用廣色域的顏色時，如果使用者的螢幕不夠好，無法顯示超出的色域，瀏覽器會尋找最接近的顏色顯示，不用擔心顏色失效。

大家可以試看看一下的 DEMO，兩者皆是同色相的水藍色，飽和度與明度皆最高的顏色：

![oklch vs. hex color ](https://cdn.hashnode.com/res/hashnode/image/upload/v1704949523401/2f1d90c7-18fc-4ed0-ac18-691d1a4c2976.png align="center")

> DEMO：[oklch vs. hex color](https://codepen.io/im1010ioio/pen/Exrjygv)

### 3\. LCH

![CSS LCH](https://cdn.hashnode.com/res/hashnode/image/upload/v1698206031984/51790654-90d6-478f-bf6a-cda57543de70.png align="center")

LCH 使用以下三種數值，基本上與 HSL 很相似：

1. **明度 Lightness**：添加白色與黑色，控制顏色的明暗，  
    由黑至白，數值將由 0% 到 100% 變化。
    
2. **色度 Chroma**：色彩的純度，與飽和度一樣的概念。  
    此處 0% 對應的數值為 0，100% 對應數值為 150。  
    最小值為 0，最大值理論上無上限（但實際不超過 230）。
    
3. **色相 Hue**：由 0 度到 360 度的彩虹圓圈，起始都是紅色（數值超過 360 就是第二圈，例如：數值 1 的色相等同於 361 的色相）。
    

如上圖所示，在 Chrome 的開發者模式中選色時，會標示一條 sRGB 的線，於這條線右側就是屬於廣色域的顏色。

> 延伸閱讀：[lch() - CSS：层叠样式表 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color_value/lch)

---

### 4\. OKLCH（⭐️ 會是明日之星嗎？）

![CSS OKLCH](https://cdn.hashnode.com/res/hashnode/image/upload/v1698212636689/5ef86451-4814-4828-988b-8f3c7b60aa7b.png align="center")

OKLCH 和 LCH 基本上一樣，只有**明度 Lightness**與**色度 Chroma 的地方不一樣**：

1. **明度 Lightness**：添加白色與黑色，控制顏色的明暗，  
    由黑至白，數值將由 0 到 1 變化。
    
2. **色度 Chroma**：色彩的純度，與飽和度一樣的概念。  
    此處 0% 對應的數值為 0，100% 對應數值為 0.4。  
    最小值為 0，最大值理論上無上限（但實際上不超過 0.5）。
    
3. **色相 Hue**：由 0 度到 360 度的彩虹圓圈，起始都是紅色（數值超過 360 就是第二圈，例如：數值 1 的色相等同於 361 的色相）。
    

#### OKLCH 改善了 LCH 的致命傷

LCH 雖已改善了 RGB 色相變化時的感知明度，但是他仍有致命缺點：就是當色相 Hue 介於 270 至 330（大約是藍色與紫色區間），當明度 Lightness 有所改變時，他的色相會有所偏移。以下面的例子來說，LCH 在加亮時，從藍色調偏移到了紫色調：

![CSS HLS vs. LCH vs. OKLCH](https://cdn.hashnode.com/res/hashnode/image/upload/v1698126842682/eb41f1c3-5966-4f03-b711-ba5c5a5c4462.png align="center")

色相偏移在為品牌建立色彩系統時，會造成問題，所以與 LCH 相比，建議大家使用 OKLCH。

以這個例子來說，在明度變化時，HSL 雖能夠維持同色相但是飽和度會突然變高；LCH 雖然飽和度穩定變化，但是色相偏移；而 OKLCH 幾乎沒有什麼缺點，它正是為了修正這個問題而誕生的，OKLCH 能完美地保持明度與色相的合理變化，非常值得被設計師與前端工程師使用。

> 這邊所謂的色彩系統，就是設計師為品牌定義好的一整套色彩計畫，通常被包含在 VIS 視覺識別系統設計中，例如：
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698215470829/c3b5f065-3463-4e0f-9a2e-8844e61bdf9c.png align="center")
> 
> 範例：[❖ Ultimate color palette system – Untitled UI](https://www.figma.com/community/file/1029506782158027808/ultimate-color-palette-system-untitled-ui)

大家可以去試試使用 OKLCH 調色喔！它的瀏覽器已經 100% 支援了。（真希望繪圖軟體也能夠盡快支援）

除了使用 OKLCH 調色，CSS 還新增了 `color-mix()`，可以快速建立起一整套顏色，我們將在下一篇解說。

> 延伸閱讀：  
> [oklch() - CSS：层叠样式表 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color_value/oklch)  
> [LCH vs OKLCH: what is the difference? | Atmos](https://atmos.style/blog/lch-vs-oklch)
> 
> 這篇文章有許多神奇的進階應用：  
> [OKLCH in CSS: why we moved from RGB and HSL—Martian Chronicles, Evil Martians’ team blog](https://evilmartians.com/chronicles/oklch-in-css-why-quit-rgb-hsl)

---

色彩的背後是一堆色彩 3D 空間和數學運算，研究了後我也還是不太懂它們的細節、座標是如何運算的，但是我們只要掌握運作原理，就能夠在適合的情景使用了。

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")