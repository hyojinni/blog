---
layout: default
title: javascript functions
parent: Web Tech
nav_order: 5
---

#  javascript functions
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---


##  functions

> 큐(Queue)자료구조 : FIFO(First In First Out) : 처음에 입력된 데이터가 먼저 나온다.<br>
스택(Stack)자료구조 : LIFO(Last In First Out) :  마지막에 입력된 데이터가 먼저 나온다.<br>

#### .shift()
첫번째 요소를 제거하고 그 요소를 반환한다.

```js
'use strict'

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
'use strict'

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
'use strict'

const arr = [2, 3, 4];
const isBiggerThenOne = arr.every( key => key > 1);
console.log(isBiggerThenOne); // true
```


#### .some()
최소 한개이상의 요소에 대해 만족을 하면 true 반환

```js
'use strict'

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
'use strict'

const arr = ['아름다운', '대한민국' ];
const test = arr.find( key => key ==='아름다운' );
console.log(test); // 아름다운
```

#### .includes()
실제로 해당하는 데이터는 필요하지 않고 단지 해당데이터가 포함하고 있는지에 대한 조건만을 수행하고 싶을때

```js
'use strict'

const arr = ['아름다운', '대한민국' ];
const test = arr.includes( '대한민국' );
console.log(test); // true
```


#### .map()
배열 내의 모든 요소에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환

```js
'use strict'

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

```js
'use strict'

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

```js
'use strict'

let arr = [0,1,2,3,4];
const reduceFunc = arr.reduce(function(accumulator, currentValue, currentIndex, array){
  return accumulator + currentValue; 
}, 0);

console.log(reduceFunc);
// 10
```

#### .forEach()

```js
'use strict'

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
'use strict'

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
'use strict'

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
'use strict'

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

```js
'use strict'

const obj = {0: 'a', 1: 'b', 2: 'c'};
console.log(Object.keys(obj));      // ["0", "1", "2"]
console.log(Object.values(obj));    // ["a", "b", "c"]
console.log(Object.entries(obj));   // ["0", "a"], ["1", "b"], ["2", "c"]
```
---

### template String
한 문장내에서 변수, 상수, 기존의 데이터를 통합해서 표현할 수 있다.

```js
'use strict'

  const covid = 'covid';
  const num = 19;
  const text = '모두모두';

  const article = `Out!! ${covid}-${num}, ${text} 힘냅시다.`
  
  console.log(article);// Out!! covid-19, 모두모두 힘냅시다.
```

---





---

## 참고
- [Node 웹 프로그래밍 올인원 패키지 Online.]패스트캠프

