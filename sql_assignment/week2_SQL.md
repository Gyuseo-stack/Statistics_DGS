# SQL_BASIC 2주차 정규 과제 

📌SQL_BASIC 정규과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고 간단한 문제를 풀면서 학습하는 것입니다. 이번주는 아래의 **SQL_Basic_2nd_TIL**에 나열된 분량을 수강하고 `학습 목표`에 맞게 공부하시면 됩니다.

**2주차 과제**는 1주차 과제처럼 SQL의 필요성이나 느낀점 위주가 아닌, **실제 강의 내용을 바탕으로 개념을 정리하고 학습한 내용을 집중적으로 기록**해주세요. 완성된 과제는 Github에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요. 

**👀(수행 인증샷은 필수입니다.)** 

## SQL_BASIC_2nd

### 섹션 3. 데이터 탐색 - 조건, 추출, 요약

### 2-3. 데이터 탐색 (SELECT, FROM, WHERE)

### 2-4. SELECT 연습문제

### 2-5. 집계 (Group By + Having + Sum/Count)



## 🏁 강의 수강 (Study Schedule)

| 주차  | 공부 범위              | 완료 여부 |
| ----- | ---------------------- | --------- |
| 1주차 | 섹션 **1-1** ~ **2-2** | ✅         |
| 2주차 | 섹션 **2-3** ~ **2-5** | ✅         |
| 3주차 | 섹션 **2-6** ~ **3-3** | 🍽️         |
| 4주차 | 섹션 **3-4** ~ **4-4** | 🍽️         |
| 5주차 | 섹션 **4-4** ~ **4-9** | 🍽️         |
| 6주차 | 섹션 **5-1** ~ **5-7** | 🍽️         |
| 7주차 | 섹션 **6-1** ~ **6-6** | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념정리 

## 2-3. 데이터 탐색 (SELECT, FROM, WHERE)

~~~
✅ 학습 목표 :
* SQL 쿼리 구조를 이해할 수 있다. 
* SELECT, FROM, WHERE의 핵심 문법을 설명할 수 있다. 
~~~
### SQL 쿼리 구조
SQL은 보통 **SELECT – FROM – WHERE** 순서로 작성 
하지만 **실행 순서**는 `FROM → WHERE → SELECT`

EX)
SELECT 컬럼1, 컬럼2, ...

FROM   테이블명

WHERE  조건식;

### FROM

**데이터를 가져올 테이블을 지정**

FROM 프로젝트ID.데이터셋.테이블

프로젝트 ID 명시 기준:

여러 프로젝트를 사용할 때만 프로젝트ID를 명시하면 됨.

별칭 지정:

테이블명이 길면 AS를 사용해 별칭을 지정할 수 있음.

### WHERE

**FROM에서 지정한 테이블의 데이터 중 조건을 만족하는 행만 필터링**

### SELECT

테이블에서 출력할 컬럼을 선택

주요 사용법:

* '*'  : 모든 컬럼을 출력
* '*' EXCEPT(컬럼명) : 특정 컬럼을 제외하고 전체 출력
*  AS : 컬럼에 별칭 지정 (큰따옴표 "" 필요 없음)


## 2-5. 집계 (Group By / HAVING / SUM,COUNT)

~~~
✅ 학습 목표 :
* 데이터를 집계하고 그룹화하는 방법을 설명할 수 있다.
* GROUP BY, HAVING, ORDER BY, 집계함수(SUM/COUNT 등)을 활용하는 방법을 설명할 수 있다.
* having과 where의 차이에 대해서 설명할 수 있다.
~~~

## 1. 집계와 GROUP BY
- **GROUP BY** : 특정 컬럼의 같은 값끼리 모아 **그룹화**.
- 그룹화된 각 그룹에 대해 **집계 함수**를 적용해 합계, 평균, 최대/최소값 등을 계산.

### 사용법
- **집계할 컬럼**은 `SELECT`에 명시,
-  **GROUP BY 절에도 반드시 작성**해야 함.
EX)
SELECT 컬럼1, 집계함수(컬럼2)
FROM   테이블
GROUP BY 컬럼1;

#### 주요 집계 함수
* SUM() : 합계
* AVG() : 평균
* MAX() : 최대값
* MIN() : 최소값
* COUNT() : 행(row) 개수

#### DISTINCT
중복을 제거하고 유니크한 값만 조회.

EX)
-- 메인 페이지 VIEW 수: 4
SELECT COUNT(user_id) 
FROM page_view;

-- 메인 페이지를 VIEW한 유저의 수: 3
SELECT COUNT(DISTINCT user_id) 
FROM page_view;

### GROUP BY 활용 포인트
데이터 분석에서 자주 활용되는 집계 사례

* 일자별 집계 : 특정 시간대 유저 행동을 일자별로 집계
* 연령대별 집계 : 특정 연령대의 구매 현황 분석
* 제품 타입별 집계 : 어떤 제품 타입이 많이 팔렸는가?
* 앱 화면별 집계 : 어떤 화면에 유저가 많이 접근했는가?

### 조건 설정: WHERE vs HAVING

* WHERE: **그룹화 이전 원본 데이터**에 조건을 설정
* HAVING: **그룹화 이후 GROUP BY**로 집계된 결과에 조건을 설정

#### 서브쿼리
SELECT문 안에 존재하는 SELECT 쿼리.

FROM 절에 또 다른 SELECT문을 넣을 수 있음.

서브쿼리 결과에 대해 바깥쪽에서 WHERE 조건 설정 가능

#### ORDER BY & LIMIT
* ORDER BY : 쿼리 결과를 정렬.

-DESC : 내림차순

-ASC : 오름차순 (기본값)
* LIMIT : 쿼리 결과의 행(row) 수를 제한
# 2️⃣ 학습 인증란

<img width="761" height="154" alt="image" src="https://github.com/user-attachments/assets/b471da28-aa8d-4c3f-9f9e-cb97b9515e21" />




<br><br>



---

# 3️⃣ 확인문제

## 문제 1

> **🧚Q. 포켓몬 마스터 승화는 포켓몬 데이터 조회하는 SQL문에 재미를 느껴서 혼자서 데이터를 조회하는 쿼리문을 짰습니다. 하지만 세 가지의 오류로 다음 코드가 실행이 안된다고 하는데, 각 오류의 위치와 이유를 설명하고, 올바른 쿼리문으로 수정해보세요.**

~~~sql
# 승화의 SQL Query문 
SELECT name AS '포켓몬 이름', ID;
WHERE type = 'Electric';
FROM pokemon;
~~~

~~~
1. SELECT → FROM → WHERE 순서로 작성해야 한다.
2. 각 절(SELECT, WHERE, FROM)의 끝에 있는 세미콜론(세미콜론은 문장의 마지막에 한 번만 사용)
**올바른 코드**
SELECT name AS '포켓몬 이름', ID

FROM pokemon

WHERE type = 'Electric';
~~~


## 문제 2

> **🧚Q. 앞서 SQL Query의 오류를 해결한 승화는 기분 좋게 이번에는 포켓몬 데이터에서 타입별 평균 공격력이 60 이상인 타입만 조회하려는 쿼리를 작성하려고 했습니다. 하지만 이번에도 실수를 하여 쿼리문이 실행되지 않거나 잘못된 결과가 나오고 있는데, 쿼리에서 잘못된 부분이 무엇인지 설명하고, 올바르게 수정한 쿼리를 작성해보세요.**

~~~sql
SELECT type, AVG(attack) AS avg_attack
FROM pokemon
WHERE AVG(attack) >= 60
GROUP BY type;
~~~



~~~
**올바른 코드**
SELECT type, AVG(attack) AS avg_attack
FROM pokemon
GROUP BY type
HAVING AVG(attack) >= 60;

집계 함수는 개별 행이 아닌 그룹에 대한 연산을 수행.
따라서 WHERE 절에서는 사용할 수 없고, 그룹화된 결과에 조건을 적용하는 HAVING 절을 사용해야 합니다.
~~~



### 🎉 수고하셨습니다.
