---
layout: default
title: D3.js
parent: Web Tech
nav_order: 7
---

#  D3.js
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

### Basic
{:.bigger}

1. 데이터를 불러온다.
2. 작업할 공간을 선택한다.
3. 공간에 불러온 데이터를 연결(바인딩)한다.
4. 각각 연결한 것을 원하는대로 그린다.

```js
var dataset = [ 15, 5, 32, 20, 21 ];
d3.select("body") // body요소를 선택      
  .selectAll("p") // P태그를 가진 요소 전체 선택
  .data(dataset)  // 해당 태그와 dataset데이터를 바인딩(할당)         
  .enter()        // 바인드가 되지 않은 <p>요소에 데이터를 넣어 새로운 selection을 반환한다.          
  .append("p")    // 해당 데이터 공간 수 만큼 문서요소를 만든다.         
  .text("Hello!");// p 태그들에 text를 삽입한다. (생성된 P태그 만큼 P태그에 text를 삽입.)
                  // body에 p태그가 2개가 있고 생성된 P태그가 3개인 경우 - 5개의 P태그 중 3개 <p>Hello!</p> 생성됨
```

### Installation
{:.bigger}

##### NPM
{:.bigger}

```js
npm install --save d3
```
##### CDN
{:.bigger}

```js
<script src="https://d3js.org/d3.v5.js"></script>

// minified version
<script src="https://d3js.org/d3.v5.min.js"></script>
```

##### import
{:.bigger}

```js
import * as d3 from "d3";
```

### D3.js 동작과정
{.bigger}

- `Loading`{:.property} 시각적 요소를 그리기 전 보여주고자 하는 데이터를 불러온다.
- `Selecting-Bindin`{:.property} 시각적 요소 안에 데이터 수치를 입력한 코드에 맞춰 연동시킨다.
- `Transform`{:.property} 그래프의 유형, 색상, 축 등 다양한 요소 지정
- `Transition`{:.property} 클릭, 드래그 등 인터렉션 효과 지정

### D3.js method
{:.bigger}

- `d3.select()`{:.property} 현재 문서에서 특정 태그 하나를 선택하는 메서드
- `d3.selectAll()`{:.property} 특정 태그 전체를 선택
- `.data()`{:.property} 참조 연결할 데이터를 가져옴 (선택된 태그에 대한 데이터 매칭)
- `.enter()`{:.property} 데이터 개수 만큼 태그가 부족할때, 부족한 갯수만큼 플레이스 홀더를 반환
- `.append()`{:.property} 새로운 태그 추가
- `.exit()`{:.property} 종료 (더이상 필요없는 태그 반환)
- `.remove`{:.property} 현재 문서에서 선택된 태그를 제거 


##### 축(Axis) 함수
- `d3.axisLeft()`{:.property} 왼쪽 수직 축을 생성
- `d3.axisRight()`{:.property} 세로 방향의 오른쪽 축을 생성
- `d3.axisBottom()`{:.property} 하단 수평 축을 생성
- `d3.axisTop()`{:.property} 상단 수평 축을 생성

```js
const xAxis = d3
    .axisBottom(x)
    .ticks(4)
    .tickFormat(d3.timeFormat("%b %d"));

const yAxis = d3
    .axisLeft(y)
    .ticks(4)
    .tickFormat(d => d + "m");
```

##### .scaleLinear()
```js
 d3.scaleLinear()
    .domain([참조최소값, 참조최대값])
    .range([출력최소값, 출력최대값]);
```

<u>설명</u>

```js
// 0 부터 5까지 표현할 수 있다면 0부터 500까지 있는 데이터 중에 100 이라면 1과 매칭 시켜준다.
d3.scale().linear.domain([0, 500]).range([0, 5]);

//인자로 `data`(=d)를 받아 `data`를 반환하는 함수이므로 dataArray에 있는 값이 width 가 된다.
.attr("width", function(d) {return d;})

// `data`(=d)와` index`(=i)를 같이 받아`y` 값을 `index` * 60으로 반환
.attr('y', function (d, i) { return i * 60 });
```



---

## 참고링크
- [github : D3.js](https://github.com/d3/d3){:target="_blank"}
- [D3.js 기본 문법 정리](https://jeong-pro.tistory.com/149){:target="_blank"}
- [D3.js 쉽게 시작하세요](https://mynameisdabin.tistory.com/15){:target="_blank"}
- [D3.js 기본함수](https://ddiri01.tistory.com/316){:target="_blank"}
- [D3.js 배우는 방법](https://mobicon.tistory.com/275){:target="_blank"}
- [D3JS 기본 개념 및 API](https://pa-pico.tistory.com/2){:target="_blank"}
- [D3.js API Reference](https://github.com/zziuni/d3/wiki/API-Reference){:target="_blank"}
- [Data-Visualizing-D3.js-란](https://velog.io/@smooth97/-Data-Visualizing-D3.js-란){:target="_blank"}



