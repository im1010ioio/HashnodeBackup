---
title: "#58 CSS offset-path：沿著軌跡行進動畫"
datePublished: Wed Aug 13 2025 11:03:03 GMT+0000 (Coordinated Universal Time)
cuid: cme9v3dhu000802kz91s3hl2a
slug: css-offset-path
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766492239186/add6d5f6-6878-4908-b6ba-06db13e96ce6.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766492244746/e6f2ee8a-664b-4b78-abd0-c4936af90871.png
tags: css3, css, css-animation, offset-path, css-offset-path

---

這篇我們會介紹如何使用 CSS 的 `offset-path` 屬性來創建路徑動畫。這個屬性允許元素沿著指定的路徑跑，配合 `offset-distance` 可以控制元素在路徑上的哪個位置。我們將透過一些範例來了解 `offset-path` 的用法。

### 基本概念

`offset-path` 用來定義一個元素應該沿著哪條路徑進行動畫效果。

這個屬性支援許多不同的形狀，包括：

* **圓** `circle()`
    
* **橢圓** `ellipse()`
    
* **矩形** `inset()`、`rect()`、`xywh()`
    
* **多邊形** `polygon()`
    
* **自訂 SVG 路徑** `path()`
    
* **外連 SVG 路徑** `url('#id')`
    

---

### 範例

以下我們簡單做幾個例子，搭配 `@keyframes` 和 `animation`，就可以讓元素不斷地在這些路徑上移動。

> DEMO: [CSS offset-path animations](https://codepen.io/im1010ioio/pen/eYqdyxN)

還可以簡單做出一個沿著地球旋轉的月亮動畫：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728442009538/486257f0-0656-4cfa-b9e6-7dc6608e6cc6.gif align="center")

> DEMO: [Earth & moon CSS offset-path animations](https://codepen.io/im1010ioio/pen/RwXGJGY)

```css
@keyframes move {
    to {
        offset-distance: -100%;
    }
}

.offset-item::before{
    animation: move 3s linear infinite;
}
```

這段 code 定義了動畫 move，使元素沿著 `offset-path` 所指定的路徑移動。`offset-distance: -100%` 指的是元素從路徑的起點移動到終點。動畫會持續 3 秒並無限循環，運行方式為線性（`linear`）。

### 使用不同的路徑

#### 1\. 圓形路徑 `circle()`

```css
.circle{
    &::before{
        offset-path: circle(); /* 預設為 closest-side */
    }
    &::after{
        height: 100%;
        aspect-ratio: 1 / 1;
        border-radius: 50%;
    }
}
```

* `offset-path: circle();` 用來定義一個圓形的路徑，元素將沿著這個圓形移動。預設情況下，圓的大小取決於容器的最短邊（`closest-side`）。
    
* `::after` 則用來設置圓的外觀，如寬高比例為 1:1 和圓角邊框（`border-radius: 50%`）。
    

#### 2\. 橢圓形路徑 `ellipse()`

```css
.ellipse{
    &::before{
        offset-path: ellipse();
    }
    &::after{
        width: 100%;
        height: 100%;
        border-radius: 50%;
    }
}
```

* `ellipse()` 則是橢圓形路徑，類似於 `circle()`，但可以有不同的長短軸比例。
    

#### 3\. 插入矩形路徑 `inset()`

```css
.inset{
    &::before{
        offset-path: inset(2rem 2rem 2rem 2rem);
    }
    &::after{
        top: 2rem;
        left: 2rem;
        right: 2rem;
        bottom: 2rem;
    }
}
```

* `inset()` 創建一個內縮的矩形路徑，四個數值代表各邊的內縮距離。這裡的例子是四邊均內縮 2rem。
    

#### 4\. 多邊形路徑 `polygon()`

```css
.polygon{
    &::before{
        offset-path: polygon(50% 0,100% 100%, 0 100%);
    }
    &::after{
        opacity: 0;
    }
}
```

* `polygon()` 定義一個多邊形路徑，該路徑的點可以用百分比來定義。在這個例子中，我們使用了一個三角形路徑。
    

#### 5\. 自定義 SVG 路徑 `path()`

```css
.path{
    &::before{
        offset-path: path('M4.66763 3.47839C7.73415 0.452998 53.2014 0.124822 67.28 0.124733C82.531 0.124822 131.656 -0.773326 134.978 2.24924C138.189 5.17089 138.456 38.5311 138.456 51.5029C138.456 63.5364 139.794 94.6159 137.653 98.4684C135.492 102.358 84.6732 103.285 75.308 103.285C66.6627 103.285 7.61119 104.189 4.40005 101.412C0.694916 98.2075 0.5858 63.5837 1.07982 51.5509C1.60756 38.6968 1.70352 6.40276 4.66763 3.47839Z');
    }
    &::after{
        opacity: 0;
    }
}
```

* `path()` 屬性允許你使用更為靈活的 SVG 路徑語法來定義自定義的動畫路徑。
    

### 總結

`offset-path` 提供了一種靈活的方式來創建基於路徑的動畫。無論是簡單的圓形和橢圓形，還是複雜的 SVG 路徑，`offset-path` 都能夠滿足需求。透過這些範例，我們可以輕鬆為元素創建有趣且流暢的動畫效果。

---

> 延伸閱讀：[让路径动画更好用！CSS offset-path现在也支持基本形状了](https://www.51cto.com/article/790497.html)