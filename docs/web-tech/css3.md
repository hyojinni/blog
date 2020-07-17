---
layout: default
title: CSS3
parent: Web Tech
nav_order: 1
---

# CSS3
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---
### CSS의 방법론
{:.bigger}

##### **SMACSS**(Scalable & Modular Architecture for CSS)
{:.bigger}

> - 범주화(categorization)로 패턴화 하고자 하는 방법론이다.<br>
- 기본(base), 레이아웃(layout), 모듈(module), 상태(state), 테마(theme) 다섯가지의 범주를 제시<br>
    1. 기본 규칙(Base)
        - 페이지 전반의 기본 스타일을 정의.
        - 클래스나 id는 사용하지 않음.
    2. 레이아웃 규칙(Layout)
        - 페이지의 레이아웃에 대한 정의.
        - id를 사용해서 스타일을 정의.
        - 페이지 내에서 레이아웃을 변경하는 경우에는 Class를 사용하며, 접두어로 l- 사용.
    3. 모듈 규칙(Module)
        - 스타일 재사용을 위한 규칙.
        - 내비게이션 바, 다이얼로그, 위젯 등이 모두 모듈에 해당하며, 모듈로 디자인하면 재사용이 쉬움.
        - 여러 곳에서 사용되는 공통 요소를 정의하므로 id보다는 Class를 사용함.
    4. 상태 규칙(State)
        - 요소의 상태를 전환시키기 위한 스타일.
        - 접두어로 is-사용.
    5. 테마 규칙(Theme)
        - 전반적인 표현과 느낌을 결정하는 색깔이나 이미지를 정의.
        - 테마 스타일 규칙만 따로 모아서 분리하면 테마를 쉽게 교체하고 재정의할 수 있음.
{:.list}
   

##### **BEM** (Block Element Modifier)  - 블록 / 요소 / 수식어
{:.bigger}

> - Block, Element, Module 약자<br>
- ID는 사용할 수 없다.<br>
- 오직 Class명만 사용한다.<br>
    ```css
    /*block*/
    .header { ... }
    .block { ... }
    /*element{:.property}  블록의 내부 구성을 표현, 두개의 underscores( _ )로 표기*/
    .header { ... }
    .header__link { ... }
    .header__tap { ... }
    .header__tap__item { ... }
    /*modifier{:.property}  요소의 상태를 표현, 두개의 hyphen(-)로 표기*/
    .header--hide { ... }
    .header__tap--big { ... }
    .header__tap--big { ... }
    ```
{:.list}

##### **OOCSS**(Object Oriented CSS)
{:.bigger}

> - css를 모듈화하여 중복을 최소화 한다<br>
- 구조와 외양을 분리한다.<br>
- 결합하면 다양한 결과물을 얻을 수 있다.<br>
- 컨테이너와 컨텐츠 분리<br>
    ```html
    <div class="header common-width">Header</div>
    <div class="footer common-width">Footer</div>
    ```
    ```css
    .header{
        position: fixed;
        top: 0;
    }
    .footer{
        position: absolute;
        bottom: 0;
    }
    .common-width{
        width: 700px;
        margin: 0;
    }
    ```
{:.list}

---

### Viewport CSS 단위

{:.nowrap}
| 단위 | 설명 |
|:--------------------|:-------------------------------------|
| vw(vertical width)  | 브라우저 너비(뷰포트(Viewport))값을 기준으로 100분의 1의 단위이다. |
| vh(vertical height) | 브라우저 높이(뷰포트(Viewport)) 값을 기준으로 100분의 1의 단위이다. |
| vmin & vmax         | vh, vw는 뷰포트의 너비값과 높이값에 상대적으로 영향을 받기 때문에 vmin, vmax의 너비값과 높이값에 따라 최소, 최대 값을 지정할수 있다. |


<div class="code-example narrow" markdown="1">
[브라우저 크기] 
- width{:.property}   900px - 1vmin , 
- heght{:.property}   1000px - 1vmin: 9px, 
- 1max{:.property}  10px

</div>

````css
.box { height: 100vmin; width: 100vmin; } 
 // 터치화면 양 변에 가득차는 정사각형 요소를 만들때는 이렇게 정의하면 됩니다.
.box { height: 100vmax; width: 100vmax; } 
 // 뷰포트 화면에 보여야 하는(모든 네 변이 스크린에 꽉 차 있는) 경우에는 
````
---

### Flex
{:.bigger}

##### **Container**{:.thin} `display`, `flex-flow`, `justify-content` 등의 속성을 사용
{:.bigger}

**속성**
- `display`{:.property}Flex Container를 정의
    > **flex**	 : Block 특성<br>
    **inline-flex** : Inline 특성<br>
    {:.list}

- `flex-flow`{:.property}	flex-direction와 flex-wrap의 단축 속성

- `flex-direction`{:.property}	Flex Items의 주 축(main-axis)을 설정<br>
    > **row** :	Items를 수평축(왼쪽→오른쪽)으로 표시(기본값)<br>
    **row-reverse** :	row의 반대 축으로 표시	<br>
    **column** :	Items를 수직축(위→아래)으로 표시<br>	
    **column-reverse** : column의 반대 축으로 표시<br>
    {:.list}

- `flex-wrap`{:.property}	Flex Items의 여러 줄 묶음(줄 바꿈) 설정
    > **nowrap**	모든 Itmes를 한 줄에 표시(기본값)<br>
    **wrap**	Items를 여러 줄로 묶음	<br>
    **wrap-reverse**	wrap의 역 방향으로 여러 줄로 묶음<br>
    {:.list}

- `justify-content`{:.property}	주 축(main-axis)의 정렬 방법을 설정
    > **stretch**	Container의 교차 축을 채우기 위해 Items를 늘림(기본값)<br>
    **flex-start**	Items를 각 줄의 시작점으로 정렬	<br>
    **flex-end**	Items를 각 줄의 끝점으로 정렬	<br>
    **center**	Items를 가운데 정렬	<br>
    **space-between**	시작 Item은 시작점에, 마지막 Item은 끝점에 정렬되고 나머지 Items는 사이에 고르게 정렬됨	<br>
    **space-around**	Items를 균등한 여백을 포함하여 정렬<br>
    {:.list}

- `align-content`{:.property}	교차 축(cross-axis)의 정렬 방법을 설정(2줄 이상)
    > **stretch**	Container의 교차 축을 채우기 위해 Items를 늘림(기본값)<br>
    **flex-start**	Items를 각 줄의 시작점으로 정렬	<br>
    **flex-end**	Items를 각 줄의 끝점으로 정렬	<br>
    **center**	Items를 가운데 정렬	<br>
    **space-between**	시작 Item은 시작점에, 마지막 Item은 끝점에 정렬되고 나머지 Items는 사이에 고르게 정렬됨	<br>
    **space-around**	Items를 균등한 여백을 포함하여 정렬<br>
    {:.list}

- `align-items`{:.property}	교차 축(cross-axis)에서 Items의 정렬 방법을 설정(1줄)
    > **stretch**	Container의 교차 축을 채우기 위해 Items를 늘림(기본값)<br>
    **flex-start**	Items를 각 줄의 시작점으로 정렬	<br>
    **flex-end**	Items를 각 줄의 끝점으로 정렬	<br>
    **center**	Items를 가운데 정렬	<br>
    **baseline**	Items를 문자 기준선에 정렬<br>
    {:.list}

##### **Items**{:.thin} `order`, `flex`, `align-self` 등의 속성을 사용
{:.bigger}

**속성**
- `order`{:.property}	Flex Item의 순서를 설정
    > **0** : 기본값, 숫자로 순서 설정
    {:.list}

- `flex`{:.property} flex-grow, flex-shrink, flex-basis의 단축 속성 (Item의 너비(증가, 감소, 기본)를 설정)
    > **flex-grow**	Item의 증가 너비 비율을 (기본값 : 0)<br>
    **flex-shrink**	Item의 감소 너비 비율을 설정 (기본값 : 1)<br>
    **flex-basis**	Item의 (공간 배분 전) 기본 너비 설정 (기본값 : auto)<br>
    {:.list}

    ```css
        flex: 증가너비 감소너비 기본너비;
        flex : 1; or flex : 1 1; = flex : 1 1 auto; (X)
        flex : 1; or flex : 1 1; = flex : 1 1 0; (O)
    ```

- `flex-grow`{:.property}	Flex Item의 증가 너비 비율을 설정
    > **0** : 기본값
    {:.list}

- `flex-shrink`{:.property}	Flex Item의 감소 너비 비율을 설정
    > **1** : 기본값
    {:.list}

- `flex-basis`{:.property}	Flex Item의 (공간 배분 전) 기본 너비 설정
     > **auto** : 기본값<br>
     flex-basis를 생략하면 값이 0이 되는 것을 주의<br>
     px, em, cm 등 단위로 지정<br>
    {:.list}

- `align-self`{:.property}	교차 축(cross-axis)에서 Item의 정렬 방법을 설정
    > **auto**	Container의 align-items 속성을 상속받음(기본값)<br>
    **stretch**	Container의 교차 축을 채우기 위해 Item을 늘림<br>	
    **flex-start**	Item을 각 줄의 시작점으로 정렬	<br>
    **flex-end**	Item을 각 줄의 끝점으로 정렬	<br>
    **center**	Item을 가운데 정렬	<br>
    **baseline**	Item을 문자 기준선에 정렬<br>
    {:.list}


---

### text-overflow
{:.bigger}

**요소 내에 문자열의 넘침 현상을 처리**{:.thin .text-blue-100}하는 속성

```css
div { text-overflow: ellipsis; }
```
- `clip`{:.property} 텍스트를 잘라낸다.
- `ellipsis`{:.property} 텍스트가 잘렸다는 것을 표현하기 위해 말줄임표(...)를 표시한다.
- `string(문자열)`{:.property} 지정된 문자열을 출력한다.

---
### word-wrap4
{:.bigger}

**띄어쓰기가 없는 긴 단어**{:.thin .text-blue-100}를 어떻게 처리하는 속성
```css
p { word-wrap: break-word; }
```
- `normal`{:.property}  break point에서 줄바꿈한다
- `break-word`{:.property}  요소의 경계에서 break point가 아니어도 줄바꿈을 한다
- `initial`{:.property}  기본값으로 설정한다
- `inherit`{:.property}  부모 요소의 속성값을 상속받는다.

---

### word-break
{:.bigger}

**줄바꿈**{:.thin .text-blue-100}을 할 때 단어 기준으로 할 지 글자 기준으로 할 지 정하는 속성

```css
p { word-break: break-all; }
```
- `normal`{:.property}  CJK 문자는 글자 기준으로, CJK 이외의 문자는 단어 기준으로 줄바꿈한다.
- `break-all`{:.property}  글자 기준으로 줄바꿈한다.
- `keep-all`{:.property}  단어 기준으로 줄바꿈한다.
- `initial`{:.property}  기본값으로 설정한다.
- `inherit`{:.property}  부모 요소의 속성값을 상속받는다.

---

### [attribute]
{:.bigger}

주어진 특성의 존재 여부나 그 값에 따라 요소를 선택

* a 태그에  target="_blank" 라는 속성을 가진 요소의 폰트색을 red 적용
    ```css
    a[target="_blank"] { color: red; }
    ```
* .box를 가진 요소의 백그라운드색을 yellow 적용
    ```css
    div[class~="box"] { background-color: yellow; }
    ```
* .layer로 시작하는 요소만 선택하여 백그라운드색을 yellow 적용
    ```css
    div[class|="layer"] { background-color: yellow; }
    ```
    ```html
    <div class="layer">layer</div> <!--적용-->
    <div class="layer-red">layer</div> <!--적용-->
    <div class="layer blue">layer</div> <!--미적용-->
    <div class="green layer">layer</div> <!--미적용-->
    ```
* .box로 시작하는 요소를 전부 선택
    ```css
    div[class^="box"] { background-color: red; }
    ```
    ```html
    <div class="box">layer</div> <!--적용-->
    <div class="box-yellow">layer</div> <!--적용-->
    <div class="box_yellow">layer</div> <!--적용-->
    <div class="box blue">layer</div> <!--적용-->
    <div class="yellow box">layer</div> <!--미적용-->
    <div class="yellow_box">layer</div> <!--미적용-->
    ```
* .box로 끝나는 요소를 전부 선택
    ```css
    div[class$="box"] { background-color: red; }
    ```
    ```html
    <div class="box">layer</div> <!--적용-->
    <div class="first box">layer</div> <!--적용-->
    <div class="second_box">layer</div> <!--적용-->
    <div class="box blue">layer</div> <!--미적용-->
    ```
*  .box로 가진 모든 요소를 전부 선택
    ```css
    div[class*="box"] { background-color: red; }
    ```
    ```html
    <div class="box">layer</div> <!--적용-->
    <div class="first box">layer</div> <!--적용-->
    <div class="second_box">layer</div> <!--적용-->
    <div class="box blue">layer</div> <!--적용-->
    ```

----

### transform
{:.bigger}

요소에 **회전, 크기 조절, 기울이기, 이동 효과**{:.thin .text-blue-100}를 부여

##### 2D
{:.bigger}

| 속성	|설명	| 단위 |
|:----------------------|:------|:-----|
| translate(x,y)	    | 요소의 위치를 X축으로 x만큼, Y축으로 y만큼 이동	      |   px, %, em 등   |
| translateX(n)	        | 요소의 위치를 X축으로 x만큼 이동	                     |  px, %, em 등    |
| translateY(n)	        | 요소의 위치를 Y축으로 y만큼 이동	                     |  px, %, em 등    |
| scale(x,y)	        | 요소의 크기를 X축으로 x배, Y축으로 y배 확대 또는 축소   |   0과 양수        |
| scaleX(n)	            | 요소의 크기를 X축으로 x배 확대 또는 축소	             |  0과 양수          |
| scaleY(n)	            | 요소의 크기를 Y축으로 y배 확대 또는 축소	             |  0과 양수          |
| skew(x-angle,y-angle)	| 요소를 X축으로 x 각도만큼, Y축으로 y 각도만큼 기울인다.	      |  +/- 각도(deg)    |
| skewX(x-angle)	    | 요소를 X축으로 x 각도만큼 기울인다.	                         | +/- 각도(deg)     |
| skewY(y-angle)	    | 요소를 Y축으로 y 각도만큼 기울인다.	                         | +/- 각도(deg)     |
| rotate(angle)	        | 요소를 angle만큼 회전	                                 | +/- 각도(deg)    |

##### 3D
{:.bigger}

|  속성	|  설명	 | 단위 |
|:----------------------|:------|:-----|
|  translate3d(x,y,z)	|  요소의 위치를 X축으로 x만큼, Y축으로 y만큼 Z축으로 z만큼 이동	    | px, %, em 등  |
|  translateX(n)	    |  요소의 위치를 X축으로 x만큼 이동	                                  | px, %, em 등  |
|  translateY(n)	    |  요소의 위치를 Y축으로 y만큼 이동	                                  | px, %, em 등  |
|  translateZ(n)	    |  요소의 위치를 Z축으로 z만큼 이동	                                  | px, %, em 등  |
|  scale3d(x,y)	        |  요소의 크기를 X축으로 x배, Y축으로 y배, Z축으로 z배 확대 또는 축소   |  0과 양수     |
|  scaleX(n)	        |  요소의 크기를 X축으로 x배 확대 또는 축소	                           | 0과 양수      |
|  scaleY(n)	        |  요소의 크기를 Y축으로 y배 확대 또는 축소	                           | 0과 양수      |
|  scaleZ(n)	        |  요소의 크기를 Z축으로 z배 확대 또는 축소	                           | 0과 양수      |
|  rotate3d(x,y,z)	    |  요소를 X축으로 x각도, Y축으로 y각도, Z축으로 z각도 회전	            | +/- 각도(deg) |
|  rotateX(x)	        |  요소를 X축으로 x각도 회전	                                      | +/- 각도(deg) |
|  rotateY(y)	        |  요소를 Y축으로 y각도 회전	                                      |  +/- 각도(deg) |
|  rotateZ(z)	        |  요소를 Z축으로 z각도 회전	                                      | +/- 각도(deg) |


---

### Transition
{:.bigger}

**화면 이동**{:.thin .text-blue-100}을 위한 점진적 효과

- `transition`{:.property}
    > 모든 transition 속성을 이용한 스타일을 한 줄에 설정할 수 있음.
    ```css
    transition: width 2s, height 2s, transform 2s;
    ```
    {:.list}
- `transition-delay`{:.property}
    > 전환 효과가 나타나기 전까지의 지연 시간을 설정
    ```css
    transition-delay: 1s;
    ```
    {:.list}
- `transition-duration`{:.property}
    > 전환 효과가 지속될 시간을 설정함.
    {:.list}
- `transition-property`{:.property}
    > 요소에 추가할 전환 효과를 설정함.
    {:.list}
- `transition-timing-function`{:.property}
    > 전환 효과의 시간당 속도를 설정함.<br>
    ```css
    transition-timing-function: ease-in-out;
    ```
    `linear`{:.property} 전환 효과가 처음부터 끝까지 일정한 속도로 진행됩니다.<br>
    `ease`{:.property} 기본값으로, 전환 효과가 천천히 시작되어, 그다음에는 빨라지고, 마지막에는 다시 느려집니다.<br>
    `ease-in`{:.property} 전환 효과가 천천히 시작됩니다.<br>
    `ease-out`{:.property} 전환 효과가 천천히 끝납니다.<br>
    `ease-in-out`{:.property} 전환 효과가 천천히 시작되어, 천천히 끝납니다.<br>
    `cubic-bezier(n,n,n,n)`{:.property} 전환 효과가 사용자가 정의한 cubic-bezier 함수에 따라 진행됩니다.<br>
    {:.list}


---

### Animation
{:.bigger}

##### animation 속성
{:.bigger}

- `animation-delay`{:.property} 엘리먼트가 로드되고 나서 언제 애니메이션이 시작될지 지정.
- `animation-direction`{:.property} 애니메이션이 종료되고 다시 처음부터 시작할지 역방향으로 진행할지 지정.
- `animation-duration`{:.property} 한 싸이클의 애니메이션이 얼마에 걸쳐 일어날지 지정한다.
- `animation-iteration-count`{:.property} 애니메이션이 몇 번 반복될지 지정. `infinite` : 무한히 반복
- `animation-name`{:.property} 이 애니메이션의 중간 상태를 지정. 중간 상태는  @keyframes 규칙을 이용.
- `animation-play-state`{:.property} 애니메이션을 멈추거나 다시 시작할 수 있다.
- `animation-timing-function`{:.property} 중간 상태들의 전환을 어떤 시간간격으로 진행할지 지정.
- `animation-fill-mode`{:.property} 애니메이션이 시작되기 전이나 끝나고 난 후 어떤 값이 적용될지 지정.
{:.list}

##### animation 작성법
{:.bigger}

```css
/* 단일 속성 */
.object {
  animation-name: 1s;
  animation-duration: 2s;
  animation-delay: 1s;
  animation-direction: alternate;
  animation-iteration-count: 3;
  animation-play-state: paused;
  animation-timing-function: 1s;
  animation-fill-mode: both;
}

/* 속기형 */
animation: name | duration | timing-function | delay | iteration-count | direction | fill-mode | play-state>[,...];
```


##### CSS Animation 장점
{:.bigger}

- 자바스크립트를 모르더라도 간단하게 애니메이션을 만들 수 있다.
- 자바스크립트를 이용한 애니메이션은 잘 만들어졌더라도 성능이 좋지 못할때 있으나, CSS 애니메이션은 frame-skipping 같은 여러 기술을 이용하여 최대한 부드럽게 렌더링된다.
- 브라우저는 애니메이션의 성능을 효율적으로 최적화할 수 있으며, 예를 들어 현재 안보이는 엘리먼트에 대한 애니메이션은 업데이트 주기를 줄여 부하를 최소화할 수 있다.


> 속도차이 : velocity.js **&gt;** css 애니메이션 **&gt;** jquery 애니메이션
{:.special}

##### velocity.js의 애니메이션 최적화 방법
{:.bigger}

- 레이아웃 스레싱을 최소화
- DOM 질의를 최소화 하기 위해 속성값을 캐싱
- px, em 같은 단위 변환 비율을 캐싱
- 업데이트가 시각적으로 판별할 수 없는 수준이면 스타일 업데이트 스킵

> [velocityjs](http://velocityjs.org/){:target="_blank"}<br>
[Make Your Website Interactive and Fun with Velocity.js (No jQuery)](https://www.sitepoint.com/how-to-use-velocity-js-without-jquery/){:target="_blank"}<br>
{:.list}


###  will-change 
{:.bigger}

##### 속성
{:.bigger}

> `auto`{:.property}  <br>
`scroll-position`{:.property}  <br>
`contents`{:.property}  <br>
`transform`{:.property}  <br>
`top, left`{:.property}  <br>
{:.list}


will-change를 사용하여 애니메이션 적용 대상을 브라우저가 알도록 하세요.
그러면 개발자가 변경을 수행하기 전에 브라우저를 최적화할 수 있다. 
그러나 will-change를 남용하지는 마세요. 그럴 경우 브라우저가 리소스를 낭비하여 더 많은 성능 문제를 야기할 수 있다.

일반적으로 사용자의 상호작용으로 또는 애플리케이션의 상태로 인해 그 다음 200ms 이내에 애니메이션이 트리거될 수 있는 경우, 애니메이션 요소에 will-change를 적용하는 것이 좋다. 대부분의 경우 앱의 현재 뷰에서 애니메이션을 적용할 모든 요소는 변경할 속성에 대해 will-change를 활성화해야 한다. 이전 가이드에서 사용한 상자 샘플의 경우, transform 및 opacity에 will-change를 추가하면 다음과 같게 됩니다.

```css
.box {
  will-change: transform, opacity;
}
```

##### 사용시 주의할 점
{:.bigger}

1. 너무 많은 속성과 요소에 will-change 속성을 사용하지 않는다.
2. 애니메이션 동작이 끝난 후 기본 상태로 되돌려야 한다
    브라우저가 변화에 최적화를 시도하면 일반적으로 비용이 발생한다 브라우저는 보통 필요한 경우에 최적화를 실시하고 최적화가 필요가 없으면 다시 원래되로 되돌아 옵니다. 
    하지만 will-change의 경우는 최적화를 길게 유지하게 됩니다. 그러므로 엘리먼트에 변경이 종료되면 반드시 will-change를 삭제해야 한다 
    그러면 will-change에 사용하고 있던 자원을 회수할 수 있다.
3. 조금 더 빨리 적용하려고 will-change를 사용해서는 안 됩니다.
    will-change를 사용하지 않아도 페이지가 잘 작동된다면 will-change를 사용하지 않아도 됩니다. 조금 더 빨리하기 위해 will-change 속성을 추가하면 과도한 메모리 사용과 더 복잡한 렌더링으로 성능이 더 안좋아 질 수 있는다.

```js
// 간단한 예제
// 클릭할 때 애니메이션을 재생할 엘리먼트를 선택한다
var el = document.getElementById('element');
// 엘리먼트에 마우스 커서가 올라가면 will-change를 설정한다
el.addEventListener('mouseenter', hintBrowser);
el.addEventListener('animationEnd', removeHint);
function hintBrowser() {
    // 애니메이션의 키프레임 블럭을 최적화할 수 있는 속성을 사용한다
    this.style.willChange = 'transform, opacity';
}
function removeHint() {
    this.style.willChange = 'auto';
}
```

단, 슬라이드처럼 수초 내에 반드시 변화가 일어나거나 마우스 움직임에 따라 변화가 일어나는 경우는 자바스크립트로 will-change로 삭제하지 않고 스타일시트에 바로 선언해도 문제 없다.

```css
.slide {
    will-change: transform;
}
```

---


### resize 
{:.bigger}

> 사용자의 **요소 크기 조정 권한**{:.thin .text-blue-100} 지정 <br>
textarea 변경 못하도록 고정하는 방법
{:.list}

- `none`{:.property}조정 불가. 기본값. 
- `both`{:.property} 높이와 너비 둘 다 조정 가능.
- `horizontal`{:.property} 너비만 조정 가능.
- `vertical`{:.property} 높이만 조정 가능.
- `initial`{:.property} 이 속성의 기본값으로 설정
- `inherit`{:.property} 부모 요소의 속성값 상속

```html
<div>
   <textarea class="noresize"></textarea>
</div>
```

```css
.noresize {
  resize: none; /* 사용자 임의 변경 불가 */
}
```

---

### outline
{:.bigger}

**border의 외곽선**{:.thin .text-blue-100}(border의 속성과 비슷)

- `outline-color`{:.property} 아웃라인 색상을 지정
- `outline-style`{:.property} 아웃라인 스타일을 지정 `none|hidden|dotted|dashed|solid|double|groove|ridge|inset|outset|initial|inherit`{:.special}
- `outline-width`{:.property} 아웃라인 너비를 지정 `medium|thin|thick|length|initial|inherit`{:.special}
- `outline-offset `{:.property} 테두리와 아웃라인 사이의 여백**{:.thin .text-blue-100}을 설정. `기본값 :  0`{:.special}
- `inherit`{:.property} 부모 요소로부터 값을 상속 받음
{:.list}


```css
div {
  border: 1px solid gray;
  outline: 2px solid red;
  outline-offset: 15px;
  outline-style: dotted; 
  outline-width: 5px;
}
```

##### 자바스크립트 문법

```js
object.style.outlineColor='#00FF00';
```

---


### columns

- `column-count`{:.property} 나눌 열 수를 지정 
- `column-gap`{:.property} 열 사이의 간격을 지정
- `column-rule-style`{:.property} 열 사이의 규칙 스타일을 지정
- `column-rule-width`{:.property} 열 사이의 규칙 색상을 지정
- `column-rule-color`{:.property} 칼럼 사이에 들어갈 라인의 색상을 설정
- `column-rule`{:.property} 스타일을 한 줄에 설정
- `column-span`{:.property} 요소가 얼마나 많은 열을 확장해야하는지 지정
- `column-width`{:.property} 열 너비를 지정
{:.list}

```css
#col {
    /* columns: <column-width> || <column-count>; */
    columns: 300px 2;
    column-gap: 2rem;
    column-rule: 1px solid #2196F3;
}
```

---

### background 
{:.bigger}

##### background-clip
{:.bigger}

> **요소의 배경이 테두리, 안쪽 여백, 콘텐츠 상자 중 어디까지 차지할 지**{:.thin .text-blue-100} 지정<br>
{:.list}
    - `border-box`{:.property} 배경이 테두리의 바깥 경계까지 차지한다 (Z축 순서 상 테두리 아래 위치)
    - `padding-box`{:.property} 배경이 안쪽 여백의 바깥 경계까지 차지한다. 테두리 밑에는 배경을 그리지 않는다.
    - `content-box`{:.property} 배경을 콘텐츠 상자에 맞춰 그린다.
    - `text`{:.property}  배경을 전경 텍스트 위에만 그린다.


```css
/* 키워드 값 */
background-clip: border-box;
background-clip: padding-box;
background-clip: content-box;
background-clip: text;

/* 전역 값 */
background-clip: inherit;
background-clip: initial;
background-clip: unset;
```

##### background-origin
{:.bigger}

> 배경 이미지를 **어느 영역부터 채워나갈지**{:.thin .text-blue-100}를 정한다.
{:.list}
- `border-box`{:.property} 테두리 영역 왼쪽 위부터 채운다.
- `padding-box`{:.property} 안쪽 여백 영역 왼쪽 위부터 채운다.
- `content-box`{:.property} 내용 영역 왼쪽 위부터 채운다.
- `initial`{:.property} 기본값으로 설정한다.
- `inherit`{:.property} 부모 요소의 속성값을 상속받는다.


##### background-size
{:.bigger}

> 배경 이미지 **크기가 어떻게 적용되는지**{:.thin .text-blue-100}를 정한다.
{:.list}
- `auto`{:.property}이미지 크기를 유지한다
- `length`{:.property}값을 두 개 넣으면 첫번째 값이 가로 크기, 두번째 값이 세로 크기. 값을 한 개 넣으면 가로 크기이며, 세로 크기는 원본 이미지의 가로 세로 비율에 맞게 자동으로 정해진다. 백분율을 사용할 수도 있다.
- `cover`{:.property}배경을 사용하는 요소를 다 채울 수 있게 이미지를 확대 또는 축소합니다. 가로 세로 비율을 유지한다.
- `contain`{:.property}배경을 사용하는 요소를 벗어나지 않는 최대 크기로 이미지를 확대 또는 축소합니다. 가로 세로 비율을 유지한다.
- `initial`{:.property}기본값으로 설정한다.
- `inherit`{:.property}부모 요소의 속성값을 상속받는다.


##### backgrobackground-attachment
{:.bigger} 

> 배경 이미지의 **스크롤 여부**{:.thin .text-blue-100}를 정한다.
{:.list}
- `scroll`{:.property}선택한 요소와 같이 움직인다. 내용을 스크롤하면 배경 이미지는 스크롤되지 않는다.
- `fixed`{:.property} 움직이지 않습니다.
- `local`{:.property} 선택한 요소와 같이 움직인다. 내용을 스크롤하면 배경 이미지도 스크롤된다.
- `initial`{:.property} 기본값으로 설정합니다.
- `inherit`{:.property} 부모 요소의 속성값을 상속받는다.


```css
div {
    background-image: url(image.jpg);
    background-position: 0 -100px;
    background-size: cover;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-origin: border-box;
    background-clip: padding-box;
    background-color: #333;
}

div {
    background: url('image.jpg') 0 -100px / contain no-repeat fixed border-box padding-box #333;
}
```


---

### counter
```css
body {
  counter-reset: section;        /* counter 이름 'section'으로 지정, 초깃값: 0 */
}

h3::before {
  counter-increment: section;    /* section의 카운터 값을 1씩 증가시킴. */
  content: counter(section);     /* section의 카운터 값을 표시. */
}
```

---

### @font-face
{:.bigger}

- 글꼴 파일을 html에 속에 삽입하여 사용자 컴퓨터에 설치되지 않은 글꼴을 서버에서 내려받아 사용할 수 있는 방법.
- 웹폰트를 쓸때 가장 유의해야 할 것이 브라우저간의 호환성이다
- `font-family`, `src`, `font-style`, `font-weight`, `unicode-range` 속성을 사용할 수 있다.

````css
@font-face Template
@font-face {
    font-family: 'MyWebFont';
    src: url('webfont.eot'); /* IE9 Compat Modes */
    src: url('webfont.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
    url('webfont.woff') format('woff'), /* Modern Browsers */
    url('webfont.ttf')  format('truetype'), /* Safari, Android, iOS */
    url('webfont.svg#svgFontName') format('svg'); /* Legacy iOS */
}

body {
    font-family: 'MyWebFont', Arial, sans-serif;
}
````

---


### Tip
{:.bigger}

##### 세로 가운데 정렬하는 방법

- margin 속성 이용하기
    ```css
    margin-left: auto;
    margin-right: auto;
    ```

-  display: table-cell 이용하기
    ```css
    #wrapper {
        display: table;
        width: 400px; 
        height: 400px;
    }
    
    #content {
        display: table-cell;
        vertical-align: middle;
    }
    ```

- line-height 속성 이용하기
    ```css
    #content {
        height: 240px;
        line-height: 240px;
    }
    ```
- position : absolute 속성 이용하기
    ```css
    #content {
        position: absolute;
        width: 100px;
        height: 100px;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        margin: auto;
    }
    ```
- float 속성 이용하기
    ```css
    #blank {
        float: left;
        height: 50%;
        margin-bottom: -50px;
    }
    
    #content {
        position: relative;
        clear: both;
        height: 100px;
    }
    ```

- transform 속성 이용하기
    ```css
    .centered { 
        position: absolute; 
        top: 50%; 
        transform: translateY(-50%); 
    }
    ```


##### 텍스트 마우스 드래그시 색상 변경

```css
::selection {
	background-color: #feffc3;
	color: #888888;
}
```

##### 구글 웹폰트를 빠르게 로드

*   단순히 CSS가 로드되기 전에 구글 폰트가 로드되길 원하고, 스타일되지 않은 텍스트가 번쩍거리지 않게 하려면, 웹 폰트 로더를 사용하라. 
    웹 폰트 로더는 사이트의 나머지가 로드되기 전에 로드하고, 스타일되지 않은 텍스트가 번쩍되는 것을 확실하게 피해준다. 

    ```html
    <script src="//ajax.googleapis.com/ajax/libs/webfont/1.4.7/webfont.js"></script>

    <script>
    WebFont.load({
        google: {
            families: ['Open Sans', 'Oswald']
            }
        });
    </script>
    ```

---

### 참고링크
- [CSS 가운데 정렬](https://webdir.tistory.com/31){:target="_blank"}
- [](http://tcpschool.com/css/css3_module_intro){:target="_blank"}
- [MAGIC EFFECTS](https://www.minimamente.com/project/magic/){:target="_blank"}
- [CSS3 Animation Cheat Sheet](http://www.justinaguilar.com/animations/index.html){:target="_blank"}
- [counter](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Lists_and_Counters/Using_CSS_counters){:target="_blank"}
- [CSS 방법론](https://velog.io/@pyo-dev/CSS-방법론){:target="_blank"}
- [BEM, SMACSS, OOCSS](https://medium.com/@jinminkim_50502/css-bem-smacss-oocss-9e4d6beb0a38){:target="_blank"}
- [CSS Flex(Flexible Box) 완벽 가이드](https://heropy.blog/2018/11/24/css-flexible-box/){:target="_blank"}
- [미래학자](https://futurists.tistory.com/60){:target="_blank"}
- [CSS 애니메이션(Animation), 키프레임(keyframes)](https://webclub.tistory.com/621){:target="_blank"}
- [애니메이션 및 성능](https://developers.google.com/web/fundamentals/design-and-ux/animations/animations-and-performance?hl=ko){:target="_blank"}
- [css로 고통 받 웹 개발자를 위한 작성가이드 smacss](https://blog.insightbook.co.kr/2016/01/26/css로-고통-받는-웹-개발자를-위한-작성-가이드-『smacss』/){:target="_blank"}
- [CSS / background-clip / 배경을 어디에 넣을지 정하는 속성](https://www.codingfactory.net/10582){:target="_blank"}