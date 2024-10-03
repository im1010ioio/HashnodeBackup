---
title: "#47 一次搞懂 CSS 各種混合模式：mix-blend-mode/ background-blend-mode"
datePublished: Thu Oct 03 2024 09:45:23 GMT+0000 (Coordinated Universal Time)
cuid: cm1t41zte000c0ajh2amfeghi
slug: css-mix-blend-mode
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1727948080406/44faa9a4-ed4d-409f-a099-eb07abc525c8.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1727948703951/173b6a8e-6640-45ce-a07e-46ae556603a0.png
tags: css3, css, 2articles1week, mix-blend-mode, background-blend-mode

---

> #### **↓ 今日學習重點 ↓**
> 
> * 了解 CSS 各種混合模式
>     
> * 將混合模式應用在 `mix-blend-mode` 和 `background-blend-mode` 上
>     

`mix-blend-mode` 和 `background-blend-mode` 能讓元素或背景顏色和它們背後的元素或背景進行混合，從而產生不同的視覺效果。這些效果類似於 Photoshop 等圖像編輯軟件中的「混合模式」。

如果搭配 sticky 效果或是視差捲動，會非常酷炫喔！例如「板塊設計」的官網，在文字上使用了 `mix-blend-mode: difference;`，讓文字跟背景的石頭圖片產生相反顏色的效果：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727938493149/16964be0-059e-4422-aac6-add9d72406aa.gif align="center")

> 連結：[版塊 Block Studio](https://blockstudio.tw/)

---

---

## 一、 `mix-blend-mode`

`mix-blend-mode` 用於設定一個元素如何與其父元素或背景中的其他元素進行混合。常見的應用包括圖片和文字在背景上的混合，讓內容與背景色彩產生有趣的視覺效果。

### 基本語法

```css
div {
    mix-blend-mode: difference;
}
```

我知道光用說的很難想像，讓我們用範例來理解吧！

---

---

### 1\. 預設

#### 1.1 `normal` **正常**

![CSS mix-blend-mode normal](https://cdn.hashnode.com/res/hashnode/image/upload/v1727935175623/4993fa46-6f73-4a11-a740-6e71f8f329f6.png align="center")

---

---

### 2\. 深色效果

以下這一系列的效果會讓顏色變暗，而大多白色背景會消失。

#### 2.1 `darken` **變暗**

顯示上下層較暗的部分。

下面的範例，由於上層的圖片顏色都比下層的圖片淺，所以最後只顯示了下層的圖片：

![CSS mix-blend-mode darken](https://cdn.hashnode.com/res/hashnode/image/upload/v1727935339525/9cf23b72-05a8-4136-9355-60b8e1d50b73.png align="center")

---

#### 2.2 `multiply` **色彩增值** （⭐️常用）

讓兩個圖層中的暗色混合在一起，而白色部分則會消失。

![CSS mix-blend-mode multiply](https://cdn.hashnode.com/res/hashnode/image/upload/v1727935426579/9fdf7c85-d6c5-4221-88a2-a3b1feacc54f.png align="center")

---

#### 2.3 `plus-darker`

效果比「`multiply` 色彩增值」與「`color-burn` 加深顏色」還要深。  
（這是 CSS 中新增的混合模式，Photoshop 中沒有）

![CSS mix-blend-mode plus-darker](https://cdn.hashnode.com/res/hashnode/image/upload/v1727935494722/99237bc4-321d-4e82-b703-971c405e8d69.png align="center")

---

#### 2.4 `color-burn` **加深顏色**

效果比「`multiply` 色彩增值」還要深。

![CSS mix-blend-mode color-burn](https://cdn.hashnode.com/res/hashnode/image/upload/v1727935574466/ff60700d-c210-4f87-bc02-2202770a1cb0.png align="center")

---

#### 2.5 使用情境 & DEMO

最常的使用情境是：

* 讓圖片上加一層淺色材質圖片，讓結果變得有紋理質感；
    
* 在圖片上加上文字或手繪圖案，「`multiply` 色彩增值」可以讓文字或手繪圖案看起來像是印在、畫在上面，例如：
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727939454617/7608dbb7-34cb-4e3b-be56-2fc3a0d7faab.png align="center")
    
    > DEMO: [CSS mix-blend-mode multiply](https://codepen.io/im1010ioio/pen/ZEgbzzR)
    

---

---

### 3\. 明亮效果

以下這一系列的效果會讓顏色變亮，而大多黑色背景會消失。

#### 3.1 `lighten` **變亮**

上下層顯示較亮的部分。

![CSS mix-blend-mode lighten](https://cdn.hashnode.com/res/hashnode/image/upload/v1727935734342/95700640-a5be-461b-a803-186b7999f5fb.png align="center")

---

#### 3.2 `screen` **濾色**（⭐️常用）

增加重疊區域的亮度。黑色部分會變得透明，而白色部分會保留原色。

![CSS mix-blend-mode screen](https://cdn.hashnode.com/res/hashnode/image/upload/v1727935768021/95823429-6c06-4c75-8d2e-74420c01ec17.png align="center")

---

#### 3.3 `plus-lighter`

在重疊亮度時，也考慮了透明度。  
（這是 CSS 中新增的混合模式，Photoshop 中沒有）

![CSS mix-blend-mode plus-lighter](https://cdn.hashnode.com/res/hashnode/image/upload/v1727935790884/b29744d9-7302-40d1-9cfb-0793ba5d73fc.png align="center")

---

#### 3.4 `color-dodge` **加亮顏色**

效果比「`screen` 濾色」還亮，對比度也更高，更有衝擊力！

![CSS mix-blend-mode color-dodge](https://cdn.hashnode.com/res/hashnode/image/upload/v1727935807052/c9134297-4194-4f97-9258-4d93472831e7.png align="center")

---

#### 3.5 使用情境 & DEMO

最常的使用情境是：使用黑色背景的特效素材（如：光束、雨），疊在圖片、影片上方。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727943878166/a3345db0-a642-4deb-b9ee-ffcff73a0925.gif align="center")

> DEMO: [CSS mix-blend-mode plus-lighter](https://codepen.io/im1010ioio/pen/Exqjqpp)

---

---

### 4\. 明暗效果兼具

以下這一系列的效果明暗顏色都保留，是重疊效果：

#### 4.1 `overlay` **覆蓋**

接近於「`multiply` 色彩增值」和「`screen` 濾色」，但都沒有去除白色與黑色的部分，並且增加對比度。

![CSS mix-blend-mode overlay](https://cdn.hashnode.com/res/hashnode/image/upload/v1727936099351/a122385b-6cd1-44ab-acff-a5aab164c149.png align="center")

---

#### 4.2 `soft-light` **柔光**

明亮的部分變得更亮，黑暗區域變暗。

![CSS mix-blend-mode soft-light](https://cdn.hashnode.com/res/hashnode/image/upload/v1727936104220/8079890f-96f5-4048-9279-fbdff6c68992.png align="center")

---

#### 4.3 `hard-light` **實光**

效果比「`soft-light` 柔光」更強。

![CSS mix-blend-mode hard-light](https://cdn.hashnode.com/res/hashnode/image/upload/v1727936107897/c1bbc297-8e24-4343-a7e7-22fc358972a3.png align="center")

---

---

### 5\. 顏色差異的效果

以下這一系列的效果都是強調上下層的不同之處：

#### 5.1 `difference` **差異化**（⭐️常用）

強調與背景的差異之處，能有效提升辨識度。如果文字或其他元素需要同時出現在黑白兩種背景間，而且還要清楚辨識時，這會很好用！  
（如同我們開頭提到板塊設計官網的例子）

![CSS mix-blend-mode difference](https://cdn.hashnode.com/res/hashnode/image/upload/v1727936554931/dcd05253-8d04-42f4-af84-25f24a9c3401.png align="center")

---

#### 5.2 `exclusion` **排除**

效果對比度比「`difference` 差異化」弱一點。

![CSS mix-blend-mode exlusion](https://cdn.hashnode.com/res/hashnode/image/upload/v1727936559937/677c6f1c-2d7d-4259-af50-fa61eba69e47.png align="center")

---

---

### 6\. HSL 顏色混合效果

以下這一系列的效果都是在 HSL 色彩空間中合成顏色，如同使用濾鏡調色：

#### 6.1 `hue` **色相**

保留下層的明亮度（L）和飽和度（S），但使用**上層的色相（H）的顏色**。

![CSS mix-blend-mode hue](https://cdn.hashnode.com/res/hashnode/image/upload/v1727936756209/fd6ae6e6-b0f4-46b5-a0f8-a5257e147684.png align="center")

---

#### 6.2 `saturation` **飽和度**

保留下層的明亮度（L）和色相（H），但使用**上層的飽和度（S）的顏色**。

![CSS mix-blend-mode saturation](https://cdn.hashnode.com/res/hashnode/image/upload/v1727936767323/b65673da-bd45-43f0-b598-f643ce2de352.png align="center")

---

#### 6.3 `color` **顏色**

保留下層的明亮度 （L），但使用**上層的飽和度（S）和色相（H）的顏色**。

![CSS mix-blend-mode color](https://cdn.hashnode.com/res/hashnode/image/upload/v1727936772035/5b42dd28-d7c4-4a7f-800b-4048f214a3c4.png align="center")

---

#### 6.4 `luminosity` **明度**

保留下層的飽和度（S）和色相（H），但使用**上層的明亮度（L）的顏色**。

![CSS mix-blend-mode lumonosity](https://cdn.hashnode.com/res/hashnode/image/upload/v1727936856334/06d1086d-932c-441a-a76d-9c308dce332f.png align="center")

---

---

## 二、`background-blend-mode`

`background-blend-mode` 是當你使用多重背景（背景圖片、顏色、漸層等）時，可以控制它們的混合模式。使用方法與可用的數值基本上與 `mix-blend-mode` 基本上一樣。

### 基本語法

```css
div {
    background-blend-mode: difference;
}
```

### DEMO

以下範例我們也是用「`multiply` 色彩增值」，做出了顏料畫在牆上的效果，只不過這次是使用 `background` 屬性：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727946959760/3d98acce-5266-48e9-a263-6e15d4b580b1.png align="center")

> DEMO: [CSS background-blend-mode](https://codepen.io/im1010ioio/pen/KKOzzmq)

---

## 三、用 Figma 模擬效果

如果覺得以上解說還是太抽象，很難想像會怎麼樣呈現結果，建議大家用繪圖軟體模擬看看，可以使用 Figma，因為 Figma 這套繪圖軟體是基於網頁技術製作的，而且裡面所有的混合模式都有。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727937894912/e127932a-c1bd-4bee-b881-df902134b899.png align="center")

> 連結：[Figma: The Collaborative Interface Design Tool](https://www.figma.com/)

### 操作步驟

1. 進到 Figma 後新建一個「New design file」。
    
2. 隨意在畫面上建立一個白色背景的 Frame：
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727947694390/fd8985b2-1313-496b-bc88-34361bf97452.png align="center")
    
3. 把圖片拖曳進去相疊在一起，選取要改變混合模式的圖片，在右邊可以改變 Layer 的模式，就可以試試看各種不同混合模式的效果了：
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727947718254/53645286-9b1a-4fe4-8a4e-a606c4270811.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727937739104/6794a787-54ee-4736-9381-2da9d44d84bf.gif align="center")
    

---

這些 CSS 屬性可以帶來許多創意上的可能性，讓網頁設計更加豐富和視覺化。如果你想更深入學習這些效果，可以逐步嘗試各種混合模式，並觀察它們在不同情境下的效果。

> 延伸閱讀：
> 
> * [Adobe Photoshop 中的混合模式](https://helpx.adobe.com/tw/photoshop/using/blending-modes.html)
>     
> * [動手玩 CSS Blend Mode - 根本 Photoshop 的圖層效果](https://www.casper.tw/css/2016/01/10/css-blend-mode/)
>     
> * [深入探索CSS属性mix-blend-mode：创意叠加效果的艺术之旅](https://blog.csdn.net/weixin_68127493/article/details/137744165)
>     
> * [CSSのブレンドモードが素敵！ mix-blend-modeを使いこなそう](https://ics.media/entry/7258/#%E6%9A%97%E3%81%84%E5%8A%B9%E6%9E%9C%E3%81%8C%E5%BE%97%E3%82%89%E3%82%8C%E3%82%8Bcss%E3%83%96%E3%83%AC%E3%83%B3%E3%83%89%E3%83%A2%E3%83%BC%E3%83%89)
>     

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")