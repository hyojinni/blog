---
layout: default
title: javascript
parent: Web Tech
nav_order: 4
---

#  javascript
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

## Javscript
* 컴파일 없이 브라우저뿐만 아니라 서버에서도 실행 할 수 있으며, 자바스크립트엔진이라 불리는 특별한 프로그램이 있는 모든 디바이스에서 동작한다.
* ECMAScript라는 고유한 명세를 가진 독립적인 언어이며 자바와 아무런 연관이 없다.
* 브라우저엔 자바스크립트 가상머신 엔진이 내장되어있다.
* unicode지원 (한글, emoji, 특수문자 다 지원)
{:.block}

> **V8**: 크롬과 오페라에서 쓰임<br>
**SpiderMonkey**: 파이어폭스에서 쓰임<br>
**Trident, Chakra** : IE 버전에 따라<br>
**ChakraCore**: IE엣지<br>
**SquirrelFish**: 사파리<br>
{:.list}

* 엔진은 프로세트 각 단계마다 최적화를 진행한다.
* 모던 자바스크립트는 “안전한”프로그래밍 언어이다.(메모리나 CPU같은 저수준 영역의 조작을 허용하지 않는다.)
* Node.js환경에서는 임의의 파일을 읽거나 쓰고, 네트워크 요청을 수행하는 함수를 지원한다.
{:.block}

### 엔진 동작 기본원리
* 엔진이 스크립트를 읽는다 (파싱)
* 읽어 들인 스크립트를 기계어로 전환(컴파일)
* 기계어로 전환된 코드가 실행 (기계어로 전환되었기 때문에 실행속도가 빠름)

### 브라우저에서 자바스크립트가 할수 있는 일
* 페이지에 새로운 html을 추가 하거나 기존 html, 스타일 수정하기
* 마우스 클릭이나 포인트의 움직임, 키보드 키눌림등과 같은 사용자 행동에 반응하기
* 네트워크를 통해 원격 서버에 요청을 보내거나 파일 다운로드, 업로드하기
* 쿠키를 가져오거나 설정하기, 사용자에게 질문을 건네거나 메시지 보여주기
* 클라이언트 측에 데이터 저장하기(로컬 스토리지)

### 브라우저에서 자바스크립트가 할수 없는 일
* 웹페이지 내 스크립트는 디스크에 저장된 임의의 파일을 읽거나 쓰고, 복사하거나 실행할 때 제약을 받을수 있다.
* 운영체제가 지원하는 기능을 브라우저가 직접 쓰지 못하게 막혀있기 때문이다. 
* 모던 자바스크립트를 사용하면 파일을 다를수 있지만 접근이 제한되어있다. **&lt;input&gt;**태그를 통해 선택할때 특정상황에서만 파일접근이 허용된다.
* 카메라, 마이크같은 디바이스와 상호작용하려면 사용자의 명시적인 허가가 있어야 한다.
* 브라우저 내 탭과 창은 대게 서로의 정보를 알수 없다. 자바스크립트를 사용하여 한창에서 다른창을 열때는 예외가 적용된다. 하지만 도메인, 프로토콜,포트가 다르면 접근할수 없다.
* 자바스크립트를 이용하면 페이지를 생성한 서버와 쉽게 정보를 주고 받을수 있으나. 타 사이트나 도메인에서 데이터를 받아오는 것은 불가능하다.

### 자바스크립트만의 장점
* html/css와 완전히 통합할수 있다.
* 모든 주요브라우저에서 지원하고 기본언어로 사용된다.
* 서버나 모바일 앱등을 만드는 것도 가능하다.

### 스크립트 태그
* **&lt;script&gt;****&lt;/script&gt;**의 type 과 language 속성은 필수가 아니므로, 모던 마크업에서는 사용할 필요가 없다.
* HTML안에 직접 스크립트를 작성하는 방식은 대게 스크립트가 아주 간단할때만 사용한다. 스크립트가 길어지면 별개의 분리된 파일로 만들어 저장하는 것이 좋다.
* 스크립트를 별도의 파일을 작성하면 브라우저가 스크립트를 다운받아 캐시에 저장하기 때문에 성능상의 이점이 있다.(트레픽이 절약되고 웹페이지의 실속도가 빨라짐)
* **&lt;script&gt;**태그는 src속성과 내부 코드를 동시에 가지지 못한다.
```html
<script src="file.js">console.log(1);</script> ⇒ console.log(1); 는 무시됨.
```

### 코드 구조
* 세미콜론(;) : 생략가능하지만, 생략하지 않는 것이 더 안전하므로 지켜 사용하는 것을 권장한다.
* 주석
```html
한줄 주석 – // (두 줄 슬래시, 단축키 : Ctrl+/)
여러줄 주석 – /*….*/ (단축키 : Ctrl+Shift+/)
/*…*/안에 또 다른 /*…*/이 있을 수 없다.
```
* 엄격모드 : **use strict** 
    > 항상 “use strict”를 사용권장<br>
    반드시 최상단에 위치시킴.(엄격모드가 적용되면 취소할 방법은 없다.)<br>
    모든 모던 브라우저는 엄격모드를 지원한다.<br>
    {:.list}

### 변수
* 데이터를 저장할 때 쓰이는 이름이 있는 저장소
* let 키워드를 사용하여 변수 생성.
* 여러변수를 한줄에 선언하는 것도 가능하나, 가독성을 위해 하나의 변수는 한줄에 선언
* 변수선언방식

```javascript
let user = 'John';
let age = 25;
let message = 'Hello';

let user = 'John', 
  age = 25, 
  message = 'Hello';

let user = 'John' 
  , age = 25 
  , message = 'Hello';
```

* `var`{:.property}: **let**과 동일하지만 오랜된 방식이다.
* 변수의 값이 변경되면 이전 값은 제거되고 변경된 값을 출력한다.
* 변수명명규칙
    > 변수명에는 오직 문자, 숫자, 기호 $와 _만 들어갈 수 있다. (하이픈(-)은 변수명에 쓸 수 없다)<br>
    첫글자가 숫자가 될수 없다.<br>
    여러단어를 조합하여 변수명을 만들때는 카멜표기법으로 사용한다.<br>
    대소문자를 구별한다.<br>
    영어로 사용하는 것을 권장한다.<br>
    예약어는 변수명으로 사용할 수 없다.<br>
    {:.list}

### 상수
* 변화하지 않는 변수를 선언 할 땐,  let 대신 const를 사용하며 이를 상수라 한다.
* 상수는 재할당할수 없으므로 변경하면 에러를 발생한다.
* 대문자 상수명은 하드코딩한 값의 별칭을 만들때 사용한다. (ex: const COLOR_RED = “#F00”;)
* 최대한 서술적이고 간결한 명명으로 한다.
* 변수를 재사용하는 것보다 변수를 추가하는 것이 좋은 습관이다. 변수를 추가한다고 해서 성능 이슈가 생기지는 않는다.

### 데이터 타입
{:.bigger}

##### 자료형
{:.bigger}

* 자바스크립트의 변수는 어떤 데이터든지 담을수 있다.
* 변수값을 문자열에서 숫자로 바꿔어도 에러가 발생되지 않는다.
```javascript
let message = "hello";
message = 123456;
```

##### 숫자형
{:.bigger}

* 정수, 부동소수점 숫자를 나타냄
* 숫자형과 관련된 연산은 곱셈 *, 나눗셈 /, 덧셈 +, 뺄셈 – 등
* Infinity(어떤 숫자보다 큰 특수 값, 무한대∞), -Infinity, NaN같은 ‘특수 숫자 값(special numeric value)’이 포함
```javascript
alert( 1 / 0 ); // 어느 숫자든 0으로 나누면 무한대를 얻을 수 있다.
alert( Infinity ); //Infinity를 직접 참조할 수도 있다.
alert( "숫자가 아님" / 2 ); // NaN은 계산 중에 에러가 발생했다는 것을 나타내주는 값, 문자열을 숫자로 나누면 오류가 발생
alert( "숫자가 아님" / 2 + 5 ); // NaN에 어떤 추가 연산을 해도 결국 NaN이 반환
```

* Biglnt
  > 채택된지 얼마 안된 자료형<br>
  길이에 상관없이 정수를 나타낼수 있다.<br>
  자바스크립트에선 253 (16자리 숫자로 이루어진 정수) 큰 값 혹은 -253 보다 작은 정수는 숫자형을 사용해 나타낼 수 없으므로 아주 큰  숫자가 필요하거나 높은 정밀도로 작업을 해야 할 때는 큰 숫자가 필요할 경우 사용된다.<br>
  BigInt는 정수 리터럴 끝에 n을 붙이면 만들수 있다.<br>
  {:.list}

    ```javascript
    const bigInt = 1234567890123456789012345678901234567890n;
    const sameBigInt = BigInt("1234567890123456789012345678901234567890");
    const bigintFromNumber = BigInt(10); // 10n과 동일
    ```

  > 호환성 이슈가 있다. (firefox, chrome에서만 지원가능)<br>
  BigInt는 일반 숫자와 큰 차이없이 사용된다.<br>
  {:.list}

    ```javascript
    alert(1n + 2n); // 3
    alert(5n / 2n); // 2
    alert(1n + 2); // BigInt형 값과 일반숫자를 섞어서 사용할 수 없다.

    //일반 숫자와 섞어서 써야 하는 상황이라면 BigInt()나 Number()를 사용해 명시적으로 형 변환을 해주면 된다.
    //*bigint가 너무 커서 숫자형에서 허용하는 자릿수를 넘으면 나머지 비트는 자동으로 잘려나간다.

    let bigint = 1n;
    let number = 2;
    console.log(bigint + BigInt(number); //3
    console.log(Number(bigint) + number); // 3

    // 단항덧셈연산자는 bigint사용할수 없다.
    let bigint = 1n;
    console.log(+bigint); // error
    ```

  > 비교연산자 <, >는 bigint와 일반숫자 모두 사용할수 있다.
  {:.list}

    ```javascript
    console.log(2n > 1n); //true
    console.log(2n > 1); //true
    console.log(1 == 1n); // true
    console.log(1 === 1n); // false 
    ```

* 논리연산
    > if안이나 다른 논리 연산자와 함께 사용할 때 일반숫자와 동일하게 행동한다.<br>
    if안에서 0n은 falsy이고 다른값들은 truthy로 평가된다.<br>
    ㅣㅣ, &&도 bigint를 적용할 때도 일반숫자와 유사하게 동작한다.<br>
    {:.list}

    ```javascript
    if (0n) {
      // 절대 실행되지 않습니다.
    }
    console.log(1n || 2); 1 (1n은 truthy로 판단)
    console.log(0n || 2); 2 (0n은 falsy로 판단)
    ```

* 폴리필
    > 아직까지 제대로 된 bigint 폴리필이 나오지 않은 상황<br>
    JSBI를 사용하여 숫자를 만든 다음 바벨 플러그인에 있는 폴리필을 사용해JSBI 호출을 네이티브 bigint로 변환하면 원하는 브라우저에서 연산을 수행할 수 있다.<br>
    {:.list}

##### 문자형
{:.bigger}

  * 문자열을 따옴표로 묶는다.
  * 큰따옴표(” “), 작은따옴표(‘ ‘) – 차이 없다.
  * 역 따옴표(`: 백틱) : 변수나 표현식을 감싼후 ${..}안에 넣어주면, 원하는 변수나 표현식을 문자열 중간에 넣을수 있다.
    ```javascript
    let name = "john";
    console.log(`Hello, ${name}!`); //Hello, John!
    console.log(`the result is ${1+2}`); //the result is 3 → 1+2와 같은 수학관련표현식도 넣을수 있다.
    ```
  * 자바스크립트에서는 문자형만 있을 뿐 글자형은 지원하지 않는다. C언어와 Java는 글자형을 따로 지원(char)한다.

<i class="material-icons text-red-000">note_add</i> Sting : 단순한 문자에 대한 메서드와 객체들에 여러가지 기능을 포함하고 있다.

  - `startsWith()`{:.property} 해당문자로 시작되는지
  - `includes()`{:.property}  해당문자를 포함하고 있는지
  - `endsWith()`{:.property}  해당문자로 끝나는지


  ```js
  let string = 'Javascript : 웹페이지에 생동감을 불어넣기 위해 만들어진 프로그래밍 언어';

  //startsWith() 해당문자로 시작되는지
  let isStartsWith = string.startsWith('J');
  //includes() 해당문자를 포함하고 있는지
  let isIncludes = string.includes('생동감');
  //endsWith() 해당문자로 끝나는지
  let isEndWith = string.endsWith('어');

  // 3가지 함수가 모두 참일 경우
  const checkIfContains = () => {
    if ( isStartsWith && isIncludes && isEndWith ) {
      return true
    }
  };

  //isStartsWith와 isIncludes 둘 중 하나가 참이고 inEndWith도 참일경우
  // && || 우선순위가 없으므로, 우선순위를 정해준다.()

  const checkIfContains = () => {
    if ( (isStartsWith || isIncludes ) && isEndWith ) {
      return true
    }
  };


  const test = checkIfContains();
  console.log(test);
  ```


##### 불린형
{:.bigger}

  * true, false 두가지 값 밖에는 없는 자료형으로 긍정(true), 부정(false)을 나타내는 값을 저장할 때 사용한다.

##### NULL값
{:.bigger}

  * null값은 오로지 null값만 포함하는 별도의 자료형을 만든다.
  * 자바스크립트의 null은 자바스크립트이외의 언어의 null과 성격이 다르다.
  * 다른언어에서의 null은 존재하지 않는 객체에 대한 참조나 널포인트를 나타낼때 사용한다.
  * 자바스크립트에서는 null은 존재하지 않는 값(nothing), 비어있는 값(empty), 알수 없는 값(unknown)을 나타내는 데 사용
    ```javascript
    let age = null;
    ```

##### UNDEFINED값
{:.bigger}

  * undefined값도 null값처럼 자신만의 자료형을 형성한다.
  * undefined는 값이 할당되지 않는 상태를 나타낼 때 사용한다.
  * 변수는 선언했지만, 값을 할당되지 않았다면 해당변수는 undefined가 자동으로 할당된다.
    ```javascript
    let x;
    alert(x); // "undefined"

    let y = 123;
    y = undefined; // 변수에 undefined를 직접 할당하는 것도 가능, 권장하지 않는다.
    alert(y); // "undefined"
    ```

  * 변수가 비어있거나, 알수 없는 상태라는 것을 나타내려면 null을 사용
  * 변수에 값이 할당되었는지 여부를 확인할 때는 undefined를 사용

##### 객체와 심볼
{:.bigger}

  * 객체(object)는 특수한 자료형이다.
  * 심볼(symbol)형은 객체의 고유한 식별자(unique identifier)를 만들 때 사용

##### TYPEOF 연산자
{:.bigger}

  * 인수의 자료형이다.
  * 연산자 : typeof x
  * 함수: typeof(x)
    ```javascript
    typeof undefined; //"undefined"
    typeof 0; // "number"
    typeof 10n; // "bigint"
    typeof true; // "boolean"
    typeof "foo"; // "string"
    typeof Symbol("id"); // "symbol"
    typeof Math; // "object" , 수학연산을 하는 내장객체이므로 object
    typeof null; // "object", 언어상 오류, null은 객체가 아니다.
    typeof alert; // "function", 함수는 객체형에 속함
    ```

  
  > **함수형 언어**<br>
  functional 프로그래밍 언어는 변수값 변경을 금지한다. <br>
  스칼라(Scala)와 얼랭(Erlang)이 대표적인 함수형 언어이다.<br>
  함수에 저장된 값은 영원히 유지된다.<br>
  다른 값을 저장할려면 새로운 함수를 만들어야(새변수를 선언)한다. 이전 변수는 재사용할수 없다.<br>
  중대한 개발에 상당히 적합한 언어이다.<br>
  {:.list}

### 콜백함수(CALLBACK 함수)

  * callback : 되돌아 호출해달라는 명령
  * 어떤 함수 X를 호출하면서 특정 조건일 때 함수 Y를 실행해서 나에게 알려달라는 요청을 보내고, 이 요청을 받은 함수 X의 입장에서는 해당 조건이 갖쳐졌는지 여부를 스스로 판단하고 Y를 직접 호출한다.
    ```javascript
    var count = 0;
    var callbackFunc = function() {
    console.log(count);
    if (++count > 4) clearInterval(timer);
    };
    var timer = setInterval(callbackFunc, 300);
    // 0 (0.3 sec)
    // 1 (0.6 sec)
    // 2 (0.9 sec)
    // 3 (1.2 sec)
    // 4 (1.5 sec)

    var addCoffee = function(name) {
      return new Promise(function(resolve) {
        setTimeout(function() {
          resolve(name);
        }, 500);
      });
    };
    var coffeeMaker = async function() {
      var coffeeList = '';
      var _addCoffee = async function(name) {
        coffeeList += (coffeeList ? ',' : '') + (await addCoffee(name));
      };
      await _addCoffee('에스프레소');
      console.log(coffeeList);
      await _addCoffee('아메리카노');
      console.log(coffeeList);
      await _addCoffee('카페모카');
      console.log(coffeeList);
      await _addCoffee('카페라떼');
      console.log(coffeeList);
    };

    coffeeMaker();
    ```

  * 어떤 함수의 인자에 객체의 메서드를 전달 하더라도 이는 결국 메서드가 아닌 함수 일 뿐이다.
  * 객체의 메서드를 콜백함수로 전달하면 해당 객체를 this로 바라볼수 없게 된다
  * 전통적으로는 this를 다른 변수에 담아 콜백함수로 활용할 함수에서는 this대신 그 변수를 사용하게 하고, 이는 클로저를 만드는 방식이 많이 쓰였다.
  * Promise, Generator, async/await 등 콜백지옥에서 나오는 방법이 있다.

### 클로저(Closure)
  * 어떤 함수에서 선언한 변수를 참조하는 내부함수에서만 발생하는 현상
  * 어떤 함수A에서 선언한 변수 a를 내부함수  B를 외부로 전달할 경우 A의 실행 컨텍스트가 종료된 이후에도 변수 a가 사라지지 않는 현상(여기서 외부로의 전달은 return이 아니라는 점이다.)
  * 객체지향과 함수형 모두를 아우르는 매우 중요한 개념
    ```javascript
    var outer = function() {
    var a = 1;
    var inner = function() {
      console.log(++a);
    } 
    inner();
    }

    outer();
    ```

---

##  functions

> 큐(Queue)자료구조 : FIFO(First In First Out) : 처음에 입력된 데이터가 먼저 나온다.<br>
스택(Stack)자료구조 : LIFO(Last In First Out) :  마지막에 입력된 데이터가 먼저 나온다.<br>

#### .shift()
첫번째 요소를 제거하고 그 요소를 반환한다.

```js
// queue 구현방법 예

const queue = [];
queue.push(1);
queue.push(2);
console.log(queue); // [1, 2]
const q = queue.shift();
console.log(q); //1
```


#### .pop()
마지막요소를 배열로부터 제거하고 그 요소를 반환한다.

```js
// stack 구현방법 예

const stack = [];
stack.push(1);
stack.push(2);
console.log(stack); // [1, 2]
const s = stack.shift();
console.log(s); //2
```



#### .every()
해당 배열이 조건을 모두 만족시킬 때

```js
const arr = [2, 3, 4];
const isBiggerThenOne = arr.every( key => key > 1);
console.log(isBiggerThenOne); // true
```


#### .some()
최소 한개이상의 요소에 대해 만족을 하면 true 반환

```javascript 
//(예1)
const arr = [1, 2, 0, -1, -2];
const test = arr.some( key => key < 0 );
//0보다 작은 정수를 한개라도 포함하고 있으면 true

console.log(test); // true


//(예2)
const isBiggerThan10 = function (element, index, array) {
  return element > 10;
}

let someArr1 = [2,5,8,1,4];
let someArr2 = [12,5,8,1,4];

console.log(someArr1.some(isBiggerThan10)); // false
console.log(someArr2.some(isBiggerThan10)); // true
```


#### .find()
해당하는 데이터 값을 찾고 실제 그 데이터를 리턴할 경우

```js
const arr = ['아름다운', '대한민국' ];
const test = arr.find( key => key ==='아름다운' );
console.log(test); // 아름다운
```

#### .includes()
실제로 해당하는 데이터는 필요하지 않고 단지 해당데이터가 포함하고 있는지에 대한 조건만을 수행하고 싶을때

```js
const arr = ['아름다운', '대한민국' ];
const test = arr.includes( '대한민국' );
console.log(test); // true
```


#### .map()
배열 내의 모든 요소에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환

```javascript
//(예1)
const arr = [1, 2, 3];
const m = arr.map( x => x + 1);
//의미 : 배열이 각각의 요소에 대하여 1을 더한 결과를 모아 새로운 배열을 반환

console.log(m); // [2, 3, 4]


//(예2)
const numbers = [1,4,9];
const roots = numbers.map(Math.sqrt);

console.log(roots);
// (3) [1, 2, 3]
console.log(numbers);
// (3) [1, 4, 9]
```


#### .filter()
주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열을 반환

```javascript 
//(예1)
const arr = [1, 2, 3];
const f = arr.filter(x => x > 1);
//의미 : 배열의 가각의 요소에 대하여 함수의 1보다 큰 테스트 조건을 통과한 모든 요소를 모아 새로운 배열로 반환한다

console.log(f); // [2, 3]


//(예2)
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present', 'happy'];
let longWords = words.filter(word => word.length > 6);

console.log('longWords', longWords); 
// longWords (3) ["exuberant", "destruction", "present"]

console.log('words', words);
//(7) ["spray", "limit", "elite", "exuberant", "destruction", "present", "happy"]
```

#### .reduce()

```javascript 
let arr = [0,1,2,3,4];
const reduceFunc = arr.reduce(function(accumulator, currentValue, currentIndex, array){
  return accumulator + currentValue; 
}, 0);

console.log(reduceFunc);
// 10
```

#### .forEach()

```javascript 
const items = ['item1', 'item2', 'item3'];
const copy = [];

items.forEach(function (item) {
  copy.push(item);
});

console.log(copy);
// (3) ["item1", "item2", "item3"]
```


#### Object.assign()
- 전통적인 객체를 통합(병합)하는 메서드
- Object객체는 글로벌 메서드로 선언하지 않고 사용가능하다.

```js
const obj = {
  title: '아름다운'
}

const newObj = {
  name: '대한민국'
}

// obj, newObj객체를 합치려면? 

const test = Object.assign( {}, obj, newObj );
console.log(test); // { title: '아름다운', name: '대한민국' }
```

#### Object spread
- Object.assign사용하지 않고 spread를 사용하는 이유는  가독성 측면에서 쉽게 코드를 이해할 수 있기 때문이다.
- 직관적으로 하나의 데이터로 통합
- 객체뿐만 아니라 배열에서도 사용할 수 있다.


```js
//(예1 : 객체의 경우)
const obj = {
  title: '아름다운'
}

const newObj = {
  name: '대한민국'
}

// obj, newObj객체를 합치려면? 
const test = {
  ...obj,
  ...newObj
}
console.log(test); // { title: '아름다운', name: '대한민국' }


//(예2 : 배열의 경우)
const arr = [1, 2, 3];
const newArr = [4, 5, 6];

const test = [
  ...arr,
  ...newArr
];

console.log(test); // [ 1, 2, 3, 4, 5, 6 ]
```

#### set()
- 중복되지 않는 자료구조
- 방대한 데이터 속에 중복되지 않고 한개의 데이터만 수집하고 싶을 때 set이라는 자바스크립트에 내장된 자료구조를 사용하면 쉽게 구현할수 있다

> `.add()`{:.property} 데이터 입력 <br>
`.has()`{:.property} 데이터의 존재여부확인 <br>
`.for ~ of`{:.property} set을 순회하는 방법으로 각각의 요소를 얻어오는 방법
{:.list}

```js
const test = new Set();
// set의 자료구조로 test자료구조가 생성

test.add(1);
test.add(1);
test.add(2);
test.add(2);
test.add(3);

for ( const item of test) {
  console.log(item);
}
// 1, 2, 3

// test에 2가 존재하는가?

const hasTwo = test.has(2);
console.log(hasTwo); // true
```

#### Object.value(), Object.keys(), Object.entries()

```javascript 
const obj = {0: 'a', 1: 'b', 2: 'c'};
console.log(Object.keys(obj));      // ["0", "1", "2"]
console.log(Object.values(obj));    // ["a", "b", "c"]
console.log(Object.entries(obj));   // ["0", "a"], ["1", "b"], ["2", "c"]
```

#### template String
한 문장내에서 변수, 상수, 기존의 데이터를 통합해서 표현할 수 있다.

```js
  const covid = 'covid';
  const num = 19;
  const text = '모두모두';

  const article = `Out!! ${covid}-${num}, ${text} 힘냅시다.`
  
  console.log(article);// Out!! covid-19, 모두모두 힘냅시다.
```


---