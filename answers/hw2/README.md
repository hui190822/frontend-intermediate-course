# HW2-神奇的 CSS transition
###### tags: `前端`

示意圖：

![](https://i.imgur.com/PNw3t8B.gif)


## Demo


## 作業方法

### 1. filter

|  filter   |  類似像ps的濾鏡效果，可使用filter屬性對網頁進行效果渲染。  |
| --- | --- |
|  使用方式   |  `div{ -webkit-filter: blur(3px) opacity(0.5);}` 使用不同效果 |

- **CSS Filters濾鏡效果共有十種特效，分別是：**
opacity 不透明
brightness 亮度
contrast 對比
blur 模糊
drop-shadow 下拉陰影
grayscale 灰階
sepia 懷舊
saturate 飽和
hue-rotate 色相旋轉
invert 負片

* instagram.css: https://github.com/picturepan2/instagram.css

### 2. transition

| transition            | 轉場效果，讓網頁可以做動畫變化                      |
| --------------------- | --------------------------------------------------- |
| 使用方式              | `transition: color 1s, box-shadow 2s;` 使用不同效果 |
|`transition-property`  |  定義哪些 CSS properties 會被轉場效果影響                                                             |
|`transition-duration`  |     定義轉場所花費的時間                                                |
| `transition-timing-function` | 用來定義轉場發生的時間曲線                                                |
| `transition-delay` | 定義多久之後開始發生轉場 |

* transition-timing-function: https://cubic-bezier.com/#.17,.67,.83,.67
* `transition-delay: 1s` 會延遲1s開始動畫 & 離開1s後結束動畫

## 參考來源

- [fiter](https://css-tricks.com/almanac/properties/f/filter/)
- [filter效果](http://blog.shihshih.com/css-filter/)
- [Web Fundamentals: Rendering performance](https://developers.google.com/web/fundamentals/performance/rendering/)