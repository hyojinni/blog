---
layout: default
title: HTML5
parent: Web Tech
nav_order: 3
---

# HTML5
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

### details


```html
<details>
    <summary>접기/펼치기</summary>
    <p>내부에 넣을 내용을 입력해주세요</p>
</details>
```

<details>
    <summary>접기/펼치기</summary>
    <p>내부에 넣을 내용을 입력해주세요</p>
</details>

---

### audio

```html
<audio>
  <source src="test.mp3" type="audio/mp3" />
</audio>
```
- `volume`{:.property} 소리의 크기를 결정
- `autoplay`{:.property} 자동시작
- `muted`{:.property} 음소거
- `preload`{:.property} 페이지 로드시 audio를 미리 로딩하기 위함
- `src`{:.property} 소스파일 경로
- `loop`{:.property} 반복하여 재생하기
{:.list}

---

### canvas

```html
<canvas id="biew" width="300" height="500"></canvas>
```

----

### menu, command
- `menu`{:.property}  목록과 메뉴를 정의하는 태그
- `command`{:.property}  사용자가 호출할수 있는 명령을 지정하는데 사용하는 명령 지정 태그
- 지원 브라우저 미흡

```html
<menu>
    <command type="command | checkbox | radio" label="Save" onclick="save()">Save</command>
</menu>
```

---

### datalist

```html
<form>
    <input list="browsers">
    <datalist id="browsers">
        <option value="Internet Explorer">인터넷 익스플로러
        </option><option value="Firefox">파이어폭스
        </option><option value="Chrome">크롬
        </option><option value="Opera">오페라
        </option><option value="Safari">사파리
    </option></datalist>
</form> 
```

---

### embed

```html
<embed type="video/quicktime" src="music.mp3" wmode="transparent">
```

- `src`{:.property}  포함하고자 하는 외부 자원의 주소 지정
- `type`{:.property}  인스턴스화 할 플러그인의 유효한 MIME 타입 지정
- `width`{:.property}  	요소의 너비 정의
- `height`{:.property}  	요소의 높이 정의

**wmode**
- `window`{:.property}  Flash Movie 를 맨 위에 놓게 된다. (기본값)
- `opaque`{:.property}  Movie 아래의 모든 것을 가리게 된다. 위에 레이어를 올릴 수 있다.
- `transparent`{:.property}  Movie를 투명하게 하여 뒤의 html 부분을 보여준다.

---

### hgroup

```html
<hgroup>
    <h1>h1태그</h1>
    <h2>h2태그</h2>
</hgroup>
```
- 태그영역 h1 ~ h6 요소들을 그룹짓기 위해 사용

----

### mark
```html
<p>Free copy/paste <mark>HTML</mark> codes for your website. Simply copy then paste the <mark>HTML</mark> code to your own website.</p>
```
- 인용구의 특정한 부분으로 주의를 환기시키기 위해 mark 요소를 사용
- "구문 강조"와는 다른 의미로 구문 강조에 쓰기엔 span 요소가 좀 더 적절
- 텍스트에서 "중요성"(strong)을 나타내는 것과 "연관성"(mark)을 나타내는 것의 차이가 있다. 

---


## 참고링크
[html5에서 새롭게 추가된 태그모음](https://www.biew.co.kr/entry/html5에서-새롭게-추가된-태그모음){:target="_blank"}