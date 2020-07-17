---
layout: default
title: SASS(SCSS)
parent: Web Tech
nav_order: 2
---

# Layout Utilities
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

## SASS(SCSS)

* CSS 전처리기(CSS Preprocessor)는 특별한 Syntax를 가지고 있으며,  믹스인(mixin), 중첩 셀렉터(nesting selector), 상속 셀렉터(inheritance selector) 등 프로그래밍적인 요소를 접목해 방대해지는 CSS 문서의 양을 효율적으로 처리하고 관리해 주는 통합적인 것이다.
* 이 CSS 전처리기(CSS Preprocessor) 자체만으로는 웹 서버가 인지하지 못하기 때문에 각 CSS 전처리기에 맞는 Compiler를 사용해야 하고 컴파일을 하게 되면 CSS 문서로 변환이 된다.

##### CSS 전처리기(CSS Preprocessor)장점
- 코드의 재사용
- 프로그래밍적 처리 (조건분기, 반복처리 등을 이용)
- 셀렉터 기술의 간략화
- File Merge, CSS압축

##### Sass(SCSS)
<div class="code-example narrow" markdown="1">
- Ruby로 개발되어짐
- 변수 접두어 : $
- Sass와 SCSS의 차이점은 {}(중괄호)와 ;(세미콜론)의 유무로 Sass가 없음.
- 프로그래밍적 처리를 지원
- npm에 sass자체가 등록
- 다른 전처리기에 비해 상대적으로 다양한 기능 제공 및 기속적인 업데이트 진행되고 있음.
- npm 통한 설치방법 : $npm i -g node-sass
- sass 컴파일 : $ sass style.scss style.css


| Code                        | SASS  |	SCSS      |
|:----------------------------|:-----:|:---------:|
| mixin	                      |  =  	| @mixin    |
| include	                    |  +  	| @include  |
| { } (중괄호)와 ; (세미콜론)  |	무	  | 유        |

</div>


##### LESS
<div class="code-example narrow" markdown="1">
- Javascript문법을 취하고 있음. (Node.js엔진을 기반으로 구동).
- Twitter의 부트스트랩에서 사용되면서 전파됨
- Sass에 달리 브라우저 단에서도 동작함.
- 변수 접두어 : @
- 초기에는 선호도 높았으나 node-sass가 나오고 나서부터는 sass가 더 선호됨.
- npm 통한 설치방법 : $npm i -g less
- less컴파일 : $ lessc style.less style.css
</div>

##### Stylus
<div class="code-example narrow" markdown="1">
- CSS전처리기 중 가장 나중에 나옴.
- 중괄호({})와 세미콜론(;)과 콜론(:)을 생략가능.
- 들여쓰기로 블락을 판단하기 때문에 들여쓰기는 지켜주어야 함.
- less와 동일하게 node.js 기반으로 구동.
- open-project에 많이 사용.
- 완성도 낮고 여러 버그 존재
- npm 통한 설치방법 : $ npm install -g stylus
- Stylus 컴파일 : $ stylus style.styl style.css
</div>


## 문법

##### 주석

```
//컴파일 되지 않는 한 줄 주석
/*
컴파일되는
여러 줄
주석
*/
```

##### 중첩(Nesting)

<div class="flexbox" markdown="1">

```scss

.wrapper {
  position: relative;
  width: 100%;
  .list {
    display: flex;
    justify-content: center;
    align-items: center;
    li {
      flex: 1;
    }
  }
}
```

```css

.wrapper { 
  position: relative;
}
.wrapper .list {
  display: flex; 
  justify-content: center; 
  align-items: center;
}
.wrapper .list li {
  flex: 1;
}
```
</div>

##### Ampersand(상위 선택자 참조)
<div class="flexbox" markdown="1">

```scss

.btn--simple {
    color: #000;
    border: #000 solid 1px;
    background-color: #fff;
    &:hover {
      color: #ddd;
      background-color: #444;
    }
    &.active {
      color: #fff;
      background-color: #000;
    }
}

.text {
  &--small { font-size: 12px; }
  &--medium { font-size: 14px; }
  &--large { font-size: 16px; }
}

.parent {
 .wrapper & {
    border: 1px solid black;
  }
```

```css

.btn--sample {
  color: #000; 
  border: #000 solid 1px; 
  background-color: #fff;
}
.btn--sample:hover {
  color: #ddd;
  background-color: #444;
}
.btn--sample.active{
  color: #fff;
  background-color: #000;
}
.text--small {font-size: 12px;}
.text--medium {font-size: 14px;}
.text--large {font-size: 16px;}
.wrapper .parent {border:1px solid black;}
```

</div>


##### @at-root(중첩 벗어나기)
<div class="flexbox" markdown="1">

```scss

.list {
  $w: 25%;
  $h: 50px;
  li {
    width: $w;
    height: $h;
  }
  @at-root .box {
    width: $w;
    height: $h;
  }
}
```

```css

.list li {
  width: 25%;
  height: 50px;
}
.box {
  width: 25%;
  height: 50px;
}
```
</div>

##### 중첩된 속성
<div class="flexbox" markdown="1">

```scss

.box {
  font: {
    weight: 600;
    size: 14px;
    family: 'Noto Sans KR', sans-serif; 
  }
  margin: {
    top: 10px;
    left:20px;
  }
  padding: {
    bottom: 30px;
    right: 20px;
  }
}
```

```css

.box {
  font-weight: 600;
  font-size: 14px;
  family: 'Noto Sans KR', sans-serif;
  margin-top: 10px;
  margin-left: 20px;
  padding-bottom: 30px;
  padding-right: 20px;
}
```
</div>

##### 변수(Variable) - $변수이름: 속성값;
* 변수 유효범위(Variable Scope) - 선언된 블록( { } )내에서만 유효범위를 가진다.
<div class="flexbox" markdown="1">

```scss

$color-primary: #FF5733;
$image-url:'/assets/images/';
$width:200px;

.box {
  width: $width;
  margin-left:calc(#{$width} - 150px);
  background: {
    color: $color-primary;
    image: url($image-url + 'bg.jpg');
  }
}
```

```css

.box {
 width: 200px;
 margin-left: 50px;
 background-color: #FF5733;
 bacgkround-image: url("/assets/images/bg.jpg");
```
</div>


##### 변수 재 할당(Variable Reassignment)
<div class="flexbox" markdown="1">

```scss

$red: #ff0000;
$color-danger: $red;

.box--alert {
  color: $color-danger;
}
```
```css

.box--alert {
  color: #ff0000;
}
```
</div>


##### !global(전역 설정) - 같은 이름의 변수가 있을 경우는 !global로 설정된 값이 우선시된다.
<div class="flexbox" markdown="1">

```scss

$bg: #eee;
.box1 {
  $bg: #ddd !global;
  background: $bg;
}
.box2 {
  background: $bg;
}
```
```css

.box1 {
 background: #ddd;
}
.box2 {
 background: #ddd;
}
```
</div>

##### !default(초깃값 설정) - 할당되지 않은 변수의 초깃값을 설정하지만, 할당되어 있는 변수가 있다면 기존 할당값이 우선시 된다.
<div class="flexbox" markdown="1">

```scss

$color-alert: #ff0000;

.box {
  $color-alert: #ff6600 !default;
  background: $color-alert;
}
```

```css

.box {
 background: #ff0000;
}
```
</div>

##### #{} 문자보간 - 변수값을 넣을 수 있다.
<div class="flexbox col" markdown="1">

```scss

$family: unquote("Noto+Sans");
@import url("http://fonts.googleapis.com/css?family=#{$family}");
```
```css

@import url("http://fonts.googleapis.com/css?family=Noto+Sans");
```
</div>

##### import(가져오기)

<div class="" markdown="1">

```scss
// 파일확장자가 .css일때
@import "style.css";

// 파일이름이 http://로 시작할 때 
@import "http://test.com/";

// url()이 붙었을 경우 
@import url(style);

// 미디어쿼리가 있는 경우 
@import "style" screen;

//여러파일 가져올 때(,로 구분)
@import "header", "footer";
```
</div>

##### 파일분활(Partials)
<div class="" markdown="1">
* 파일 이름 앞에 _를 붙여 @import로 가져오면 컴파일시 ~.css 파일로 컴파일 되지 않습니다.

  ```scss
  ├─css
    │  └─main.css  // main + header + footer
  ├─scss
    │  ├─_header.scss
    │  ├─_footer.scss
    │  └─main.scss // @import header, footer가 되어 있음.
  ```

* 컴파일하면

  ```css 
  main.css 
  // main.scss + header.scss + header.scss의 css내용이 main.css에 합쳐서 컴파일된다.
  ```
</div>

## 연산(Operations)
<div class="" markdown="1">
* 상대적 단위(%, em, vw 등)의 연산의 경우 CSS calc()로 연산

```scss
width: 50% - 20px; // 단위 모순 에러(Incompatible units error)
width: calc(50% - 20px); // 연산 가능
```
</div>

##### 나누기 연산 (/) 
<div class="flexbox" markdown="1">

```scss

.box{
  $w: 100%;
  width: $w / 2;  // 변수에 저장된 값을 나누기
  height: (500px / 2);  // 괄호로 묶어서 나누기
  font-size: 20px + 18px / 3;  // 더하기 연산과 같이 사용
}
```
```css

.box {
  width: 50%;
  height: 250px;
  font-size: 26px;
}
```
</div>

##### 문자(String)연산 : "+"로 연결
<div class="flexbox" markdown="1">

```scss

.box::after {
  content: "Hello " + World;
  flex-flow: row + "-reverse" + " " + wrap
}
```
```css

.box::after {
  content: "Hello World";
  flex-flow: row-reverse wrap;
}
```
</div>

##### 색상(color) 연산 ​
<div class="flexbox col" markdown="1">

```scss

.box {
  color: #123456 + #235678;
  // R: 12 + 23 = 35
  // G: 34 + 56 = 8a
  // B: 56 + 78 = ce
  background: rgba(50, 100, 150, .5) + rgba(10, 20, 30, .5);
  // R: 50 + 10 = 60
  // G: 100 + 20 = 120
  // B: 150 + 30 = 180
  // A: Alpha channels must be equal
}

.box2 {
  $color: rgba(10, 20, 30, .5);

  color: opacify($color, .3);  // 30% 더 불투명하게  0.5 + 0.3
  background-color: transparentize($color, .2);  // 20% 더 투명하게  0.5 - 0.2
}
```

```css

.box{
  color: #358ace;
  background: rgba(60, 120, 180, 0.5);
}
.box2 {
  color: rgba(10, 20, 30, 0.8);
  background-color: rgba(10, 20, 30, 0.3);
}
```
</div>


##### 논리(Boolean) 연산 - @if 조건문에서 사용
<div class="flexbox" markdown="1">

```scss

$width: 90px;
.box {
  @if not ($width > 100px) {
    height: 300px;
  }
}
```
```css

.box{
  height: 300px;
}
```
</div>

##### 재활용(Mixins) - @mixin, @include

```scss
@mixin 믹스인이름 {
  스타일;
}
```

<div class="flexbox" markdown="1">

```scss

@mixin large-text {
  font-size: 22px;
  font-weight: bold;
}

.box {
  @include large-text; // @include 믹스인이름;
  width: 100%;
  border: #cecece solid 1px;
}
```

```css

.box{
  font-size: 22px;
  font-weight: bold;
  width: 100%;
  border: #cecece solid 1px;
}
```
</div>

## 인수(Arguments)

```scss
// 인수 설정
@mixin 믹스인이름($매개변수) {
  스타일;
}

// 인수 기본값 설정
@mixin 믹스인이름($매개변수: 기본값) {
  스타일;
}

// 키워드 인수
@mixin 믹스인이름($매개변수A: 기본값, $매개변수B: 기본값) {
  스타일;
}

@include 믹스인이름($매개변수B: 인수);

//가변 인수
@mixin 믹스인이름($매개변수...) {
  스타일;
}

@include 믹스인이름(인수A, 인수B, 인수C);
```
<div class="flexbox col" markdown="1">

```scss

//인수 설정
@mixin dash-line($width, $color) {
  border: $width dashed $color;
}

//인수 기본값 설정
@mixin solid-line($width: 1px, $color: black) {
  border: $width solid $color;
}

//키워드 인수
@mixin position($p: absolute, $t: null, $b: null, $l: null, $r: null) {
  position: $p;
  top: $t;
  bottom: $b;
  left: $l;
  right: $r;
}

//가변 인수
@mixin bg($width, $height, $bg-values...) {
  width: $width;
  height: $height;
  background: $bg-values;
}

@mixin font($style: normal, $weight: normal, $size: 16px, $family: sans-serif) {
  font: {
    style: $style;
    weight: $weight;
    size: $size;
    family: $family;
  }
}

.box1 { @include dash-line(1px, #ff0000);}
.box2 { @include dash-line(4px, blue);}
.box3 { @include solid-line;}
.box4 { @include solid-line(4px);}
.box5 { @include position($b: 10px, $r: 20px);}
.box6 {
  @include position(
    fixed,
    $t: 30px,
    $r: 40px
  );
}
.box7 {
  @include bg(
    100px,
    200px,
    url("/images/a.png") no-repeat 10px 20px,
    url("/images/b.png") no-repeat,
    url("/images/c.png")
  );
}
.box8 { // 매개변수 순서와 개수에 맞게 전달
  $font-values: italic, bold, 16px, sans-serif;
  @include font($font-values...);
}
.box8-1 { // 필요한 값만 키워드 인수로 변수에 담아 전달
  $font-values: (style: italic, size: 22px);
  @include font($font-values...);
}
.box8-2 { // 필요한 값만 키워드 인수로 전달
  @include font((weight: 900, family: monospace)...);
}
```

```css

.box1 {border: 1px dashed #ff0000;}
.box2 {border: 4px dashed blue;}
.box3 {border: 1px solid black;}
.box4 {border: 4px solid black;}
.box5 {position: absolute; bottom: 10px; right: 20px;}
.box6 {position: fixed; top: 30px; right: 40px;}
.box7 {
  width: 100px;
  height: 200px;
  background: url("/images/a.png") no-repeat 10px 20px,
              url("/images/b.png") no-repeat,
              url("/images/c.png");
}
.box8 {font-style: italic; font-weight: bold; font-size: 16px; font-family: sans-serif;}
.box8-1 {font-style: italic; font-size: 22px;}
.box8-2 {font-weight: 900; font-family: monospace;}
```
</div>

##### @content

```scss
@mixin 믹스인이름() {
  스타일;
  @content;
}

@include 믹스인이름() {
  // 스타일 블록
  스타일;
}
```

<div class="flexbox" markdown="1">

```scss

@mixin icon($url) {
  &::after {
    content: $url;
    @content;
  }
}

$color: red;

@mixin colors($color: blue) { // Mixin의 범위
  @content;
  background-color: $color;
  border-color: $color;
}

.icon1 {
  @include icon("/images/icon.png");
}
.icon2 {
  @include icon("/images/icon.png") {
    position: absolute;
  };
}
.box1 {
  @include colors() { // 스타일 블록이 정의된 범위
    color: $color;
  }
}
```

```css

.icon1::after {
  content: "/images/icon.png";
}
.icon2::after {
  content: "/images/icon.png";
  position: absolute;
}
.box1 { 
 color: red;
 background-color: blue;
 border-color: blue;
}
```
</div>

## 함수

##### @function

```scss
@function 함수이름($매개변수) {
  @return 값
}

// Functions
함수이름(인수)
```

<div class="flexbox" markdown="1">

```scss

$max-width: 980px;

@function columns($number: 1, $columns: 12) {
  @return $max-width * ($number / $columns)
}

.box_group {
  width: $max-width;
  .box1 {width: columns();}
  .box2 {width: columns(6);}
  .box3 {width: columns(3);}
}
```
```css

.box_group {width: 980px;}
  .box_group .box1 {width: 81.666px;}
  .box_group .box2 {width: 490px;}
  .box_group .box3 {width: 245px;}
}
```
</div>

##### if (함수)

```scss
if(조건, 표현식1, 표현식2)
// 조건의 값이 true이면 표현식1을 실행.
// 조건의 값이 false이면 표현식2를 실행.
```

<div class="flexbox" markdown="1">

```scss

.box {
  $width: 980px;
  width: if(width > 300px, $width, null);
}
```
```css

.box {width:980px;} 
```
</div>

##### @if

```scss
@if (조건1) {
  /* 조건1이 참일 때 구문 */
} @else if (조건2) {
  /* 조건2가 참일 때 구문 */
} @else {
  /* 모두 거짓일 때 구문 */
}
```
<div class="flexbox" markdown="1">

```scss

$color: orange;
.box1 {
  @if $color == strawberry {
    color: #FE2E2E;
  } @else if $color == orange {
    color: #FE9A2E;
  } @else if $color == banana {
    color: #FFFF00;
  } @else {
    color: #2A1B0A;
  }
}

@function limitSize($size) {
  @if $size >= 0 and $size <= 200px {
    @return 200px;
  } @else {
    @return 800px;
  }
}

.box2 {
  width: limitSize(180px);
  height: limitSize(340px);
}

@mixin pCenter($w, $h, $p: absolute) {
  @if
    $p == absolute
    or $p == fixed
    or not $p == relative
    or not $p == static
  {
    width: if(unitless($w), #{$w}px, $w);
    height: if(unitless($h), #{$h}px, $h);
    position: $p;
  }
}

.box3 { @include pCenter(10px, 20px); }
.box4 { @include pCenter(50, 50, fixed); }
.box5 { @include pCenter(100, 200, relative); }
```

```css

.box1 {
  color: #FE9A2E;
}
.box2 {
  width: 200px; 
  height:800px;
}
.box3 {
  width: 10px; 
  height: 20px; 
  position: absolute;
}
.box4 {
  width: 50px; 
  height: 50px; 
  position: fixed;
}
```
</div>

##### @for

```scss
// through
// 종료 만큼 반복
@for $변수 from 시작 through 종료 {
  // 반복 내용
}

// to
// 종료 직전까지 반복
@for $변수 from 시작 to 종료 {
  // 반복 내용
```

<div class="flexbox" markdown="1">

```scss

// 1부터 3번 반복
@for $i from 1 through 3 {
  .through:nth-child(#{$i}) {
    width : 20px * $i
  }
}

// 1부터 3 직전까지만 반복(2번 반복)
@for $i from 1 to 3 {
  .to:nth-child(#{$i}) {
    width : 20px * $i
  }
}
```
```css

.through:nth-child(1) { width: 20px; }
.through:nth-child(2) { width: 40px; }
.through:nth-child(3) { width: 60px; }

.to:nth-child(1) { width: 20px; }
.to:nth-child(2) { width: 40px; }
```
</div>

##### @each

```scss
@each $변수 in 데이터 {
  // 반복 내용
}

@each $key변수, $value변수 in 데이터 {
  // 반복 내용
}
```

<div class="flexbox" markdown="1">

```scss

$fruits: (apple, orange, banana);

.fruits1 {
  @each $fruit in $fruits {
    li.#{$fruit} {
      background: url("/images/#{$fruit}.png");
    }
  }
}
.fruits2 {
  @each $fruit in $fruits {
    $i: index($fruits, $fruit); // index내장함수
    li:nth-child(#{$i}) {
      left: 50px * $i;
    }
  }
}

/*
$apple: (apple, korea);
$orange: (orange, china);
$banana: (banana, japan);

@each $fruit, 
$country in $apple, 
$orange, 
$banana {
  .box-#{$fruit} {
    background: url("/images/#{$country}.png");
  }
}
*/

$fruits-data: (
  apple: korea,
  orange: china,
  banana: japan
);

@each $fruit, $country in $fruits-data {
  .box-#{$fruit} {
    background: url("/images/#{$country}.png");
  }
}
```

```css

.fruits1 li.apple {
  background: url("/images/apple.png");
}
.fruits1 li.orange {
  background: url("/images/orange.png");
}
.fruits1 li.banana {
  background: url("/images/banana.png");
}

.fruits2 li:nth-child(1) {left: 50px;}
.fruits2 li:nth-child(2) {left: 100px;}
.fruits2 li:nth-child(3) {left: 150px;}

.box-apple {
  background: url("/images/korea.png");
}
.box-orange {
  background: url("/images/china.png");
}
.box-banana {
  background: url("/images/japan.png");
}
```
</div>


##### @while

```scss
@while 조건 {
  // 반복 내용
}
```
<div class="flexbox" markdown="1">

```scss

$i: 6;

@while $i > 0 {
  .item-#{$i} {
    width: 2px * $i;
  }
  $i: $i - 2;
}
```
```css

.item-6 { width: 12px; }
.item-4 { width: 8px; }
.item-2 { width: 4px; }
```
</div>


-----

## 참고링크
- [CSS 전처리기(Pre-Processor) 배우기!](https://kdydesign.github.io/2019/05/12/css-preprocessor/){:target="_blank"}
- [LESS Syntax 시작하기](https://webclub.tistory.com/388){:target="_blank"}
- [CSS전처리기 트렌드](https://trends.google.co.kr/trends/explore?cat=733&date=today%205-y&q=Sass,Less,Stylus){:target="_blank"}
- [Sass(SCSS) 완전 정복!](https://heropy.blog/2018/01/31/sass/){:target="_blank"}
- [[개발상식] 19. Sass란, less란, Sass와 less비교](https://asfirstalways.tistory.com/141){:target="_blank"}
- [Sass가 제공하는 기본 내장 함수](https://poiemaweb.com/sass-built-in-function){:target="_blank"}
- [SASS/SCSS 내장 함수 정리](https://soooprmx.com/archives/7975){:target="_blank"}
- [Sass Color Generator](http://scg.ar-ch.org/){:target="_blank"}
- [Sass & Compass Color Functions](http://jackiebalzer.com/color){:target="_blank"}
- [HTML color codes](https://htmlcolorcodes.com/){:target="_blank"}

