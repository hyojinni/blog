---
layout: default
title: node.js
parent: Web Tech
nav_order: 8
---

#  node.js
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---
### Node.js 
{:.bigger}
 
- Node.js : Chrome V8 JavaScript 엔진으로 빌드된 JavaScript 런타임
- LTS : 장기적인 지원이 보장받는 버전
- Current : 장기적인 지원을 보장받을수는 없으나 최신기능 모두 체험해 볼수 있는 기능

##### Packages and modules : about sematic versioning
{:.bigger}

- 1.0.0
- 1.0.`1` : (Major releases) 하위버전과 호환이 가능하고 버그를 수정했을 때
- 1.`1`.0 : (Minor releases) 하위버전과 호환이 가능하고 새로운 기능이 추가 되었을때
- `2`.0.0 : (Patch releases) 하위버전과 호환이 되지 않지만 새롭고 매우 중요한 변화가 생겼을때

> Patch releases : 1.0 or 1.0.x or `~`1.0.4 <br>
Minor releases : 1 or 1.x or `^`1.0.4 <br>
Major releases * or x <br>
{:.list}



### 패키지 설치 
{:.bigger .alone}

`npm install <패키지명>`{:.property}
- Node.js에서 사용할 수 있는 모듈인 패키지를 설치
{:.mb-6}

`npm install <패키지명>`{:.property} `--save -dev`{:.special}
 - --save -dev 의 의미는 해당 패키지가 정상적으로 설치되고 package.json파일 안에 추가되어 다음번 인스톨할때 자동으로 설치 되도록 하는 옵션.
- package.json파일에 추가되느냐 안되느냐의 차이로 보면 된다.

`npm install <패키지명>`{:.property} `-g`{:.special}
- 글로벌하게 설치. 다른 node프로젝트에서도 사용할수 있도록 하는 옵션.

`npx`{:.property}
- 설치 후 바로 실행하다는 의미
- npm을 설치하면 자동으로 설치되므로 별도의 설치 필요없음
- node-modules폴더에 저앙해서 실행하는 게 목적이 아니라 해당 모듈을 일회성으로 설치해서 실행
- 임시폴더에 설정이 되고 일회성으로 실행
- save, uninstall 같은 옵션이 필요없다.
  ```js
  npm cowsay " hello"
  ```
  {:.mb-6}

`npm init`{:.property}
- **package.json**{:.text-purple-000} 파일을 작성.
- `npm init -y` 질문 없이 바로 시작하고 싶다면 **-y(--yes)**{:.text-green-000}
{:.mb-6}

`npm install express`{:.property}
- express는 자바의 Spring 프레임워크와 비슷
- 실질적인 nodejs의 표준 프레임워크
{:.mb-6}

`npm update`{:.property}
- 설치한 패키지를 업데이트
{:.mb-6}


`$ npm install -g nodemon`{:.property}
- 서버를 실행하면 코드가 바뀔때마다 자동으로 재시작
- <i class="material-icons fs-4 text-blue-000"> settings</i>vscode → File → Auto Save가 설정이 되어 있고 파일의 변화가 생기면 자동으로 이 변화를 감지해서 실행
{:.mb-6}

`npm install morgan`{:.property}
- nodeJS 에서 사용되는 로그 관리를 위한 미들웨어 (요청에 대한 정보를 콘솔에 기록)
{:.mb-6}

`npm install nunjucks`{:.property}
- 템플릿 엔진을 자동화를 사용하기 위해 사용

<i class="material-icons text-green-000">insert_drive_file</i> macro/link.html 

```js
  { % from "macro/link.html" import link % }
  { { link( '/admin/products' , "List" , req_path ) } }
  { { link( '/admin/products/write' , "Write" , req_path ) } }
```

<i class="material-icons text-green-000">insert_drive_file</i> base.html

```js
{ # 
    href : 태그안의 링크
    text : 링크안에 들어갈 텍스트
    current_url : 현재 url
# }
{ % macro link( href , text , current_url ) % }
    <li { % if href == current_url  % } class="active" { % endif % }>
        <a href="{ { href } }">{ { text } }</a>
    </li>
{ % endmacro % }
```


- { { } } : 변수 사용 <br>
  value로서 { { } }를 사용할 경우, ""안에 넣어줘야 한다는 점 <br>

  ```js
  (예)<input name="name" value="{ { name } }"/>
  ```

- if, else, endif

  ```js
  { % if isLogin % }
  (이 부분은 로그인 했을때 보여주고 싶은 tag들을 보여준다.)
  { % else % }
  (로그인 안 했을때의 보여주고 싶은 tag들을 보여준다.)
  { % endif % }
  ```

- block, endblock (include같은 개념)

  ```js
  { % block content % }{ % endblock % }
  ```

- for

  ```js
   { % for item in sequence % }     
      (반복할 내용....)
   { % endfor % }
  ```
{:.mb-6}


---


### HTTP 통신을 할 수 있는 서버를 구현 
{: .bigger}

##### <i class="material-icons text-red-000">note_add</i> http 
{: .bigger}

```js
const http = require('http')

const server = http.createServer( (req, res) => { // 서버생성
  res.statusCode = 200 // 정상적인 결과를 보낸다
  res.setHeader('Content-Type', 'text/html') // 어떠한 데이터 타입을 사용해서 해당하는 결과를 리턴하는지 명시
  res.end('<div>Hello World</div>')
})

const port = process.env.PORT // 명시적으로 port를 외부에서 받을수 있다

server.listen(port, () => { //리스너를 작성
  console.log(`Server running at port ${port}`)
})
```

##### https
{: .bigger}

- 모든 데이터 교류 과정 중에 ssl프로토콜이 추가가 되어 https를 사용하면 해당하는 모든 데이터 트랜젝션 즉 데이터 처리과정이 암호화되어 안전하게 전송되는 프로토콜
- Option이 있다.

```js
const https = require('https')
const options = {
  hostname: 'google.com', // https 안써도 된다
  port: 443, // 일반적으로 사용
  path: '/login', // hostname과 결합되는 url (= google.com/login)
  method: 'GET' // CRUD - Create(POST), Read(GET), Update(PUT), Delete
}

const req = https.request(options, res = > {
  console.log(`statusCode: ${res.statusCode}`)

  res.on('data', d => {
    process.stdout.write(d)
    //stdout : standard output
    //콘솔에서 표준 입출력을 관리하는 모듈 중 standard input, standard output이 있음
  })

  req.on('error', e => {
    console.log(error)
  })
})

req.end() // 명시적으로 종료를 해줘야 메모리 누수를 방지
```


##### http 상태코드
{: .bigger}

|상태코드|설명|
|:------|:---|
|1xx    |조건부 응답  |  
|2xx    |응답성공     |
|3xx    |리다이렉트   |
|4xx    |요청오류     |
|5xx    |서버오류     |

##### Express사용하지 않을때
{: .bigger}

<i class="material-icons text-green-000">insert_drive_file</i> server.js 

```js
var http = require('http');

http.createServer( (request, response) => {  
    response.writeHead(200, {'Content-Type' : 'text/plain'});
    response.write('Hello Server');
    response.end();
}).listen(3000);
```
terminal → 해당폴더경로 > node server.js **↵** <br>
브라우저 → localhost:3000 **↵**  <br>


##### Express로 사용하여 웹서버 띄우기
{:.bigger}

<i class="material-icons text-green-000">insert_drive_file</i> app.js 

```js
const express = require('express');

const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello express');
});

app.listen(port, () => {
  console.log('Express listening on port', port);
});
```

<i class="material-icons text-green-000">insert_drive_file</i> package.js 

```js
...
 "scripts": {
    "start" : "npx nodemon app.js"
  },
...
"dependencies": {
    "express": "^4.17.1",
    "morgan": "^1.10.0",
    "nunjucks": "^3.2.2"
}
```
terminal → 해당폴더경로 > node start **↵** <br>
브라우저 → localhost:3000 **↵**  <br>
**npx**: 패키지를 설치하지 않고, npm 패키지를 1회성으로 즉석 실행해볼 수 있는 도구


### Routing
{:.bigger}

##### Express 구조
{:.bigger}

```html
├─node_module
├─controllers
   └─admin
      ├─admin.ctrl.js
      ├─index.js      
├─routes
      ├─admin.js
├─templates
   └─admin
      ├─products.html
   └─common
      ├─404.html
      ├─500.html   
   └─layout
      ├─base.html
   └─macro
      ├─link.html
├─uploads
├─app.js
├─package.json
├─package-lock.json
├─server.js
```

##### 기본 예제
{:.bigger}

<i class="material-icons text-green-000">insert_drive_file</i> app.js 

```js
const express = require('express');
const admin = require('./routes/admin');

const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Express Start');
});

app.use('/admin', admin);

app.listen(port, () => {
  console.log('Express listening on port', port);
});
```


<i class="material-icons text-green-000">insert_drive_file</i> admin.js 

```js
const express = require('express');
const router = express.Router();

router.get('/', (req, res) => {
  res.send('admin');
});

router.get('/products', (req, res) => {
  res.send('admin products');
});

module.exports = router;
```


### Class
{:.bigger}

- 캐쉬 매니저
- 데이터 매니저

<i class="material-icons text-green-000">insert_drive_file</i> cache.js

```js
'use strict'

class cacheManager {
  constructor () {
    this.config = []
  }

  addConfig (obj = {}) {
    this.config.push(obj)
  }

  getConfig () {
    return this. config
  }

}

module.exports = cacheManager
```

<i class="material-icons text-green-000">insert_drive_file</i> session.js

```js
'use strict'

const cacheManager = require('./cache')

class sessionManager extends cacheManager{}

const SessionManager = new sessionManager()
SessionManager.addConfig({
  token: 'ran'
})

const config = SessionManager.getConfig()

console.log(config) // { token: 'ran' }
```

<i class="material-icons text-green-000">insert_drive_file</i> robot.js

- constructor (name) {} : 생성자, `name`: 초기값
- super(name) : `super`는 상위생성자(Robot)를 호출하는 기능
- Ai는 Robot 클래스를 확장한 클래스이다

```js
'use strict'

class Robot {
  constructor (name) {
    this.name = name
  } 
  speak() {
    console.log(`${this.name}`)
  }
}

const r = new Robot('hi')
r.speak() // hi

class Ai extends Robot{
  constructor(name) {
    super(name)
  }
  walk() {
    console.log(`walk: ${this.name}`)
  }
}

const a = new Ai(`hi`)
a.speak() // hi
a.walk()  // walk: hi

```
<i class="material-icons">open_in_new</i> [Node Green](https://node.green/){:target="_blank"}

##### static method
{:.bigger}

- class를 생성하지 않고  class내부에 접근하여 함수를 실행할 수 있다.
- 생성자를 통해서 클래스를 초기화하는데 클래스를 초기화하지 않고 클래스 내부에 있는 함수를 접근할수 있는 것은 constructor(생성자)에 접근하지 않고 바로 Static Method를 호출하기 때문이다.
- Static Method 내에서는 constructor(생성자)에 선언된 변수나 객체나 어떠한 자료도 접근할수가 없다. `constructor()`의미가 없다.
- 기본적으로 클래스를 생성할 때는 `const Test = new test()`와 같이 new로 생성하는 데 Static Method는  new로 할당하여 클래스를 생성하는게 아니라 다이렉트로 호출할 수 있다. `test.call()`{:.special}

```js
class test {
  constructor() {
    this.config = []
  }
  fn() {

  }
  static call() {
    // this.config = [] → 사용할수 없다.
    console.log('static method')
  }
}
// const Test = new test() (X)
test.call() // static method
```
기본구문
```js
class test {
  static call() {
    console.log('static method')
  }
}
test.call() // static method
```

### Event Emitter
- 특정이벤트가 발생했을 때 일괄적으로 특정코드를 실행할수 있도록 작성할 수 있는 방법 
- 내장모듈

```js
const EventEmitter = require('events')

class ChatManager extends EventEmitter{}
const chatManager = new ChatManager()

chatManager.on('join', () => {
  console.log("new user joined")
})

chatManager.emit('join') // new user joined
```
> `'join'` : 메서드 <br>
('join', `() => {}` : 콜백함수 <br>
`on`{:.property} : 특정 이벤트가 발생했을 때 임의의 이벤트에 선언<br>
`emit`{:.property} : 선언된 이벤트를 emit로 호출<br>
{:.list}


### DNS

```js
const dns = require('dns')

dns.lookup('test.com', (err, address, family) => {
  console.log(`address: ${address}, ${family}`)
})

dns.resolve4('archieve.com', (err, addresses) => {
  if (err) throw err

  const res = JSON.stringify(addresses)
  console.log(res)

  addresess.forEach( a => {
    dns.reverse(a, (err, hostname) => {
      if (err) throw err

      console.log(`reverse for ${a}; ${JSON.stringify(hostname)}`)
    })
  })
})

// address: 69.172.200.235, 4
// reverse for 159.8.210.35; 

```

> dns.lookup(`'test.com'`, (err, address, `family`)<br>
  - `'test.com'` : 주소
  - `family` : IP버전 ( IPv`4`{: .special})
{: .list}
> dns.resolve`4`('archieve.com', (err, `addresses`) <br>
  - `addresses` : 복수형, 객체형태로 옴 
  - resolve`4` : `4`{: .special}는 IP버전
{: .list}


### File System
node.js를 일반적으로 사용하는 이유는 웹서버를 생성하여 대량의 request를 실시간 처리

```js
const fs = require('fs')

fs.readFile('test.txt', 'utf-8', (err, data) => {
  if (err) {
    console.error(err)
    return
  }
  console.log(data)
})

const content = 'something to write'
fs.writeFile('write.txt', content, err => {
  if (err) {
    console.error(err)
    return
  }
  console.log('success')
})
```


> fs.`readFile`{:.special}(`test.txt'`, `'utf-8'`, (`err`, `data`)<br>
  - `readFile` : 파일 읽는 메소드
  - `test.txt'` : 첫번째 파라미터, 파일명 기재
  - `'utf-8'` : 인코딩 지정, 기본값(기재하지 않으면 기본으로 설정)
  - `err` : 콜백함수 파라미터 - 에러
  - `data` : 콜백함수 파라미터 - 데이터{:list}
{: .list}

> fs.`writeFile`(`'write.txt'`, content, err <br>
  - `writeFile` : 파일 읽는 메소드
  - `write.txt'` : 첫번째 파라미터, 파일명 기재
  - 인코딩은 지정하지 않는다.
{: .list}

위의 코드를 가독성 좋게 변경 
```js
 'use strict'

 const fs = require('fs')
 const { promisify } = require('util')

 const read = promisify(fs.readFile)
 const write = promisify(fs.writeFile)

 const writeAndRead =  async (data = '') => {
  try {
    await write('test.txt', data)
    return ( await read('test.txt') )
  } catch (e) {
    console.error(e)
  }
 }

 writeAndRead('something to write') 
 ```

- return ( await read('test.txt') ) 아래구문과 동일
  ```js
  const content = await read('test.txt') 
  return content
  ```
- const { promisify } : 비구조화
- 비동기 함수를 프라미스로 바꾸기 위해서 상수를 선언하는 이유는 해당함수의 결과 또한 상수이기 때문이다. 
  ```js
  const read = promisify(fs.readFile)
  // 의미 : 콜백함수를 프라미스로 변경했다
  ``` 
- `await` : 기다리고 있는 상태












---

## 참조링크
- [내 NPM 패키지(모듈) 배포하기](https://heropy.blog/2019/01/31/node-js-npm-module-publish/){:target="_blank"}
- [Nunjucks 정리](https://velog.io/@pkbird/Nunjucks-basic){:target="_blank"}
- [Node 웹 프로그래밍 올인원 패키지 Online](https://www.fastcampus.co.kr/){:target="_blank"}
- [Node 웹 프로그래밍 올인원 패키지 Online.] 패스트캠프
- [Node Green](https://node.green/){:target="_blank"}
