# HW1 - 基本 HTML/CSS 練習：以 Twitch 為例
###### tags: `frontend-course` 
示意圖：
![](https://i.imgur.com/nhfV86M.gif)

## Demo
https://hui190822.github.io/frontend-intermediate-course/answers/hw1/index.html


## 作業方法

 ### 1. 如何幫背景圖片加上一層半透明顏色的遮罩 ?
 - Ref: https://medium.com/@stephenlai2017/css-%E5%B9%AB%E8%83%8C%E6%99%AF%E5%9C%96%E5%8A%A0%E4%B8%8A%E4%B8%80%E5%B1%A4%E5%8D%8A%E9%80%8F%E6%98%8E%E9%A1%8F%E8%89%B2%E7%9A%84%E9%81%AE%E7%BD%A9-fa89c2fd6f07
 - background-blend-mode: 背景圖片的混合模式
 為CSS 屬性是針對背景圖片進行 (類似ps圖層混合模式效果)
 - mix-blend-mode: 圖層混合模式
 demo: http://wcc723.github.io/WorkShop-gh-pages/cssBlendMode/
 - linear-gradient
  ```
    # 使用 background-blend-mode
    background-color: rgba(0, 0, 0, .5);
    background-image: url(../img/bg-default.jpg);
    background-blend-mode: multiply;
  ```
  ```
    # 使用 linear-gradient
    background-image: linear-gradient(rgba(0,0,0,0.5),rgba(0,0,0,0.7)), url(../img/bg-default.jpg); 
  ```

### 2. flex排版置中方式
* 需在多了解flex排版
* 垂直置中方式: https://ithelp.ithome.com.tw/users/20112550/ironman/2092
* ![](https://i.imgur.com/ZvUbeNI.png)

```

display: flex;
justify-content: center;

```

## 學習資源
1. [html & css is hard, But it doesn’t have to be](https://www.internetingishard.com/)
2. [MarkSheet: A free HTML & CSS tutorial](https://marksheet.io/)
3. [Learn to Code HTML & CSS](https://learn.shayhowe.com/html-css/)

## 自我練習

### 1. 請問 CSS 的屬性position有哪幾種值？
- static /absolute /relative /fixed/

### 2. 承上，請問那幾種值有哪些區別？請講出適合應用的地方。
- position: relative 相對定位
- position: absolute 絕對定位 (搭配相對定位父層)
    與搭配top/bottom/left/right屬性做位置變化
- position: fixed 的元素會相對於瀏覽器視窗來定位

### 3. display的三個值inline, block, inline-block有什麼異同？可以試著舉出幾個例子嗎？
- display: inline為行內元素，不能設置寬高大小
- display: block為區塊元素，佔內容一行，可設置寬高
- display: inline-block為行內但有區塊形式，可設置寬高

### 4. 有哪些 HTML 元素是 inline, 哪些是 block？
- 每個HTML元素分為inline與block兩種屬性
- inline : span, img, a
- block : div, h1-h6, figure, p

### 5. 當我設定一個元素的width為300px，並且padding設成10px之後，這個元素的寬度應該會是多少？
- 元素width為320px (300+20px推內距)
- 若有 `box-sizing: border-box;` 盒模型為300px

### 6. 這次實作的畫面當頻道名稱字太多的時候，會超出一格的大小或者會直接被卡掉，有沒有辦法讓字太多的時候在尾巴顯示...？例如原本名稱叫做：「1234567」，顯示的時候變成：「12345...」？
- 讓多行文字超出時自動隱藏，並出現…
-  text-overflow: ellipsis
- codepen: 
  [See the Pen](https://codepen.io/hui190822/pen/jOroQqp)
</iframe>
<!-- {% iframe https://codepen.io/hui190822/embed/jOroQqp?height=95&theme-id=dark&default-tab=css,result %} -->

## 參考來源
1. [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
2. [學習 CSS 版面配置: flexbox](https://zh-tw.learnlayout.com/flexbox.html)
3. [深入解析 CSS Flexbox](https://www.oxxostudio.tw/articles/201501/css-flexbox.html)
