---
title: "#55 純 Css 照片淡入淡出輪播動畫"
datePublished: Wed Aug 13 2025 10:51:52 GMT+0000 (Coordinated Universal Time)
cuid: cme9uoz5m001002l4eyt69tzx
slug: css-images-slider-fade-effects
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766491110242/7c951e63-df34-4423-b95f-696f72d5f886.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766491118115/829cba03-cb5c-410f-8234-0bbe40ed0b6c.png
tags: css3, css, css-animation, image-slider

---

今天要來教大家如何使用 CSS Animation 製作簡單的純 CSS 照片淡入淡出輪播動畫。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728141340792/d1820a41-02e2-4a71-bd7b-b7394fd8b016.gif align="center")

> DEMO: [Pure CSS images slider - fade effects](https://codepen.io/im1010ioio/pen/ZEgOGxa)

只不過這個方法有個缺點，在一開始張數與秒數就要固定，比較建議用在簡易固定的靜態網頁上；如果圖片數量為動態產生，不固定數量，還是建議使用 JS 寫喔！

---

## 一、製作照片相框的容器

首先我們需要製作裝了許多照片的容器，使用絕對定位固定住：

```xml
<div class="img-screen">
    <img src="photo1.jpg" alt="photo 1">
    <img src="photo2.jpg" alt="photo 2">
    <img src="photo3.jpg" alt="photo 3">
    <img src="photo4.jpg" alt="photo 4">
    <img src="photo5.jpg" alt="photo 5">
    <img src="photo6.jpg" alt="photo 6">
</div>
```

```css
.img-screen {
    position: relative;
    width: 80vw;
    aspect-ratio: 5 / 3;
    overflow: hidden;
    margin: auto;
    > img{
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        object-fit: cover;
        z-index: 1;
        opacity: 0;
    }
}
```

---

## 二、設定照片出現與淡出入的時間

再來就是要決定照片出現與淡出入的時間，我們先用 1 秒作為淡入淡出的時間，3 秒為照片出現的時間，然後前一張圖片與下一張圖片的淡入淡出的時間會重疊：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728140973703/d40c711f-3f01-4157-892b-7fca5f966b27.png align="center")

所以如果照片要放 6 張，加上頭尾淡入淡出，總時長就會是 25 秒。  
只不過，因為我們希望最後的圖片淡出要與開頭圖片的淡入重疊，所以減掉最後淡出的秒數，所以其實**動畫總時長應為 24 秒**。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728140977316/7fc057bc-2183-4a44-872d-dc9b622fca3a.png align="center")

接著，我們要找出一張圖片出現、消失在總時長內的時機百分比，有了這個就能寫出動畫的 `@keyframes` 了，以這個例子來說：

* 照片由 0 - 1/24 時淡入
    
* 1/24 - 4/24 時完整出現
    
* 4/24 - 5/24 時淡出
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728140979986/898d74ec-0510-4387-9283-b2e5eebed260.png align="center")

```css
@keyframes slide {
    0% {
        opacity: 0;
    }
    4.166666% {
        opacity: 1;
    }
    16% {
        opacity: 1;
    }
    20.833333% {
        opacity: 0;
    }
}
```

不過，以上的 CSS 我們還可以再精簡一下，把相同的內容使用逗點寫在一起：

```css
@keyframes slide {
    0%, 20.833333% {
        opacity: 0;
    }
    4.166666%, 16% {
        opacity: 1;
    }
}
```

---

## 三、設定動畫

然後，我們就可以把動畫套上去囉！這邊有兩個重點：

* 因為我們希望照片時無限重複輪播，所以 `animation-iteration-count` 設為 `infinite`；
    
* 我們希望照片的時間能為我們計算的平均時間，所以動畫曲線 `animation-timing-function` 應為 `linear`。
    

以下使用 `animation` 的簡寫：

```css
.img-screen > img{
    animation: slide 24s linear infinite;
}
```

---

## 四、設定每張照片的延遲時間

最後，除了第一張照片，後面的照片都需要依序延遲出現，所以每張照片需要延遲 4 秒（總時長 / 照片總數）的倍數。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728140984072/2a8d4640-55aa-485c-92ae-bdb27cae53c0.png align="center")

```css
.img-screen > img{
    &:nth-child(2){ animation-delay: 4s; }
    &:nth-child(3){ animation-delay: 8s; }
    &:nth-child(4){ animation-delay: 12s; }
    &:nth-child(5){ animation-delay: 16s; }
    &:nth-child(6){ animation-delay: 20s; }
}
```

這樣就完成簡單的 CSS 照片淡入淡出輪播動畫囉！

不過，如果我們想改變總時長時，就會變得很麻煩，要重新計算好多地方，這時我們可以善用 CSS 的變數，稍微優化一下：

```css
:root{
    --total-time: 24s;
    --total-photo: 6;
}

.img-screen > img{
    &:nth-child(2){ animation-delay: calc(var(--total-time)/var(--total-photo)); }
    &:nth-child(3){ animation-delay: calc(var(--total-time)/var(--total-photo)*2); }
    &:nth-child(4){ animation-delay: calc(var(--total-time)/var(--total-photo)*3); }
    &:nth-child(5){ animation-delay: calc(var(--total-time)/var(--total-photo)*4); }
    &:nth-child(6){ animation-delay: calc(var(--total-time)/var(--total-photo)*5); }
}
```

這樣我們想改總時長時，只需要改一個地方就好了！

只是，有個很可惜的地方，就是 `@keyframes` 的百分比目前還無法支援使用 CSS 變數，所以這個地方還是需要手動計算。

如果有天 `@keyframes` 支援使用 CSS 變數，這樣光用 CSS 就能夠做出很多、很多複雜的動畫了！