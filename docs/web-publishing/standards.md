---
layout: default
title: 웹표준 & 웹접근성
parent: Web Publishing
nav_order: 91
---

# 웹표준 & 웹접근성
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 웹표준

> 구조표현동작분리권고 <br>
W3C권고안 준수(html css)<br>
  - 웹표준화 → **HTML(구조)**{:.text-blue-100}, **CSS(표현)**{:.text-red-100}, **JS(동작)**{:.text-green-100}와 분리
{:.list}



### 웹호환성
> 운영체제, 웹브라우저 버전,종류와 상관없이 접근 크로스브라우징
{:.list}

### 웹접근성
> 인식,운용,이해의 용이성/ 인적,환경적 제약없이 웹정보접근
{:.list}

## 검색엔진최적화
- 보안프로토콜(https)
- robot.txt/ sitemap.xml : 로봇배제표준파일,사이트맵
- 타이틀& 메타디스크립션 태그 320자/160자
- 소셜검색엔진최적화 메타태그 -타켓 고객이 많이 사용하는 소셜 미디어 채널 공유
- 이미지 태그 및 최적화
- 모바일 최적화 -반응형 웹사이트를 만드는 것이 가장 좋은 검색엔진 최적화방법
- 대표주소설정
- 키워드 및 콘텐츠 최적화

## Meta Tag
HTML 문서에 대한 메타 데이터를 정의

* Meta Description
  > 메타 설명 태그는 웹사이트나 페이지가 무엇에 관한 내용인지 검색엔진에 알려주는 역할<br>
  짧은 문장을 사용하여 페이지의 50 자 (300 자) 요약을 작성<br>
  {:.list}

* 웹문서최적화 메타키워드(Meta keyword)
  >메타태그의 핵심 입니다.<br>
  메타 키워드는 사용자가 검색엔진에서 키워드 검색시 메타키워드와 매칭이 되는 것이 있으면 검색결과에 노출을 해달라는 것과 동일합니다.<br>
  너무 많은 키워드를 등록할 경우 검색 로봇이 뒷 부분의 키워드들을 무시할 경우가 있으므로. 10개이하로 키워드 설정을 하는 것이 좋습니다.<br>
  키워드를 설정하였다면, 페이지안에 키워드가 여러번 노출이 되어야 효과를 볼 수 있습니다.<br>
  {:.list}

* 캐시 완료(파기)시간 정의
  ```html
  <META HTTP-EQUIV="Expire" CONTENT="-1">
  ```

* 최종 수정 일을 정의
  ```html
  <META HTTP-EQUIV="Last-Modified" CONTENT="Mon,20 Jul 2007 19:30:30">
  ```

* 캐시가 되지 않게 하는 태그
  ```html
  <META HTTP-EQUIV='Cache-Control' CONTENT='no-cache'>
  <META HTTP-EQUIV='Pragma' CONTENT='no-cache'>
  <META HTTP-EQUIV="Refresh" CONTENT="No-Cache">
  ```

* 웹 문서의 언어 설정
  ```html
  <META HTTP-EQUIV="Content-type" content="text/html; charset=euc-kr">
  ```

* 그림 위에 마우스 오버 시 이미지 관련 툴 바가 생기지 않음
  ```html
  <META HTTP-EQUIV="Imagetoolbar" content="no">
  ```
* 페이지이동
  ```html
  <META HTTP-EQUIV="Refresh" content="15;URL=http://websitename.com/">
  ```

* 페이지 로딩 시 트랜지션 효과(장면 전환 효과)
  ```html
  <META HTTP-EQUIV="Page-Enter" content="RevealTrans(Duration=5/시간 초 단위, Transition=21)">
  ```

* 캐시 완료(파기)시간 정의
  ```html
  <META HTTP-EQUIV="Expire" CONTENT="-1">
  ```

* 최종 수정 일을 정의
  ```html
  <META HTTP-EQUIV="Last-Modified" CONTENT="Mon,20 Jul 2020 19:30:30">
  ```

* 이 문서도 긁어가고 링크된 문서도 긁어감
  ```html
  <META name="robots" content="index,follow" />
  ```

* 이 문서는 긁어가지 말고 링크된 문서만 긁어감
  ```html
  <META name="robots" content="noindex,follow" />
  ```

* 이 문서는 긁어가되, 링크는 무시함
  ```html
  <META name="robots" content="index,nofollow" />
  ```

* 이 문서도 긁지 않고, 링크도 무시함
  ```html
  <META name="robots" content="noindex,nofollow" />
  ```

* 문자 형식 지정 – HTML은 ISO코드, 완성형 코드 등의 다양한 문자 셋을 지정합니다. 일반적으로 ISO 코드를 많이 사용합니다.
  ```html
  <META http-equiv="Content-Type" content="text/html; charset=ISO-8859-5">
  ```

* 스크립트 형식 지정 – 스크립트 형식에는 text/javascript-x-x(자바스크립트) 와 VBScript-x-x(비쥬얼 베이직 스크립트)가 있습니다.
  ```html
  <META http-equiv="Content-Script-x-x-Type" content="text/javascript-x-x">
  ```

* 스타일시트 형식 지정
  ```html
  <META http-equiv="Content-Style-Type" content="text/css">
  ```

* Open Graphic / 페이스북
  ```html
  <meta property="og:title"           content="제목"/>
  <meta property="og:site_name"  content="사이트명"/>
  <meta property="og:type" content="분류 (website,article,place,product,event ...)"/>
  <meta property="og:url"             content="주소"/>
  <meta property="og:image"           content="썸네일 (200x200.jpg)"/>
  <meta property="og:description"     content="요약글"/>
  ```

* 트위터
  ```html
  <meta name="twitter:card"           content="분류 (summary, photo, gallery ...)">
  <meta name="twitter:title"          content="제목">
  <meta name="twitter:site"           content="사이트명">
  <meta name="twitter:creator"        content="작성자명">
  <meta name="twitter:image"          content="썸네일">
  <meta name="twitter:description"    content="포스트 내용">
  ```
---


