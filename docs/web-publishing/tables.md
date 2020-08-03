---
layout: default
title: Tables
parent: Web Publishing
nav_order: 4
---

# Tables
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

### 기본문법
{:.bigger}

```html
<table>
  <caption>전 세계 웹 브라우저 점유율</caption>
  <colgroup>
      <col>
      <col style="width:60%" span="1" class="bg">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">웹브라우저</th>
      <th scope="col">점유율</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Chrome</td>
      <td>69.35%</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td>Total</td>
      <td>100%</td>
    </tr>
  </tfoot>
</table>
```

* `caption`{:.property} table 요소에 제목이나 설명을 마크업할 때 사용하는 요소
* `col`{:.property} 테이블의 열 그룹
* `head`{:.property}, `tbody`{:.property}, `tfoot`{:.property} 요소는 테이블의 행 그룹
* `span`{:.property} 한번에 속성 지정할 열 개수.(기본값: 1) 
{:.block}

---

### 반응형 테이블
{:.bigger}

##### 일정비율로 축소하는 방법
{:.bigger}

- `width`를 **%**로 지정해서 기기에 맞춰 보여준다.

##### 테이블을 스크롤해서 보는 방법
{:.bigger}

- 외부 `div` **overflow-x:auto**로 감싸서  가로로 스크롤해서 내용을 보여준다.
- 기기마다 스크롤이 있는지 확인이 어려운 단점이 있다. 

```css
  .scrollable.has-scroll > div {
    overflow-x:auto;
  }
  .scrollable.has-scroll:after {
    position:absolute;
    top:0;
    left:100%;
    width:50px;
    height:100%;
    border-radius:10px 0 0 10px / 50% 0 0 50%;
    box-shadow:-5px 0 10px rgba(0, 0, 0, 0.25);
    content:'';
  }
```

- `-WebKit` 브라우저 에서 스크롤 할 때까지 스크롤 막대가 잘 보이지 않기 때문에 명시 적으로 표시

```css
.scrollable > div::-webkit-scrollbar {
	height:12px;
}
.scrollable > div::-webkit-scrollbar-track {
	box-shadow:0 0 2px rgba(0,0,0,0.15) inset;
	background:#f0f0f0;
}
.scrollable > div::-webkit-scrollbar-thumb {
	border-radius:6px;
	background:#ccc;
}
```

##### 제목행 고정 스크롤 방법
{:.bigger}

```css
.rwd-table tbody {
    display: flex;
    position: relative;
    overflow-x: auto;
    overflow-y: hidden;
}
```

Link : [CSS only Responsive Tables](https://codepen.io/dbushell/full/8e6a1ee85418f3c5abe839647dbcdec5/){:target="_blank"}




---

## 참고링크
- [colgroup](https://developer.mozilla.org/ko/docs/Web/HTML/Element/colgroup){:target="_blank"}
- [반응형웹에서 데이터 테이블 표현하기](https://iropke.com/archive/data-table.html){:target="_blank"}
- [반응형테이블코딩](https://blog.naver.com/PostView.nhn?blogId=nsoft21&logNo=221578578071&parentCategoryNo=&categoryNo=14&viewDate=&isShowPopularPosts=true&from=search){:target="_blank"}
- [Responsive scrollable tables](https://www.456bereastreet.com/archive/201309/responsive_scrollable_tables/){:target="_blank"}
- [CSS only Responsive Tables](https://dbushell.com/2016/03/04/css-only-responsive-tables/){:target="_blank"}
