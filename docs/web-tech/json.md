---
layout: default
title: json
parent: Web Tech
nav_order: 5
---

#  json
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

##  기본문법


1. JSON 데이터는  이름과 값의 쌍으로 이루어짐
2. JSON 데이터는 쉼표(**,**{:.text-purple-000})로 나열됨.
3. 객체(object)는 중괄호(**{}**{:.text-purple-000})로 둘러쌓아 표현함.
4. 배열(array)은 대괄호(**[]**{:.text-purple-000})로 둘러쌓아 표현함.

#### Object

<div  class="code-example" markdown="1">
myCat **.** name : "Meowsalot" <br>
myCat **.** species : "tuna"
{:.text-purple-200}
</div>

```json
var myCat = {
'name' : 'Meowsalot',
'species' : 'cat',
'favoriteFood': 'tuna'
}
```
#### Array
<div  class="code-example" markdown="1">
myFavColors[1];<br>
"green"
{:.text-purple-200}
</div>

```json
var myFavColors = ['blue', 'green', 'purple'];
```

#### Arrays + Objects

<div  class="code-example" markdown="1">
thePets[1] **.** favoriteFood;<br>
"carrots"
{:.text-purple-200}
</div>

```json
var thePets = [
  {
    'name' : 'Meowsalot',
    'species' : 'cat',
    'favoriteFood': 'tuna'
  },{
    'name' : 'Barky',
    'species' : 'dog',
    'favoriteFood': 'carrots'
  }
]
```

## 메서드

### JSON.stringify()
자바스크립트의 값을 JSON 문자열로 변환

> JSON.stringify(value, replacer, space)

* value(필수): JSON 문자열로 변환할 값. (배열, 객체, 또는 숫자, 문자 등이 될 수 있다.)
* replacer(선택): 함수 또는 배열. 이 값이 null 이거나 제공되지 않으면, 객체의 모든 속성들이 JSON 문자열 결과에 포함된다
* space(선택): 가독성을 목적으로 JSON 문자열 출력에 공백을 삽입하는 데 사용되는데, string이나 number 객체가 될 수 있다.


### JSON.parse()
JSON 문자열을 자바스크립트 객체로 변환

> JSON.parse(text, reviver)

* text(필수) : JSON으로 변환할 문자열. JSON 구문은 JSON 객체의 설명을 참고하세요.
* reviver(선택) : 함수라면, 변환 결과를 반환하기 전에 이 인수에 전달해 변형함.
* 반환 값 : 주어진 JSON 문자열에 대응하는 Object.
* 예외 : 변환할 문자열이 유효한 JSON이 아닐 경우 SyntaxError.




---

## 참고링크
- [JSON.stringify( )를 재귀함수로 구현하기](https://medium.com/@cheonmyung0217/%EA%B5%AC%ED%98%84-json-stringify-%EB%A5%BC-%EC%9E%AC%EA%B7%80%ED%95%A8%EC%88%98%EB%A1%9C-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0-972f08622562){:target="_blank"}
- [](https://holjjack.tistory.com/79){:target="_blank"}
