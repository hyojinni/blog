---
layout: default
title: Tables
parent: Web Publishing
nav_order: 4
---

# Tables
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

# 타이틀

## 기본문법
## 반응형 테이블
### 방법
{:.bigger}
#### 속성
##### 일정비율로 축소하는 방법
{:.bigger}

```html

```
```css

```

* `caption`{:.property} table 요소에 제목이나 설명을 마크업할 때 사용하는 요소
* `col`{:.property} 테이블의 열 그룹
* `head`{:.property}, `tbody`{:.property}, `tfoot`{:.property} 요소는 테이블의 행 그룹
* `span`{:.property} 한번에 속성 지정할 열 개수.(기본값: 1) 
{:.block}


##### 테이터를 펼쳐서 보여주는 방법
{:.bigger}


<details markdown="1">
<summary>html</summary>
내용
</details>

요소에 **회전, 크기 조절, 기울이기, 이동 효과**{:.thin .text-blue-100}를 부여

---

{: .material-icons .face} 

<i class="material-icons">insert_drive_file</i>


## 참고링크
- [colgroup](https://developer.mozilla.org/ko/docs/Web/HTML/Element/colgroup){:target="_blank"}



<i class="material-icons">insert_drive_file</i> macro/link.html 

```js
  {% from "macro/link.html" import link %}
  {{ link( '/admin/products' , "List" , req_path ) }}
  {{ link( '/admin/products/write' , "Write" , req_path )  }}
```

<i class="material-icons">insert_drive_file</i> base.html

```js
{# 
    href : 태그안의 링크
    text : 링크안에 들어갈 텍스트
    current_url : 현재 url
#}
{% macro link(  href , text , current_url ) %}
    <li {% if href == current_url  %} class="active" {% endif %}>
        <a href="{{ href }}">{{ text }}</a>
    </li>
{% endmacro %}
```

- {{}} : 변수 사용 <br>
  value로서 {{}}를 사용할 경우, ""안에 넣어줘야 한다는 점 <br>

  ```js
  (예)<input name="name" value="{{name}}"/>
  ```

- if, else, endif

  ```js
  {% if isLogin %}
  (이 부분은 로그인 했을때 보여주고 싶은 tag들을 보여준다.)
  {% else %}
  (로그인 안 했을때의 보여주고 싶은 tag들을 보여준다.)
  {% endif %}
  ```

- block, endblock (include같은 개념)

  ```js
  {% block content %}{% endblock %}
  ```

- for

  ```js
   {% for item in sequence %}     
      (반복할 내용....)
   {% endfor %}
  ```

{:.mb-6}

