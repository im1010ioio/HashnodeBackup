---
title: "#33 CSS 切換淺色/深色模式：Media Queries 的 prefers-color-scheme 搭配 CSS 變數"
datePublished: Fri Dec 01 2023 03:14:27 GMT+0000 (Coordinated Universal Time)
cuid: clpm1wqdw000h09k0awxf37db
slug: css-prefers-color-scheme
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701400321510/00c270b8-9be2-41b1-826b-e4957accebb1.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1701400338248/19cd3013-192a-4f9c-af2e-7378e3b94bb8.png
tags: css3, css, cssmediaqueries, prefers-color-scheme

---

> #### **↓ 今日學習重點 ↓**
> 
> * 使用 Media Queries 的 prefers-color-scheme  
>     搭配 CSS 變數設定預設的淺色/深色模式
>     
> * 使用 HTML input checkbox 做淺色與深色模式的切換
>     

關於顏色的設定方法、顏色的變數、混色的新方法，我們在前兩篇都說過了，關於顏色還有什麼需要了解的呢？那就是近幾年在軟體設計中常出現的：淺色與深色模式切換。

今天我們要學會使用 CSS Media Queries 加上 CSS 變數打造自己的淺色與深色模式，甚至更進一步，用 HTML 的 input checkbox 做到簡單的切換（toggle）行為。

另外，雖然 SASS (SCSS) 與 JS 不在本系列學習範圍內，但是還是提供了他們的解法給大家參考。

---

## 一、Media Queries 的 `prefers-color-scheme`

在 CSS 中我們可以透過 Media Queries 的 prefers-color-scheme 偵測使用者的裝置是偏好淺色還是深色模式。語法很簡單，總共有 3 個值可以使用：

1. `no-preference`：當使用者裝置偏好色系不知道時
    
2. `light`：當使用者裝置偏好淺色模式時
    
3. `dark`：當使用者裝置偏好深色模式時
    

寫起來如下：

```css
@media (prefers-color-scheme: no-preference) { ... }
@media (prefers-color-scheme: light)         { ... }
@media (prefers-color-scheme: dark)          { ... }
```

> 延伸閱讀：[prefers-color-scheme - CSS：层叠样式表 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@media/prefers-color-scheme)

---

## 二、依據使用者偏好色系呈現預設的淺色/深色模式

#### prefers-color-scheme 搭配變數使用

接著，我們可以使用 CSS 的變數，設定淺色模式時 11 個階層的灰階（由淺至深，含黑白色），然後，再另外於深色模式時將變數依序顛倒設定（由深至淺，含黑白色），覆蓋開頭設定的灰階變數。

> 關於 CSS 變數的的寫法，可參考這系列之前的文章：  
> [#09 原生的 CSS 變數，基本與進階應用](https://ithelp.ithome.com.tw/articles/10327133)

**CSS**

```css
/*  -------- 預設 --------  */
:root {
	--gray-000:  #fff;
	--gray-100:  #f9f9fd;
	--gray-200:  #e8edf4;
	--gray-300:  #DBE2E7;
	--gray-400:  #CED7E0;
	--gray-500:  #A9B3BD;
	--gray-600:  #677889;
	--gray-700:  #495562;
	--gray-800:  #2D4155;
	--gray-900:  #1A2632;
	--gray-1000: #000;
}

/*  -------- 當使用者偏好深色模式 --------  */
@media (prefers-color-scheme: dark){
	:root{
		--gray-000:  #000;
		--gray-100:  #1A2632;
		--gray-200:  #2D4155;
		--gray-300:  #495562;
		--gray-400:  #677889;
		--gray-500:  #A9B3BD;
		--gray-600:  #CED7E0;
		--gray-700:  #DBE2E7;
		--gray-800:  #e8edf4;
		--gray-900:  #f9f9fd;
		--gray-1000: #fff;
	}
}
```

> 補個設計小知識，以上範例的黑白灰，在色相上都帶有一點點的藍色。
> 
> 因為如果是純正的黑白灰，沒有一點顏色的話，看起來會很像影印的結果，讓人感覺死氣沉沉。所以在 UI 設計上，常常見到黑白灰會加上一點藍色或紫色調，呈現結果會比較漂亮。當然這不是絕對，也是有很棒的純黑白設計。

這樣一來，只要需要切換顏色的地方都套用我們設定的黑白灰變數，就能夠依據使用者偏好色系，呈現對應的的淺色/深色模式囉！

![@media prefers-color-scheme](https://cdn.hashnode.com/res/hashnode/image/upload/v1701236639457/af1ee584-2567-493e-9b08-03f00c8e4f4e.gif align="center")

> DEMO 連結：[@media prefers-color-scheme](https://codepen.io/im1010ioio/pen/GRzXNvW)

---

## 三、切換淺色/深色模式

不過，這樣還不夠，我們通常會希望：預設顏色模式是依據使用者偏好色系，但是使用者也可以自主切換淺色/深色模式。

### 1\. 使用 HTML input checkbox 切換

其實 HTML 的 input checkbox 加上 CSS 的 `:checked` 偽類，能夠在不寫 JS 的情況下，做到簡單的來回切換（toggle）行為。

如果換頁時要記住使用者的設定，就需要使用到 JS，可以在 cookie 中存放一個布林值，然後在每一頁套用在這個 input 上。

#### (1) 純 CSS 版本

**HTML**

```xml
<input type="checkbox" id="color-scheme-toggle">
<!-- 使用 label 控制 checkbox -->
<label for="color-scheme-toggle">
	<span class="material-icons"></span>
</label>
```

**CSS**

```css
/* 隱藏起 checkbox，並且防止誤觸 */
#color-scheme-toggle{
	position: fixed;
	pointer-events: none;
	width: 0;
	height: 0;
	opacity: 0;
}

label[for="color-scheme-toggle"] {
    /* 設定基本樣式 */
	display: inline-block;
	margin-top: 2rem;
	padding: 1rem 1.5rem;
	color: var(--gray-700);
	cursor: pointer;
	border: 1px solid currentcolor;
	border-radius: 2rem;
	transition: var(--transition-base);

    /* 因為想要使用 CSS 切換文字，所以使用 ::before、::after 放文字 */
	.material-icons::before{
		content: "light_mode";
	}
	&::after{
		content: "Switch to Light Theme";
	}
}
```

接著，透過 checkbox 的勾選與否，加上使用父層選擇器 `:has` ，設定當有勾選的時候 html 變數不一樣，把 `:root` 預設的變數覆蓋過去，就能改變整頁的設定了：

> 注意：Firefox 桌機版即將在下個版本（版本 121）才支援 `:has` ，而 Firefox Android 尚未支援，開發時請斟酌一下用戶瀏覽器的支援程度。（2023/11）

```css
/*  -------- 預設 --------  */
:root {
	/* 略：設定淺色變數與文字樣式 */
}

/* 當 html 中的 #color-scheme-toggle checked 時  */
html:has(#color-scheme-toggle:checked) {
    /*  略：設定深色變數與文字樣式 */
}

/*  -------- 當使用者偏好深色模式 --------  */
@media (prefers-color-scheme: dark) {
    /*  略：設定深色變數與文字樣式 */

    /* 當 html 中的 #color-scheme-toggle checked 時  */
    html:has(#color-scheme-toggle:checked) {
        /*  略：設定淺色變數與文字樣式 */
    }
}
```

實際結果結果如下：

![Pure CSS Color Scheme Toggle](https://cdn.hashnode.com/res/hashnode/image/upload/v1701249965929/a4800318-2c79-4998-bfe2-f752703b8d97.gif align="left")

> DEMO 連結：[Pure CSS Color Scheme Toggle](https://codepen.io/im1010ioio/pen/QWYVdJw)

#### (2) SASS (SCSS) 版本

> SASS (SCSS) 不在本次系列文的教學範圍內，不會的可以先跳過。

剛剛那樣寫有一點髒髒的，我們重複寫了兩遍長長的淺色與深色的變數與文字樣式，如果你會使用 SASS (SCSS) 可以用 `@mixin` 和迴圈 `@for` 管理：

```scss
$grays: #fff, #f9f9fd, #e8edf4, #DBE2E7, #CED7E0, #A9B3BD, #677889, #495562, #2D4155, #1A2632, #000;

@mixin light-mode() {
	body {
		@for $i from 1 through length($grays) {
			$color: nth($grays, $i);
			--gray-#{$i - 1}00: #{$color};
		}
	}
	label[for="color-scheme-toggle"]{
		.material-icons::before{ content: "dark_mode"; }
		&::after{ content: "Switch to Dark Theme"; }
	}
}

@mixin dark-mode() {
	body {
		@for $i from 1 through length($grays) {
			$color: nth($grays, $i);
			--gray-#{10 - $i + 1}00: #{$color};
		}
	}
	label[for="color-scheme-toggle"]{
		.material-icons::before{ content: "light_mode"; }
		&::after{ content: "Switch to Light Theme"; }
	}
}

// -------- 預設 -------- //
@include light-mode();
html:has(#color-scheme-toggle:checked) {
	@include dark-mode();
}

// -------- 當使用者偏好深色模式 -------- //
@media (prefers-color-scheme: dark) {
	@include dark-mode();
	html:has(#color-scheme-toggle:checked) {
		@include light-mode();
	}
}
```

> DEMO 連結：[Pure CSS Color Scheme Toggle (SCSS Version)](https://codepen.io/im1010ioio/pen/rNPZrJe)

### 2\. 使用 JS 切換

> JS 不在本次系列文的教學範圍內，不會的可以先跳過。

當然，我們也可以使用 JS 切換樣式。

這邊不管是淺色還是深色模式，CSS 預設的變數寫在 `:root` 裡，相反的變數則寫成 class，要切換時使用 JS 在 HTML body 加上對應的 class，把 `:root` 預設的變數覆蓋過去。

我本來使用 JS 切換，是想要減少重複寫 CSS 變數的次數，但是 `@media` 和其他選擇器不能並列寫在一起，所以還是得要多寫一次深色模式的變數。所以，說有優化其實也還好，就當多一種寫法給大家參考囉！如果你有更好的方式也歡迎底下留言告訴我。

（PS. 這邊的範例沒有 watch 系統預設偏好色系的改變，所以如果更換系統預設偏好色系，要重整才有作用）

**CSS**

```css
/*  -------- 預設 --------  */
:root, .light-mode { /* 略：設定淺色變數 */ }

/*  -------- 當使用者偏好深色模式 --------  */
@media (prefers-color-scheme: dark) {
    :root { /* 略：設定深色變數 */ }
}
.dark-mode { /* 略：設定深色變數 */ }
```

**JS**

```javascript
const body = document.body;
const toggleIcon = document.getElementById("toggle-icon");
const toggleText = document.getElementById("toggle-text");

const iconString = ["light_mode", "dark_mode"];
const textString = ["Switch to Light Theme", "Switch to Dark Theme"];

// 套用初始文字
if (window.matchMedia('(prefers-color-scheme: dark)').matches){
	toggleIcon.innerText = iconString[0];
	toggleText.innerText = textString[0];
} else {
	toggleIcon.innerText = iconString[1];
	toggleText.innerText = textString[1];
}

function toggleString() {
    toggleIcon.innerText = (toggleIcon.innerText === iconString[0]) ? iconString[1] : iconString[0];
    toggleText.innerText = (toggleText.innerText === textString[0]) ? textString[1] : textString[0];
}

function toggleColorMode() {
	if(window.matchMedia('(prefers-color-scheme: dark)').matches){
		body.classList.toggle("light-mode");
	} else {
		body.classList.toggle("dark-mode");
	}
	toggleString();
}
```

> DEMO 連結：[Color Scheme Toggle](https://codepen.io/im1010ioio/pen/gOqdyYE)

---

好的，關於 CSS 顏色的部分就暫時先告一個段落了。  
接下來，我們要來準備處理圖片與畫圖形了。

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")