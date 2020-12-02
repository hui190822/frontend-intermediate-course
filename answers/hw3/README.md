# HW3 - 寫 CSS 必備神器：CSS 預處理器
###### tags: `前端`

## Demo:
https://hui190822.github.io/frontend-intermediate-course/answers/hw3/index.html

> ## 我們為什麼要認識CSS preprocessor預處理器呢 ?

### 1. 傳統CSS
- 由於傳統CSS沒有變數與可重複使用樣式的寫法，使得邏輯上相近的樣式設定常需要重複撰寫，導致維護性較差。
- 在模組化開發時，不能採用嵌套（nested）的寫法，導致需要寫很多重複的選擇器。
### 2. CSS預處理器

若是能讓 CSS 像一般程式語言一樣，出現巢狀、變數、函式、迴圈等功能提前設置，讓你不怕業主總想從顏色A-> B-> C都修改看看，然後再回去A的選項 QQ

- 主流的 CSS 預處理器有三種 : Sass/SCSS、Less、Stylus
- CSS 預處理器相對於CSS算是較高階的語法，需經過編譯成 CSS，瀏覽器才看得懂
- 功能 : 變數 ( Variable )、繼承 ( Extend )、函式 ( Function )、混用 ( Mixin )

> ## 介紹SASS/SCSS

1. SASS 與 SCSS差別
Sass 與 Scss 的差別僅在於有無使用 { } 包覆程式碼

Scss：使用{ }表達階層關係

``` # SCSS
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
}
```
Sass：使用縮排方式表達階層關係
```# SASS
nav
  ul
    margin: 0
    padding: 0
    list-style: none
```
2. 建置環境
- 環境: Node.js
- 軟體: Vs code
- 外掛: Live Sass Compiler
    - [Live Sass Compiler設置參考](https://github.com/ritwickdey/vscode-live-sass-compiler/blob/master/docs/settings.md)

### 變數 (Variable) $
用 $ 符號宣告變數，常用在設定顏色，字型大小等，變數編譯後不會輸出在css 檔案中。

```
// 變數
$bg-color: rgba(0, 0, 0, 0.6);
$container-width: 300px;
$font-color: rgb(255, 255, 255);

//style.scss
.container{
    background-color: $bg-color;
}


//style.css
.container {
  background-color: rgba(0, 0, 0, 0.6);
}

```
### 繼承 (Extend) @extend
如果有很多 css 樣式需要重複使用，這邊就可以用繼承，將固定要寫的樣式集中在一起，日後需要使用可以用語法乎叫。
- % : 專門被繼承的樣式

```#SCSS
%aButton {
  display:block;
  text-decoration:none;
}

a {
 @extend %aButton;
 /*透過上面的@extend 直接呼叫使用已經寫好的樣式，接下來可以自定義按鈕其他的樣式*/
 width:100%;
 height:20px;
 line-height:20px;
}
```
### 函式 (Function) @function
自訂函式，可以帶變數做簡易計算變化

- 假設運用不同字級
```#scss
$baseSize: 12px;

/*寫一個函數去定義每一種類別的字，它的大小 */

@function font($level: 1) {
  @return $baseSize *$level; // 預設12px
}

/*套用函數 font()*/

.Title {
 font-size:font(6); // 72px = 12px * 6
 font-family: Roboto-Black;
}

.Title2 {
 font-size:font(4); // 48px = 12px * 4
 font-family: Roboto-Black;
}

.Paragraph {
 font-size:font(1.3); // 15.6px = 12px * 1.3
 font-family: Roboto-Black;
}
```

### 混用 (Mixin) @mixin
需搭配 @include 使用，產出多組樣式，達到客製化效果

注意: Mixin 跟 extend 最大的不同 →
Mixin 是產生多個樣式；extend 是將樣式全部集中管理。
-  下列為Alex大大提供的字級樣式

``` #scss
$baseSize:14px;
$sizeLevel:2px;

@function font($level: 0) {
  @if $level < 0 {
    $level:0 
  }
  @return $baseSize + $sizeLevel * round($level);
}

@function rhythm($size) {
  @return ceil($size * $paddingLevel / $baseLineSize) * $baseLineSize;
}

@mixin font($level: 1, $line-height: auto) {
  $size: font($level);
  $line: rhythm($size);

  font-size: $size;
  @if $line-height == auto or $line-height < $line {
    line-height: $line;
  } @else {
    line-height: $line-height;
  }
}


.aaa {
  @include font(2);
}

.bbb {
  @include font(4);
}

.ccc {
  @include font(2);
}

/* 產生出來的 CSS */

.aaa {
  font-size:20px;
}

.bbb {
   font-size:28px;
}

.ccc {
  font-size:16px;
}
```

### 補充說明

1. 在scss的註解
```
// 不會被轉譯css
/* 會被轉譯css
```
2. 使用scss，建立分區概念
- scss 工作區 (建議注解在這，從工作區修改)
- style 測試區 (dev)
- dist 上線區 (壓縮檔案)
![](https://i.imgur.com/JTr08HQ.png)

3. 匯入 (Import) @import


| 匯入其他 scss 的檔案 | 使用 @import |
| -------- | -------- |
|  撰寫 scss 時，通常會模組化管理非常多的檔案，統一匯入最終的scss，再編譯成 css        |     檔名前面會加一個下底線( _ )，e.g. _reset.scss 讓編譯工具不直接編譯成CSS     |

```#scss
@import "reset"; // 重設css
@import "variables"; // 所有變數都存放於此
@import "mixins"; // 所有mixin相關的scss
```

### 參考資料
- [從 CSS 到 SASS (SCSS) 超入門觀念引導](https://www.youtube.com/watch?v=mzuKtTuimEE)
- [Sass/SCSS 簡明入門教學](https://blog.techbridge.cc/2017/06/30/sass-scss-tutorial-introduction/)
- [SASS](https://sass-lang.com/)
