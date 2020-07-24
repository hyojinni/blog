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


---

## 참조링크
- [내 NPM 패키지(모듈) 배포하기](https://heropy.blog/2019/01/31/node-js-npm-module-publish/){:target="_blank"}
- [Nunjucks 정리](https://velog.io/@pkbird/Nunjucks-basic){:target="_blank"}
- [Node 웹 프로그래밍 올인원 패키지 Online](https://www.fastcampus.co.kr/){:target="_blank"}