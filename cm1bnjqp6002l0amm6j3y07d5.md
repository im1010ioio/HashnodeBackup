---
title: "#41 用 CSS border-radius 畫圓角與圓圓的形狀：圓、圓柱、橢圓、蛋型、鐘型、葉子 (眼睛)、花瓣 (水滴/心形)、牛角 (彎月)"
datePublished: Sat Sep 21 2024 04:31:12 GMT+0000 (Coordinated Universal Time)
cuid: cm1bnjqp6002l0amm6j3y07d5
slug: css-border-radius
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766409453594/0471d9d5-f46b-4993-9bdc-2f6911bf1a58.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766409462965/ea06b53f-ea7d-4af9-a510-c29fdd32e5ac.png
tags: css3, css, 2articles1week, border-radius

---

在上篇文章中，我們用簡單的圓形加上模糊效果繪製了不規則的漸層，這篇我們來探討如何繪製各種形狀，其實使用 CSS 邊框 (`border`) 中的「邊框圓角 (`border-radius`) 」可以繪製出許多形狀。（突然覺得應該先寫這篇）

`border-radius` 是 CSS 中用來讓元素的邊角變圓的屬性。你可以使用這個屬性來製作圓角到圓形等效果，廣泛應用在按鈕、卡片、圖片等元素的設計中。無論是用在按鈕還是圖片上，它都能讓你的頁面設計更具柔和感。

> #### **↓ 今日學習重點 ↓**
> 
> * 學會 `border-radius` 的基本用法
>     
> * 了解繪製出圓角的原理
>     

---

## 一、基礎語法

* `border-radius` 的數值可以是**像素** (px)、**百分比** (%)，甚至是 **em** 等單位。
    
* 數值越大，圓角的弧度越大。
    
* 當 `border-radius` 的數值等於元素寬高的一半時，元素會呈現出完美的圓形。
    

### 1 個值：單一圓角（⭐️常用）

如果四個角的圓角都一樣，可以只設定一個值：

```css
div {
    border-radius: 10px;
}
```

像這樣，`div` 的四個角都會有 10px 的圓角。

### 1 個值：圓角的百分比（⭐️常用）

`border-radius` 也可以用百分比來設定，代表寬高的一半。

```css
div {
    border-radius: 50%;
}
```

這段語法會讓元素的寬高相等時，變成一個圓形；寬高不同時則會變成橢圓形。

### 2 個值：左上/右下

`border-radius` 也支援使用兩個值，分別指的是「左上+右下」和「左下+右上」的圓角。

```css
div {
    border-radius: 50px 25px;
}
```

這樣會讓元素在「左上+右下」有 50px 的圓角，「左下+右上」有 25px 的圓角。

### 4 個值：四角

你可以用四個值來分別設定每個角的圓角，順序是 **左上角、右上角、右下角、左下角**（順時針旋轉）。

```css
div {
    border-radius: 10px 20px 30px 40px;
}
```

這樣會讓左上角有 10px 圓角、右上角 20px、右下角 30px、左下角 40px。

### 完整寫法：用斜線隔開水平/垂直方向

其實 `border-radius` 完整的數值有八個，左上、右上、左下、右下的角度分為「水平方向 (橘色)」與「垂直方向 (藍色）」，如下圖：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1726853425661/c6b519c3-ce24-433c-a649-779903b12f89.png align="center")

可以使用斜線 `/` 將「水平」和「垂直」的圓角分開，這樣可以控制每個角的不同圓滑程度。

若四邊都一樣也可以簡寫，「水平」和「垂直」方向各寫一次就好：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1726853367927/36e61a00-4689-48ab-9763-bbf289ff8335.png align="center")

```css
div {
    border-radius: 40px / 20px;

    /* 等於以下： */
    border-top-left-radius: 40px 20px;
    border-top-right-radius: 40px 20px;
    border-bottom-right-radius: 40px 20px;
    border-bottom-left-radius: 40px 20px;
}
```

---

## 二、實際 DEMO：各種圓圓的形狀

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1726847571258/01f53ee0-32ba-4062-98e7-b93141c723f7.png align="center")

我在這裡搜集了許多用 `border-radius` 可以做出來的有趣形狀，給大家參考看看，之後再來研究關於他們的數學（有的話我會再更新在這篇文章）：

> DEMO: [CSS round shapes](https://codepen.io/im1010ioio/pen/YzomoGb)

### 圓形（⭐️常用）

```css
.circle{
    width: 100px;
    height: 100px;
    border-radius: 50px;
    /* 等同於： */
    /* border-radius: 50%; */
}
```

### 圓柱形

```css
.cylindrical{
    width: 200px;
    height: 100px;
    border-radius: 50px;
}
```

### 橢圓形

```css
.oval{
    width: 200px;
    height: 100px;
    border-radius: 50%;
    /* 等同於： */
    /* border-radius: 100px / 50px; */
}
```

### 半橢圓形

```css
.half-oval{
    width: 200px;
    height: 100px;
    border-radius: 50% / 100% 100% 0% 0%;
}
```

### 蛋形

```css
.egg{
    width: 100px;
    height: 130px;
    border-radius: 100% / 120% 120% 75% 75%;
}
```

### 鐘型

```css
.bell{
    width: 100px;
    height: 120px;
    border-radius: 100% / 160% 160% 25% 25%;
}
```

### 自訂圓角

```css
.custom-corners{
    width: 200px;
    height: 100px;
    border-radius: 40px / 20px;
}
```

### 自訂圓角 (拉長的葉子)

```css
.custom-corners-2{
    width: 200px;
    height: 100px;
    border-radius: 50% 5%;
}
```

### 葉子 (眼睛)

如果旋轉 45 度就會變成眼睛形狀。（之後會再講解 CSS 特效 `transform`）

```css
.leaf {
    width: 100px;
    height: 100px;
    border-radius: 80% 0;
}
```

### 花瓣 (水滴/心形)

如果旋轉 45 度就會變成水滴形狀。  
如果有兩個這個形狀，旋轉後可以拼成心形。（之後會再講解 CSS 特效 `transform`）

```css
.petal {
    width: 100px;
    height: 100px;
    border-radius: 0 50% 50% 50%;
}
```

### 牛角 (彎月)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1727018172885/d7c9e18d-6269-421f-a154-61adada51af0.png align="left")

如果有兩個這個形狀，旋轉後可以拼成彎月。

> DEMO: [CSS Horn](https://codepen.io/im1010ioio/pen/BagvZWe)

```css
.horn{
    height: 300px;
    width: 200px;
    border-right: 150px solid #FADC04;
    border-radius:0 0 100% 0;
}
```

---

## 三、其他例子

### BonBon — Sweet CSS3 Buttons

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1726828347459/12679b49-4a5f-48d4-adf0-977ddcda9e1c.png align="center")

> 連結：[BonBon - Sweet CSS3 Buttons](https://simurai.com/archive/buttons/)

雖然擬物風已不流行許久了，但不覺得這些按鈕滿像最近流行的 Y2K 風格嗎？總覺得這種按鈕會很可能出現在 Nokia 手機上 XD。

### 好文分享：Shapes in CSS

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1726837898526/189cfc14-eab2-46b0-a16c-0d380c86a314.avif align="center")

> 連結：[Shapes in CSS](https://alvaromontoro.hashnode.dev/shapes-in-css)

這篇文章繪製了很多圖形大家也可以參考看看，其中有些是使用 `clip-path` 做，之後我們也會在提到。

寫這篇時，發現我從未了解過 CSS 的 `border-radius`，能夠有這麼多變化，真的很神奇！（雖然最常用的還是統一尺寸的圓角或是圓形）

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")