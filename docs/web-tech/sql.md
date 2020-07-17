---
layout: default
title: SQL
parent: Web Tech
nav_order: 6
---

#  SQL
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

##  기본문법

<div class="code-example narrow" markdown="1">
no열 값이 2가 아닌 행만 검색<br>
</div>
```sql
SELECT * FROM sample01 WHERE no <> 2;
```

<div class="code-example narrow" markdown="1">
문자열형 상수는  싱글퀴트('')로 표기
</div>
```sql
SELECT * FROM sample01 WHERE name = '이효진'
```
<div class="code-example narrow" markdown="1">
날짜시간 형일때도 싱글퀴트('')로 표기, 연월일은  **-** 으로 구분, 시분초는 **:** 로 구분표기
</div>

```sql
SELECT * FROM sample01 WHERE date = '2019-01-21 10:20:43'
```

##### Like 조건을 사용하여 데이터 찾기
<div class="code-example narrow" markdown="1">
1. `'A%'`{:.property}    'A'로 시작하는 모든 문자열 <br>
2. `'%A%'`{:.property}   'A'가 포함된 모든 문자열 <br>
3. `'_A%'`{:.property}   두 번째 문자가 'A'인 모든 문자열 <br>
4. `'[ABC]%'`{:.property}  첫 번째 문자가 'A' 또는 'B' 또는 'C'인 모든 문자열<br>
5. `'[A-D]%'`{:.property}  첫 번째 문자가 ABCD에 속하는 모든 문자열 <br>
6. `'[^A]%'`{:.property}   첫 번째 문자가 'A'가 아닌 모든 문자열 <br>
</div>
```sql
1 SELECT 컬럼명 FROM 테이블명 WHERE 컬럼명 LIKE 'A%'
2 SELECT 컬럼명 FROM 테이블명 WHERE 컬럼명 LIKE '%A%' 
3 SELECT 컬럼명 FROM 테이블명 WHERE 컬럼명 LIKE '_A%'
4 SELECT 컬럼명 FROM 테이블명 WHERE 컬럼명 LIKE '[ABC]%'
5 SELECT 컬럼명 FROM 테이블명 WHERE 컬럼명 LIKE '[A-D]%'
6 SELECT 컬럼명 FROM 테이블명 WHERE 컬럼명 LIKE '[^A]%'
```

##### ORDER BY 정렬해서 출력하기
<div class="code-example narrow" markdown="1">
1. 내릴차순으로 정렬 : 1000 → 500 → 100 → 50 → 10<br>
2. 오름차순으로 정렬 : 10 → 50 → 100 → 500  → 1000<br>
</div>
```sql
1 SELECT 열명 FROM 테이블명 ORDER BY  열명 DESC
2 SELECT 열명 FROM 테이블명 ORDER BY  열명 ASC
```
---

<div class="code-example narrow bg" markdown="1">
[store 테이블]


|name         | sales	| date        |
|:------------|------:|:-----------:|
| Los Angeles | 1500  | Jan-05-2018 |
| San Diego   | 250   | Jan-07-2018 | 
| Los Angeles | 300   | Jan-08-2018 | 
| Boston      | 700   | Jan-08-2018 | 

</div>


##### DISTINCT  중복제거하기

<div class="code-example narrow" markdown="1">
> SELECT DISTINCT 컬럼명1, 컬럼명2, ... FROM 테이블명;
{:.list}

```sql
SELECT DISTINCT name FROM store;
```

|name         |
|:------------|
| Los Angeles |
| San Diego   |
| Boston      |

</div>

##### COUNT, SUM, AVG, MIN, MAX

<div class="code-example narrow" markdown="1">
> SELECT **COUNT**{:.text-blue-300} ("필드명") FROM "테이블명";
{:.list}

```sql
SELECT COUNT(name) FROM store WHERE name IS NOT NULL;
// 4
SELECT COUNT(DISTINCT name) FROM store;
// 3
```

> SELECT **SUM**{:.text-blue-300} ("필드명") FROM "테이블명";
{:.list}

```sql
SELECT SUM(sales) FROM store;
// 2750
```

> SELECT **AVG**{:.text-blue-300} ("필드명") FROM "테이블명";
{:.list}

```sql
SELECT AVG(sales) FROM store
// 687.5000
```


> SELECT **MAX**{:.text-blue-300} ("필드명") FROM "테이블명";<br>
> SELECT **MIN**{:.text-blue-300} ("필드명") FROM "테이블명";<br>
{:.list}

```sql
SELECT MAX(sales), MIN(sales) FROM store
// MAX(sales) : 1500 , MIN(sales) : 250
```

</div>

##### GROUP BY 
<div class="code-example narrow" markdown="1">
> SELECT "필드1", SUM("필드2") FROM "테이블명" GROUP BY "필드1";
{:.list}

```sql
SELECT name, SUM(sales) FROM store GROUP BY name;
```

|name         | SUM(sales) |
|:------------|-----------:|
| Los Angeles |  1800      |
| San Diego   |   250      |
| Boston      |  700       |

</div>





### 수치연산
<div class="code-example narrow" markdown="1">
amount 별명을 사용해 내림차순으로 정렬하기
</div>
```sql
SELECT *, price*quantity AS amount FROM sample06 ORDER BY amount DESC;
```

### 함수연산

<div class="code-example narrow" markdown="1">
1. Round 함수 (반올림 함수)<br>
2. 소수점 둘째자리에서 반올림하기<br>
3.  10단위로 반올림<br>
</div>
```sql
1 SELECT amount, ROUND(amount) FROM sample07;
2 SELECT amount, ROUND(amount, 1) FROM sample07
  // 출력 : 5961.6, 2138.4, 1080.0
3 SELECT amount, ROUND(amount, -2) FROM sample07
  // 출력 : 5961.60 => 6000
```

### 문자열 연산
<div class="code-example narrow" markdown="1">
**CONCAT함수**{:.text-blue-300}  문자열결합
> SELECT CONCAT(str1, str2 ...);
{:.list}
</div>
```sql
SELECT CONCAT('안녕하세요.', '감사해요.', '다시만나요.') AS hello;
// 안녕하세요.감사해요.다시만나요.
```

<div class="code-example narrow" markdown="1">
**SUBSTRING함수**{:.text-blue-300} 문자열의 일부분을 계산해서 반환해주는 함수
</div>
```sql
SUBSTRING('20200220001', 1, 4) ;  // 2020
SUBSTRING('20200220001', 5, 2); // 02
```
<div class="code-example narrow" markdown="1">
**TRIM함수**{:.text-blue-300} 문자열의 앞뒤로 여분의 스페이스가 있을경우 제거해주는 함수)
</div>
```sql
TRIM('  ABC    '); // 'ABC'
```

<div class="code-example narrow" markdown="1">
**CHARACTER_LENGTH함수**{:.text-blue-300} 문자열의 길이를 계산해 돌려주는 함수
  - EUC-KR에서 ASCII문자는 한글은 2바이트용량을 가짐
  - UTF-8에서 ASCII문자는 한글은 3바이트 용량을 가짐
</div>

### 날짜 연산
<div class="code-example narrow" markdown="1">
> 1 SELECT **DATEDIFF**{:.text-blue-300} ('구분자','Start_Date','End_Date');<br>
2 SELECT **TIMESTAMPDIFF**{:.text-blue-300} (단위, 날짜1, 날짜2);<br>
{:.list}
</div>

```sql
SELECT DATEDIFF(dd,'2018-01-01','2018-12-31') + 1
// 365
SELECT TIMESTAMPDIFF(MONTH, '2019-07-01', '2020-07-28');
// 12
```

### CRUD
<div class="code-example narrow" markdown="1">
>**C**{:.text-red-000}reate(생성) :  **INSERT INTO**{:.text-blue-300} 테이블명 **VALUES**{:.text-blue-300}(데이터)<br>
**R**{:.text-red-000}ead(읽기) : **SELECT**{:.text-blue-300}  필요한 컬럼 **FROM**{:.text-blue-300} 테이블명 WHERE 조건<br>
**U**{:.text-red-000}pdate(갱신) : **UPDATE**{:.text-blue-300} 테이블명 **SET**{:.text-blue-300} 수정할컬럼 = 수정할값 WHERE 조건문<br>
**D**{:.text-red-000}elete(삭제) : **DELETE FROM**{:.text-blue-300} 테이블명 WHERE 조건문<br>
{:.list}
</div>

---
## 참고링크
- [Like](https://ggmouse.tistory.com/131){:target="_blank"}
- [Concatenate](https://araikuma.tistory.com/522){:target="_blank"}
- [MySQL](https://extbrain.tistory.com/category/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4/MySQL){:target="_blank"}
- [SQL](https://araikuma.tistory.com/category/SQL){:target="_blank"}