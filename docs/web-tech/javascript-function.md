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

### .shift()
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


### .pop()
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

### push()
- 새로운 항목을 배열 뒤에 추가해 원본 배열을 변경



### .every()
- 해당 배열이 조건을 모두 만족시킬 때
- 반환값이 false이거나 false로 처리할 수 있는 값이면 처리를 멈추고 false를 반환, 반환값이 true혹은 true로 처리할 수 있는 값이면 배열에 대한 처리를 계속 진행합니다.
- every()메서드가 배열의 끝에 도달하면 true를 반환합니다.

```js
'use strict'

const arr = [2, 3, 4];
const isBiggerThenOne = arr.every( key => key > 1);
console.log(isBiggerThenOne); // true
```


### .some()
- 최소 한개이상의 요소에 대해 만족을 하면 true 반환
- 반환 값이 true이거나 true같은 값이면 some메서드는 처리를 중간하고 true를 반환한다. 반대로 false이거나 false같은 값이면 처리를 계속 진행합니다.
- 배열의 끝에 도달하면 false를 반환한다.


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


### .find()
- 해당하는 데이터 값을 찾고 실제 그 데이터를 리턴할 경우
- some()처럼 동작하지만 ture나 false를 반환하지 않고 처리 중인 배열요소의 값을 반환한다.

```js
'use strict'

const arr = ['아름다운', '대한민국' ];
const test = arr.find( key => key ==='아름다운' );
console.log(test); // 아름다운
```

### .findIndex()
- find()와 똑같지만, 배열요소의 값 대신 배열요소의 색인을 반환한다.

### .includes()
- 존재여부를 확인하라
- 실제로 해당하는 데이터는 필요하지 않고 단지 해당 데이터가 포함하고 있는지에 대한 조건만을 수행하고 싶을때
- boolean값을 반환한다.(true, false)

```js
'use strict'
//예제 1)
const arr = ['아름다운', '대한민국' ];
const test = arr.includes( '대한민국' );
console.log(test); // true

//예제 2)
const article = ['아름다운', '대한민국' ];

function displayArticle(article) {
  return article.indexOf('대한민국') > -1;
}
displayArticle(article); //true

//↓ includes를이용
function displayArticle(article) {
  return article.includes('대한민국')
}
displayArticle(article); //true
```

### .map()
- 배열 내의 모든 요소에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환
- forEach()와 비슷하지만 인자로 전달된 함수의 모든 반환 값을 모아서 새로운 배열로 반환한다.
- 원래 배열을 개선 하거나 확장하는 방식으로 변환해서 새로운 배열을 만드는데 이상적인 메서드이다.

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


### .filter()
- 주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열을 반환
- find()와 똑같지만 항상 배열의 끝까지 처리하며 반환값이 true인 배열요소의 목록을 배열로 반환한다.
- find()는 일치하는 처음 값을 반환하고 filter는 일치하는 모든 값을 반환한다.

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

### .reduce()

```js
'use strict'

let arr = [0,1,2,3,4];
const reduceFunc = arr.reduce(function(accumulator, currentValue, currentIndex, array){
  return accumulator + currentValue; 
}, 0);

console.log(reduceFunc);
// 10
```


### .forEach()

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

### .for...in 
- 객체의 모든 열거 가능한 속성에 대해 반복
- 객체의 key 값에 접근할 수 있지만, value 값에 접근하는 방법은 제공하지 않는다

```js
  let names = ['홍길동', '이대한', '박민국' ];

  for (let val in names) {
    console.log(val); // 0, 1, 2
  }
```


### .for...of 
- ES6+
- [Symbol.iterator] 속성을 가지는 컬렉션 전용 반복 구문

```js
  let names = ['홍길동', '이대한', '박민국' ];

  for (let val of names) {
    console.log(val); // 홍길동, 이대한, 박민국
  }
```

### .concat()
- 두개 이상의 배열을 연결해서 새로운 배열로 만든다.

### .reverse()
- 배열의 요소들을 반대 방향으로 뒤집는다.

### .slice()
- 배열 전체를 복사하거나 배열의 일부를 복사할 수 있다.


### 정리
- forEach()나 find()는 배열의 끝에 도달하기 전에 종료할 수 있다(forEach를 조기종료하는 방법은 forEach대산 every()나 some()을 쓰는 것)
- map(), reduce(), filter()는 배열의 끝에 도달하기 전에는 종료할 수 없다.
- reduce()는 reduceRight()처럼 배열을 반대방향으로 처리할 수 있는 방법이 있지만, forEach, map, filter, find는 그런 방법이 없다.


### Object.assign()
- 조작없이 객체를 생성
- 전통적인 객체를 통합(병합)하는 메서드
- Object객체는 글로벌 메서드로 선언하지 않고 사용가능하다.
- 객체의 속성들을 다른 객체로 복사할 수 있다. 객체를 생성하고 싶다면 빈 객체에 대입하면 된다.

```js
'use strict'

// 예1)
const obj = {
  title: '아름다운'
}
const newObj = {
  name: '대한민국'
}

// obj, newObj객체를 합치려면? 
const test = Object.assign( {}, obj, newObj );
console.log(test); // { title: '아름다운', name: '대한민국' }

// 예2) - 자바스크립트 코딩의 기술 책 중
const basic = {
  author: '',
  title: '',
  year: 2020,
  rating: null
};

const book = {
  author: 'Joe Morgan',
  title: 'Simplifying Javascript'
};
const updated = Object.assign({}, basic, book)

// 예3) - 자바스크립트 코딩의 기술 책 중
const book = {
  title: 'Reasons and Persons',
  author: 'Derek Parfit'
};
const update = { ...book, year: 1984 };

console.log(update); // {title: "Reasons and Persons", author: "Derek Parfit", year: 1984}
```

### Object spread
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

### .set()
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

### Object.value(), Object.keys(), Object.entries()

```js
'use strict'

const obj = {0: 'a', 1: 'b', 2: 'c'};
console.log(Object.keys(obj));      // ["0", "1", "2"]
console.log(Object.values(obj));    // ["a", "b", "c"]
console.log(Object.entries(obj));   // ["0", "a"], ["1", "b"], ["2", "c"]
```

### Map()

- 키-값 데이터를 갱신
- 키-값 쌍이 자주 추가되거나 삭제되는 경우 사용
- 키가 문자열이 아닌 경우 (여러가지 자료형을 키로 받을수 있다 예: 숫자)

> `.set()` 새로운 맵을 생성할 때 <br>
`.delete()` 맵에서 값을 제거할 때 <br>
`.get()` 맵에서 데이터를 가져올 때. 인수로는 키만 전달 <br>
`.clear()` 맵에서 모든 키-값 쌍을 제거할 때 <br>
{:.list}

```js
//예1 - 자바스크립트 코딩의 기술 책 중
let filters = new Map(
  [
    ['견종', '래브라도레트리버'],
    ['크기', '대형견'],
    ['색상', '갈색']
  ]
)
filters.get('색상');  //갈색
filters.delete('색상'); // true
filters.clear('색상'); // undefined

//예2 - 자바스크립트 코딩의 기술 책 중
const filters = new Map()
                .set('색상', '검정색')
                .set('견종', '래브라도레트리버');
function checkFilters (filters) {
  for (const entry of filters) {
    console.log(entry)
  }
}
console.log(checkFilters(filters));
// ["색상", "검정색"]
// ["견종", "래브라도레트리버"]
```


---

## 참고
- [Node 웹 프로그래밍 올인원 패키지 Online.]패스트캠프
- [자바스크립트는 왜 그 모양일까?] 더글리스 크락포드 지음
