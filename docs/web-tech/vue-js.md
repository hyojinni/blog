---
layout: default
title: Vue.js
parent: Web Tech
nav_order: 7
---

#  Vue.js
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---
## vuex

State : 컴포넌트 간에 공유할 데이터

Getters : state값을 접근하는 속성이자 computed() 처럼 미리 연산된 값을 접근하는 속성

Mutations : Vuex 의 데이터, 즉 state 값을 변경하는 로직들을 의미

* 인자를 받아 Vuex 에 넘겨줄 수 있음
* computed 가 아닌 methods 에 등록
* 동기적 로직을 정의

Actions:
Mutations 에는 순차적인 로직들만 선언하고 Actions 에는 비 순차적 또는 비동기 처리 로직들을 선언
setTimeout() 이나 서버와의 http 통신 처리 같이 결과를 받아올 타이밍이 예측되지 않은 로직은 Actions 에 선언
actions 를 호출할 때는 아래와 같이 dispatch() 를 이용 

[Increment Counter](https://hyojinni.github.io/blog/sample/vuex.html){:target="_blank"}