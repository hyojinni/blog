---
layout: default
title: D3.js
parent: Web Tech
nav_order: 7
---

#  D3.js
{: .no_toc }

## 기본문법

1. 데이터를 불러온다.
2. 작업할 공간을 선택한다.
3. 공간에 불러온 데이터를 연결(바인딩)한다.
4. 각각 연결한 것을 원하는대로 그린다.

```js
var dataset = [ 15, 5, 32, 20, 21 ];
d3.select("body")          
  .selectAll("p")          
  .data(dataset)           
  .enter()                 
  .append("p")             
  .text("hi jeongpro!");   
```

## Installation

### NPM

```js
npm init
NPM install D3: npm install --save d3
```
### CDN

```js
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/d3/5.16.0/d3.min.js"></script>
```


----

## 참고링크
- [](https://riptutorial.com/d3-js){:target="_blank"}
- [](https://mobicon.tistory.com/275){:target="_blank"}
- [D3.js 기본 문법 정리] (https://jeong-pro.tistory.com/149){:target="_blank"}