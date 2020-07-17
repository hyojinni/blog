---
layout: default
title: Typography
parent: Web Publishing
nav_order: 1
---

# Typography
{: .no_toc}
<!-- 읽기 편하고, 이해할 수 있으며, 읽기 쉬워야 합니다. -->


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

## HTML 텍스트 관련 태그

- `<p>`{:.property} 단락만들기
- `<br>`{:.property} 줄 바꾸기
- `<hr>`{:.property} 수평선 긋기
- `<blockquote>`{:.property} 인용문 넣기,  블럭 요소
- `<q>`{:.property} 인용 내용 표시,  인라인 요소
- `<strong>`{:.property} 강조할 텍스트 굵게 표시
- `<b>`{:.property} 텍스트 굵게 표시
- `<em>`{:.property} 강조할 텍스트 이탤릭체로 표시
- `<sub>`{:.property} 아래첨자 표시
- `<sup>`{:.property} 위 첨자 표시
- `<ins>`{:.property} 텍스트 아래 밑줄
- `<del>`{:.property} 텍스트 중간 밑줄
- `<mark>`{:.property} 형광펜 효과 내기
- `<span>`{:.property} 줄바꿈 없이 영역묶기
- `<small>`{:.property} 텍스트 작게 표시
- `<pre>`{:.property} 입력한 그대로 출력
- `<code>`{:.property} 컴퓨터 프로그래밍 코드 일부를 그래도 표시하고자 할 때
- `<kbd>`{:.property} 키보드 입력을 지정할 때
- `<samp>`{:.property} 컴퓨터 프로그램에서 샘플을 출력할 때
- `<var>`{:.property} 변수를 입력할 때
- `<cite>`{:.property} 작품의 명칭을 나타내는 요소
{:.block}


## 폰트 속성

- `font-style`{:.property}
- `font-variant`{:.property}
- `font-weight`{:.property}
- `font-size`{:.property}
- `line-height`{:.property}
- `font-family`{:.property}
{:.block}


## 폰트 단위

| 단위           | 설명                                                                                                   |
|:---------- ---|:-------------------------------------------------------------------------------------------------------|
| px            |절대값 단위, 기준값(font-size:16px)                                                                      |
| em            |부모태그의 영향을 받는 상대적 길이                                                                        |
| rem (root em) |최상위 요소인 html요소에 비례하여 크기를 가지는 상대적 길이                                                 |
| %             |사용자가 보이는 화면에서 차지하는 비중                                                                     |
| ex            |엘레먼트 폰트의 x(소문자) 사이즈 , 현재 폰트의 x-높이값 또는 em의 절반 값                                    |
| ch            |단위, 또는 글꼴 단위는 제로 문자인 0의 너비값의 고급 척도<br>`width: 40ch`는 40개의 문자열을 포함하고 있다는 뜻|

## 가독성 및 글자 수 제한

- 휴대 기기의 경우 :  30 ~ 40자 정도 사용
- 인쇄 및 데스크탑 : 60자 정도 사용

## 행간
- 줄과 줄 사이 간격 : 문자 높이 보다 약 30% 정도

## 색의 대비
- 작은 텍스트 : 배경 대비 **4.5 : 1** 이상
- 큰 텍스트 (예. 굵은 폰트 경우 14pt 이상, 일반의 경우 18pt 이상) : 배경 대비 **3 : 1** 이상



## 폰트 크기 

{:.h3-light}
### 폰트크기 정하는 속성

```css
font-size : medium | xx-small | x-small | small | large | x-large | xx-large | smaller | larger | length | initial | inherit
```
<div  class="code-example" markdown="1">
- `medium` : 웹브라우저에서 정한 기본 글자크기
- `xx-small`, `x-small`, `small`, `large`, `x-large`, `xx-large` : medium에 대한 상대적인 크기
- `smaller`, `larger` : 부모 요소의 글자 크기에 대한 상대적인 글자 크기
- `initial` : 기본값으로 설정
- `inherit` : 부모 요소의 속성값을 상속받음
{:.block}
</div>

{:.h3-light}
### 폰트 크기 비교 

#### Bootstrap vs Meterial

| Class          | Bootstrap                                      | Class     | Meterial                      | 
|:---------------|:-----------------------------------------------|:----------|:------------------------------|
|`.h1`           |40px  <span class="text-split-sm">2.5rem</span> | `h1`      |96px <span class="td-split-sm">letter-spacing: -1.5px</span> |
|`.h2`           |32px  <span class="text-split-sm">2rem</span>   | `h2`      |60px <span class="td-split-sm">letter-spacing: -0.5px</span> |
|`.h3`           |28px  <span class="text-split-sm">1.75rem</span>| `h3`      |48px <span class="td-split-sm">letter-spacing: 0px</span>    |
|`.h4`           |24px  <span class="text-split-sm">1.5rem</span> | `h4`      |34px <span class="td-split-sm">letter-spacing: 0.25px</span> |
|`.h5`           |20px  <span class="text-split-sm">1.25rem</span>| `h5`      |24px <span class="td-split-sm">letter-spacing: 0</span>      |
|`.h6`           |16px  <span class="text-split-sm">1rem</span>   | `h6`      |20px <span class="td-split-sm">letter-spacing: 0.15px</span> |
|`.display-1`    |96px  <span class="text-split-sm">6rem</span>   |`Subtitle` |16px <span class="td-split-sm">letter-spacing: 0.15px</span> |
|`.display-2`    |88px  <span class="text-split-sm">5.5rem</span> |`Body`     |16px <span class="td-split-sm">letter-spacing: 0.5px</span>  |
|`.display-3`    |72px  <span class="text-split-sm">4.5rem</span> |`Body2`    |14px <span class="td-split-sm">letter-spacing: 0.25px</span> |
|`.display-4`    |56px  <span class="text-split-sm">3.5rem</span> |`Button`   |14px <span class="td-split-sm">letter-spacing: 1.25px</span> |
|`<small>`       |80%                                             |`Caption`  |12px <span class="td-split-sm">letter-spacing: 0.4px</span>  |
|                |                                                |`Overline` |10px <span class="td-split-sm">letter-spacing: 1.5px</span>  |


#### JustTheDocs theme

|Selector  |font-size | Example |
|:---------|:---------|:--------|
| `h1`     |36px<span class="td-split-sm">small screen: 32px</span>|<span class="fs-8">Heading 1</span>|
| `h2`     |24px<span class="td-split-sm">small screen: 18px</span>|<span class="fs-6">Heading 2</span>|
| `h3`     |18px<span class="td-split-sm">small screen: 16px</span>|<span class="fs-5">Heading 3</span>|
| `h4`     |16px<span class="td-split-sm">small screen: 14px</span>|<span class="fs-2">Heading 4</span>|
| `h5`     |18px<span class="td-split-sm">small screen: 16px</span>|<span class="fs-3">Heading 5</span>|
| `h6`     |24px<span class="td-split-sm">small screen: 18px</span>|<span class="fs-2">Heading 6</span>|
| `.fs-1`  |10px<span class="td-split-sm">Small screen:  9px</span>|<span class="fs-1"> Font size 1 </span>|
| `.fs-2`  |12px<span class="td-split-sm">Small screen: 11px</span>|<span class="fs-2"> Font size 2 </span>|
| `.fs-3`  |14px<span class="td-split-sm">Small screen: 12px</span>|<span class="fs-3"> Font size 3 </span>|
| `.fs-4`  |16px<span class="td-split-sm">Small screen: 14px</span>|<span class="fs-4"> Font size 4 </span>|
| `.fs-5`  |18px<span class="td-split-sm">Small screen: 16px</span>|<span class="fs-5"> Font size 5 </span>|
| `.fs-6`  |24px<span class="td-split-sm">Small screen: 18px</span>|<span class="fs-6"> Font size 6 </span>|
| `.fs-7`  |32px<span class="td-split-sm">Small screen: 24px</span>|<span class="fs-7"> Font size 7 </span>|
| `.fs-8`  |38px<span class="td-split-sm">Small screen: 32px</span>|<span class="fs-8"> Font size 8 </span>|
| `.fs-9`  |42px<span class="td-split-sm">Small screen: 38px</span>|<span class="fs-9"> Font size 9 </span>|
| `.fs-10` |48px<span class="td-split-sm">Small screen: 42px</span>|<span class="fs-10">Font size 10</span>|

---

## 참고링크
- [웹디자인을 위한 타이포그라피 10가지 팁](http://koreawebdesign.com/typography-for-webdesign/){:target="_blank"}
- [반응형 웹을 위한 rem 단위로 디자인하기](https://indivdot.github.io/css/2016/03/26/emrem.html/){:target="_blank"}
- [당신은 모를 수도 있는 CSS의 7가지 단위](https://webdesign.tutsplus.com/ko/articles/7-css-units-you-might-not-know-about--cms-22573/){:target="_blank"}
- [CSS / font-size / 글자 크기 정하는 속성](https://www.codingfactory.net/10544){:target="_blank"}
- [Bootstrap](https://getbootstrap.com/docs/4.5/content/typography/){:target="_blank"}
- [Meterial](https://material.io/design/typography/the-type-system.html#type-scale/){:target="_blank"}
