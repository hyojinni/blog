---
layout: default
title: Form
parent: Web Publishing
nav_order: 6
---

# Form
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

## Form 

```html
 <form action="URL경로" target="_self" target="_blank" method="get">
    ID: <input type="text" name="id" value="1"><br>
    username: <input type="text" name="username" value="val"><br>
    <input type="submit" value="전송">
  </form>
```
* `name`{:.property} 폼의 이름<br>
* `action`{:.property} 폼의 정보가 전달될 주소<br>
* `value`{:.property} 속성 값, key=value 형태로 전송<br>
* `get`{:.property} 넘겨지는 값이 보임, 보안에 취약<br>
* `method`{:.property} 데이터를 전달하는 방식을 정의하는 부분<br>
* `post`{:.property} 노출이 되지 말아야 할 데이터들 전송<br>
* `accept-charset`{:.property} 데이터의 문자셋 변경해서 전송하기<br>
* `target`{:.property} `_self` 이벤트가 일어난 페이지에서 열리게 됨,
                       `_blank` 새로운 탭이나 팝업으로 별도의 창에서 열림
{:.block}

## fieldset / legend
```html
<form>
  <fieldset>
    <legend>Login</legend>
    Username <input type="text" name="username">
    Password <input type="text" name="password">
    <input type="submit">  
  </fieldset>
</form>
```
* `filedset`{:.property} 관련된 입력양식들을 그룹화<br>
* `legend`{:.property} fieldset태그 내에서 사용되어야 하며, fieldset의 제목을 정의<br>
{:.block}


## input 


|타입     | HTML5추가   | 설명   |
|:--------|:------:||:------|
|`type="button"`        | | 버튼생성 |
|`type="checkbox"`      | | checkbox 생성 |
|`type="color"`         |●| 컬러 선택 생성 |
|`type="date"`          |●| date control (년월일) 생성 |
|`type="datetime-local"`|●| 지역 date & time control (년월일시분초) 생성 |
|`type="email"`         |●| 이메일 입력, subumit 시 자동 검증한다. |
|`type="file"`          | | 파일 선택  |
|`type="hidden"`        | | 감추어진 입력 |
|`type="image"`         | | 이미지로 된 submit button 생성 |
|`type="month"`         |●| 월 선택 |
|`type="number"`        |●| 숫자 입력, 브라우저 지원안됨 |
|`type="password"`      | | password 입력  |
|`type="radio"`         | | radio button 생성 |
|`type="range"`         |●| 범위 선택 |
|`type="reset"`         | | 초기화 |
|`type="search"`        |●| 검색어 입력 |
|`type="submit"`        | | 제출 button 생성 |
|`type="tel"`           |●| 전화번호입력,브라우저에 실행안됨 |
|`type="text"`          | | 텍스트입력 |
|`type="time"`          |●| 시간선택 |
|`type="url"`           |●| URL입력 |
|`type="week"`          |●| 주선택입력 |

```html
<label for="id">이름: <input type="text" id="id"></label>
```
* `<label>`{:.property} 제목이나 이름<br>
* `for`{:.property} for의 값과 양식의 id의 값이 같으면 연결. <br>
*input 등 양식을 label로 감싸면 id와 for가 없이도 같은 결과를 얻을 수 있습니다.
{:.block}

```html
<input type="checkbox" name="fruit1" value="apple" checked> 사과
<input type="color" name="mycolor">
<input type="datetime-local" name="birthdaytime">
<input type="email" name="useremail">
<input type="file" name="myfile">
<input type="date" name="birthday">
<input type="hidden" name="country" value="Norway">
<input type="image" src="img/img_submit.gif" alt="Submit" width="48" height="48">
<input type="month" name="birthdaymonth">
<input type="password" name="pwd">
<input type="radio" name="gender" value="male" checked> 남자
<input type="range" name="points" min="0" max="10" step="1" value="5">
<input type="reset">
<input type="search" name="googlesearch">
<input type="submit" value="Submit">
<input type="tel" name="mytel">
<input type="text" name="myname">
<input type="time" name="mytime">
<input type="url" name="myurl">
<input type="week" name="week_year">
```



## select 

```html
<select name="fruits"  size="2" multiple autofocus>
  <option value="apple" selected>사과</option>
  <optgroup label="mango">
     <option value="appleMango">애플망고</option>
     <option value="greenMango">그린망고</option>
  </optgroup>
  <optgroup label="orange" disabled>
    <option value="navelOrange">네이블 오렌지</option>
    <option value="valenciaOrange">발렌시아 오렌지</option>
  </optgroup>
  <option value="strawberry" disabled>딸기</option>
  <option value="banana">바나나</option>
  <option value="watermelon">수박</option>
</select>
```
* `name`{:.property} 드롭다운 목록의 이름<br>
* `value`{:.property} option 요소의 속성 값, key=value 형태로 전송<br>
* `optgroup`{:.property} option을 그룹화<br>
* `selected`{:.property} 기본으로 지정하고 싶은 값<br>
* `disabled`{:.property} 비활성화<br>
* `multiple`{:.property} 두 개 이상의 옵션을 동시에 선택<br>
* `size`{:.property} 드롭다운 목록에서 보이는 옵션의 개수<br>
* `autofocus`{:.property} 자동으로 포커스 됨. html새로 추가된 속성<br>
* `required`{:.property} 전송전에 선택이 필수임을 지정. 주요브라우저에서 지원안됨<br>
* `form`{:.property} select영역이 속한 form의 id. &lt;select form="formID"&gt;
{:.block}

## textarea 

```html
<textarea name="message" rows="10" cols="30" placeholder="Input some text">Write something here</textarea>
```
* `cols`{:.property} 가로 크기<br>
* `rows`{:.property} 세로 크기<br>
* `placeholder`{:.property} 안내 문구<br>
* `readonly`{:.property} 읽기만 가능<br>
* `disabled`{:.property} 비활성화<br>
{:.block}

## button

```html
<button type="button">Click Me!</button>
<input type="submit" value="전송">
```
* `autofocus`{:.property} 자동으로 포커스 됨<br>
* `disabled`{:.property} 비활성화<br>
* `type="submit"`{:.property} 양식을 전송할 때 사용하면 별도의 자바스크립트 없이 자동으로 전송<br>
{:.block}


## datalist
```html
<input list="browsers"> 
<datalist id="browsers"> 
  <option value="Internet Explorer"> 
  <option value="Firefox"> 
  <option value="Chrome"> 
  <option value="Opera"> 
  <option value="Safari"> 
</datalist>
```
* `<datalist>`{:.property}  html5에 새로 추가된 요소. 텍스트 필드 형태로 제공. autocomplete와 비슷
{:.block}

## meter 
```html
<meter value="2" min="0" max="10">2</meter>
<meter value="0.6">60%</meter>
```
* `<meter>`{:.property}  html5에 새로 추가된 요소. 계기(METER gauge)를 표시
{:.block}

## progress

```html
<progress value="5000" max="10000"> 
  <span id="status">50</span>% 
</progress>
```
* `<progress>`{:.property}  진행 상태(PROGRESS)를 표시. 현재값이 없으면 진행 상태 바가 나타나지 않는다.
{:.block}

## output
```html
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">
0 <input type="range" id="a" value="50">100 
+ <input type="number" id="b" value="50"> 
= <output name="x" for="a b"></output> </form>
</form>
```
* `<meter>`{:.property}  html5에 새로 추가된 요소. 계산 결과(OUTPUT)를 표시
{:.block}



## 참고링크
- [사용자와의 커뮤니케이션을 위한 폼 태그](https://poiemaweb.com/html5-tag-forms){:target="_blank"}
- [버튼 요소](https://developer.mozilla.org/ko/docs/Web/HTML/Element/button){:target="_blank"}
- [HTML / textarea / 여러 줄의 문자열을 입력할 수 있는 양식](https://www.codingfactory.net/11611){:target="_blank"}
- [폼(Form) 요소](https://webdir.tistory.com/320){:target="_blank"}