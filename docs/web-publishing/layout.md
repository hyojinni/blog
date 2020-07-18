---
layout: default
title: Layout
parent: Web Publishing
nav_order: 7
---

# Layout
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---
## Layout Utilities 비교


### Bootstrap
{:.bigger}

##### 여백
{:.bigger }

| prefix | 속성   | prefix | 속성     |
|:-------|:-------|:------|:---------|
| `.m-`  | `margin`                      | `.p-` | `padding`                        |
| `.mx-` | `margin-left`, `margin-right` | `.px-`| `padding-left`, `padding-right`  |
| `.my-` | `margin top`, `margin bottom` | `.py-`| `padding top`, `padding bottom`  |
| `.mt-` | `margin-top`                  | `.pt-`| `padding-top`                    |
| `.mr-` | `margin-right`                | `.pr-`| `padding-right`                  |
| `.mb-` | `margin-bottom`               | `.pb-`| `padding-bottom`                 |
| `.ml-` | `margin-left`                 | `.pl-`| `padding--left`                  |

기본값 : `1rem = 16px` 

| Spacer/suffix  |    rem    |     px     |(-) Spacer/suffix|   rem     |   px    |
|:---------------|:----------|:-----------|:----------------|:----------|:--------|
| `0`            | 0         | 0          | `n1`            | -0.25rem  | -4px    |
| `1`            | 0.25rem   | 4px        | `n2`            | -0.5rem   | -8px    |
| `2`            | 0.5rem    | 8px        | `n3`            | -1rem     | -16px   |
| `3`            | 1rem      | 16px       | `n4`            | -1.5rem   | -24px   |
| `4`            | 1.5rem    | 24px       | `n5`            | -3rem     | -48px   |
| `5`            | 3rem      | 48px       |||
| `auto`         | auto      | auto       |||


##### 정렬(FLEX)
{:.bigger }

###### 수평
{:.bigger}

* 모든 flex-클래스 `flex-` 의  상위요소에는 `d-flex` 적용되어야 한다.

| Classname                  | 속성                             |
|:---------------------------|:---------------------------------|
| `.justify-content-start`   | `justify-content: flex-start`    |
| `.justify-content-end`     | `justify-content: flex-end`      |
| `.justify-content-center`  | `justify-content: center`        |
| `.justify-content-between` | `justify-content: space-between` |
| `.justify-content-around`  | `justify-content: space-around`  |


###### 수직
{:.bigger}

| Classname              | 속성                      |
|:-----------------------|:--------------------------|
| `.align-items-start`   | `align-items: flex-start` |
| `.align-items-end`     | `align-items: flex-end`   |
| `.align-items-center`  | `align-items: center`     |
| `.align-items-baseline`| `align-items: baseline`   |
| `.align-items-stretch` | `align-items: stretch`    |

* 아이템 개별 정렬은 수직 정렬만 있고 수평정렬은 없다.<br>
  - `.align-self-start` 
  - `.align-self-end` 
  - `.align-self-center` 
  - `.align-self-baseline` 
  - `.align-self-stretch`
 {:.block}


---

### JustTheDocs
{:.bigger}

##### 여백
{:.bigger }

| prefix |               속성            | prefix|               속성               |
|:-------|:------------------------------|:------|:---------------------------------|
| `.m-`  | `margin`                      | `.p-` | `padding`                        |
| `.mx-` | `margin-left`, `margin-right` | `.px-`| `padding-left`, `padding-right`  |
| `.my-` | `margin top`, `margin bottom` | `.py-`| `padding top`, `padding bottom`  |
| `.mt-` | `margin-top`                  | `.pt-`| `padding-top`                    |
| `.mr-` | `margin-right`                | `.pr-`| `padding-right`                  |
| `.mb-` | `margin-bottom`               | `.pb-`| `padding-bottom`                 |
| `.ml-` | `margin-left`                 | `.pl-`| `padding--left`                  |


기본값 : `1rem = 16px` 

| Spacer/suffix  | rem       | px     |
|:---------------|:----------|:-------|
| `1`            | 0.25rem   | 4px    |
| `2`            | 0.5rem    | 8px    |
| `3`            | 0.75rem   | 12px   |
| `4`            | 1rem      | 16px   |
| `5`            | 1.5rem    | 24px   |
| `6`            | 2rem      | 32px   |
| `7`            | 2.5rem    | 40px   |
| `8`            | 3rem      | 48px   |
| `auto`         | auto      | auto   |

* 가로로 가운데 배치 : `mx-auto` 


```css
class="mb-4"
margin-bottom : 1rem 
margin-bottom : 16px
```

##### 정렬
{:.bigger }

###### 수평
{:.bigger}

| Classname               | 속성                             |
|:------------------------|:---------------------------------|
| `.float-left`           | `float: left`                    |
| `.float-right`          | `float: right`                   |
| `.flex-justify-start`   | `justify-content: flex-start`    |
| `.flex-justify-end`     | `justify-content: flex-end`      |
| `.flex-justify-between` | `justify-content: space-between` |
| `.flex-justify-around`  | `justify-content: space-around`  |

* 모든 flex-클래스 `flex-` 의  상위요소에는 `d-flex` 적용되어야 한다.


###### 수직
{:.bigger}

| Classname              | 속성                    |
|:-----------------------|:--------------------------------|
| `.v-align-baseline`    | `vertical-align: baseline`      |
| `.v-align-bottom`      | `vertical-align: bottom`        |
| `.v-align-middle`      | `vertical-align: middle`        |
| `.v-align-text-bottom` | `vertical-align: text-bottom`   |
| `.v-align-text-top`    | `vertical-align: text-top`      |
| `.v-align-top`         | `vertical-align: top`           |


##### Display
{:.bigger }

| Class             | 속성                     |
|:------------------|:------------------------|
| `.d-block`        | `display: block`        |
| `.d-flex`         | `display: flex`         |
| `.d-inline`       | `display: inline`       |
| `.d-inline-block` | `display: inline-block` |
| `.d-none`         | `display: none`         |

* 반응형 클래스와 함께 사용한다
  ```markdown
  이 단추는 중간 화면 크기(740px)이 될 때까지 숨겨집니다.
  <button class="d-none d-md-inline-block">확인</button>
  ```


---

## Grid

##### Bootstrap
{:.bigger}

```html
<div class="row">
  <div class="col-*-*"></div>
</div>
<div class="row">
  <div class="col-xs-6">xs-6</div>
  <div class="col-xs-4">xs-4</div>
  <div class="col-xs-2">xs-4</div>
</div>
<div class="row">
  <div class="col-*-*"></div>
  <div class="col-*-*"></div>
  <div class="col-*-*"></div>
</div>
<div class="row">
  ...
</div>
```

| Class prefix |	           | Screen size  |  매체유형  |
|:-------------|:------------|:-------------|:----------|
| `.col-xs-●`  |	`●`  1~12  | <768px       |  Mobile   |
| `.col-sm-●`  |	`●`  1~12  | ≥768px       |  Tablet   |
| `.col-md-●`  |	`●`  1~12  | ≥992px       |  Desktop  |
| `.col-lg-●`  |  `●`  1~12  | ≥1200px      |           |


```html
<body>
  <div class="col-md-4">화면크기의 1/3 너비</div>
  <div class="col-md-8">화면크기의 2/3 너비</div>
</body>
```

---

## Responsive

##### Media Query 문법
{:.bigger}

* 내부 
  ```css
  @media only|not 매체유형 and (표현식) { CSS스타일코드; }
  ```
* 외부 CSS 파일에 미디어 쿼리를 따로 저장

  ```html
  <link rel="stylesheet" media="매체유형 and|only|not (표현식)" href="CSS파일URL"/>
  ```

##### Media Query 속성
{:.bigger}

- `width`{:.property}	화면의 너비
- `height`{:.property}	화면의 높이
- `device-width`{:.property}	매체 화면의 너비
- `device-height`{:.property}	매체 화면의 높이
- `devie-aspect-ratio`{:.property}	매체 화면의 비율
- `orientation`{:.property}	매체 화면의 방향
- `color`{:.property}	매체의 색상 비트 수
- `color-index`{:.property}	매체에서 표현 가능한 색상의 개수
- `monochrome`{:.property}	흑백 매체에서의 픽셀당 비트 수
- `resolution`{:.property}	매체의 해상도
{:.list}

##### 매체유형
{:.bigger}

- `all`{:.property}	모든 매체.
- `print`{:.property}	프린터 기기.
- `screen`{:.property}	컴퓨터나 태블릿, 스마트폰 등 스크린(screen)이 있는 매체.
- `speech`{:.property}	웹 페이지를 읽어주는 스크린 리더(screenreader).
{:.list}



### Bootstrap
{:.bigger}


##### Media Query
{:.bigger}

```css
/* Small devices (tablets, ≥ 768px) */
@media (min-width: @screen-sm-min) {/* ... */}

/* Medium devices (desktops, ≥ 992px) */
@media (min-width: @screen-md-min) {/* ... */}

/* Large devices (large desktops, ≥ 1200px) */
@media (min-width: @screen-lg-min) {/* ... */}

```

##### Responsive Images
{:.bigger}

```css
.img-responsive {
  display: block;
  max-width: 100%;
  height: auto;
}
```


| class     | Screen size           |
|:----------|:----------------------|
| `.col-`   | none(auto) < 576px    |
| `.col-sm` | 540px ≥ 576px         |
| `.col-md` | 720px ≥ 768px         |
| `.col-lg` | 960px ≥ 992px         |
| `.col-xl` | 1140px ≥ 1200px       |


### Material
{:.bigger}

| class     | Screen size          |
|:----------|:---------------------|
| `.xs`     | 0px ~ 600px          |
| `.sm`     | 600px ~ 960px        |
| `.md`     | 960px ~ 1280px       |
| `.lg`     | 1280px ~ 1920px      |
| `.xl`     | 1920px ~             |


### JustTheDocs
{:.bigger}

| class     | Screen size             |
|:----------|:------------------------|
| `xs`      | ≥ 320px (20rem)         |
| `sm`      | ≥ 500px (31.25rem)      |
| `md`      | ≥ 740px (46.25rem)      |
| `lg`      | ≥ 1120px (70rem)        |
| `xl`      | ≥ 1400px (87.5rem)      |


---

## 참고링크
- [부트스트랩 공백](https://minaminaworld.tistory.com/136){:target="_blank"}
- [Responsive Web Design with Bootstrap](https://medium.com/@duncandevs/responsive-web-design-with-bootstrap-70147ecd9d98){:target="_blank"}
- [](https://poiemaweb.com/bootstrap-grid-system){:target="_blank"}
- [](https://www.sitepoint.com/responsive-web-design-tips-bootstrap-css/){:target="_blank"}
- [미디어 쿼리](http://tcpschool.com/css/css3_expand_mq){:target="_blank"}