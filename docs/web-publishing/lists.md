---
layout: default
title: Lists
parent: Web Publishing
nav_order: 5
---

# Lists
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---
## 종류

### 순서없는 목록

```html
<ul>
  <li></li>
  <li></li>
  <li></li>
</ul>
```

### 순서있는 목록 

```html
<ol>
  <li></li>
  <li></li>
  <li></li>
</ol>
```

### 설명있는 목록

<div class="code-example" markdown="1">
<dl>
  <dt>이름</dt>
  <dd>홍길동</dd>
  <dt>출생년도</dt>
  <dd>1443년</dd>
  <dt>출생지</dt>
  <dd>한국</dd>
</dl>
</div>
```html
<dl>
  <dt>이름</dt>
  <dd>홍길동</dd>
  <dt>출생년도</dt>
  <dd>1443년</dd>
  <dt>출생지</dt>
  <dd>한국</dd>
</dl>
```

## 목록속성 CSS

##### 기본 설정 제거

```css
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
```

##### list-style-type
- `disc`{:.property} ●
- `circle`{:.property} ○
- `square`{:.property} ■
- `decimal`{:.property} 1. 2. 3...
- `decimal-leading-zero`{:.property} 01. 02....10. 11.
- `lower-roman`{:.property}
- `upper-roman`{:.property}
- `lower-greek`{:.property}
- `lower-latin`{:.property}
- `upper-latin`{:.property}
- `armenian`{:.property}
- `georgian`{:.property}
- `lower-alpha`{:.property} a. b. c...
- `upper-alpha`{:.property} A. B. C...
- `none`{:.property}
{:.list}


[샘플보기](https://codepen.io/impressivewebs/pen/fKjFL){:target="_blank"}


##### list-style-image

```css
ul {
  list-style-image: url('arrow.gif');
}
```

##### list-style-position
- `outside`{:.property}
- `inside`{:.property}

```css
ul {
  list-style-position: outside;
}
```



---

## 참고링크
- [list-style](https://css-tricks.com/almanac/properties/l/list-style/){:target="_blank"}