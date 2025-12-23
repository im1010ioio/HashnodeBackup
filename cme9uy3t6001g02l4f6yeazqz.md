---
title: "#56 純 Css 跑馬燈動畫，單趟跑、無限跑、要暫停都可以"
datePublished: Wed Aug 13 2025 10:58:58 GMT+0000 (Coordinated Universal Time)
cuid: cme9uy3t6001g02l4f6yeazqz
slug: css-marquee
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766490924289/8497c2dd-406f-41f3-8886-ce580fd6c3b8.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766490929110/bc8c69c5-72d6-4d3f-8bf2-0c35c6eb7ffb.png
tags: css3, css, css-animation, marquee, css-marquee

---

在很久以前 HTML 中有跑馬燈元素 `<marquee>`，很輕易就能做出跑馬燈，所以在以前許多網頁中，常常可以看到它的身影，寫著「歡迎光臨 OOO 的小窩」之類的（暴露年紀了XD）。但是，後來 W3C 因為易用性問題，認為跑馬燈可能會分散注意力並且難以閱讀，於是棄用了它，雖然許多瀏覽器仍支援，但是**現已不建議使用這個 HTML 元素**。

然而，隨著 Y2K 風格開始流行，跑馬燈動畫有捲土重來之勢，許多網頁特效都開始加入這種效果（通常是裝飾用，建議還是不要濫用多個，不然會很花）。

雖然 HTML 中的跑馬燈已不建議用，但我們用 CSS 的 Animation + Transform 的 TranslateX，還是可以製作出簡單的純 CSS 跑馬燈動畫，今天就來教大家！

這次分享的跑馬燈動畫分成兩種：

* 一種是單趟跑，內容一次只出現一次；
    
* 另一種是無限的跑馬燈，內容從頭到尾反覆出現，沒有停頓的時候。
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728225248678/26e3fec1-f44f-422d-9cff-89777a6f1e80.gif align="center")

> DEMO: [Pure CSS marquee - One Way & Infinite](https://codepen.io/im1010ioio/pen/vYoKdQq)

---

## 一、單趟跑馬燈

單趟跑馬燈指的是：

* 一開始內容沒有出現，
    
* 內容跑完後再開始重複一次動畫。
    

所以，我們內容先設定為最小寬度為 100%，讓他的寬度至少會佔據整個畫面寬度，所以內容就不會重複出現。

再來，考慮到內容可能超出畫面寬度 100% 時，我們要讓內容能保有自己的寬度，所以設定了 `display: inline-block`。

最後，將它的動畫 `@keyframes` 設定由「往右偏移自己的寬度 `translateX(100%)` 」至「往左偏移自己的寬度 `translateX(-100%)` 」，就完成了。

```xml
<div class="marquee marquee-one-way">
    <div class="marquee-item">嗨！跑馬燈，獨自走了一遍又一遍</div>
</div>
```

```css
@keyframes marquee-one-way {
	from {
		transform: translateX(100%);
	}
	to {
		transform: translateX(-100%);
	}
}

.marquee-one-way .marquee-item{
    display: inline-block;
    min-width: 100%;
    animation: marquee-one-way 15s linear infinite;
}
```

這個方法雖然很簡單，但是在這前兩個範例中，有個小缺點，就是動畫行進的速度會受到內容的長度與畫面寬度的影響。

---

## 二、無限跑馬燈

無限跑馬燈指的是：

* 一開始內容就出現，
    
* 內容跑完後，後面還有一模一樣的內容，所以看起來像無限循環。
    

需要達到這種效果，我們需要兩個一模一樣的內容，並且將內容的寬度都設定為 100%。

因為一開始內容就出現，所以它的動畫 `@keyframes` 設定由「不偏移 `translateX(0)` 」至「往左偏移自己的寬度 `translateX(-100%)` 」。這樣就完成了！

```xml
<div class="marquee marquee-infinite">
    <div class="marquee-item">
        <div>ABCD</div><div>EFG</div><div>HIJK</div><div>LMN</div><div>OPQR</div><div>STUV</div><div>WXYZ</div>
    </div>
    <div class="marquee-item">
        <div>ABCD</div><div>EFG</div><div>HIJK</div><div>LMN</div><div>OPQR</div><div>STUV</div><div>WXYZ</div>
    </div>
</div>
```

```css
@keyframes marquee-infinite {
	from {
		transform: translateX(0);
	}
	to {
		transform: translateX(-100%);
	}
}

.marquee-infinite .marquee-item{
    min-width: 100%;
    animation: marquee-infinite 6s linear infinite;
}
```

在最後一個範例中，我的單位都使用 `vw`，所以所有文字、間距大小會隨著螢幕寬度縮放，於是就可以固定住內容移動的速度。

---

## 三、hover 時暫停跑馬燈動畫

另外，我們還可以在跑馬燈的容器上設定 hover 時暫停動畫，如果內容上有連結之類的，就不用擔心使用者按不到了：

```css
.marquee:hover .marquee-item{
    animation-play-state: paused;
}
```

---

不過實際怎麼做，還是要依據需求而定，這三個範例就留給大家參考囉！