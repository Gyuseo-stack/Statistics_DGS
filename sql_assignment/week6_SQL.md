# SQL_BASIC 6주차 정규 과제 

📌SQL_BASIC 정규과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고 간단한 문제를 풀면서 학습하는 것입니다. 이번주는 아래의 **SQL_Basic_6th_TIL**에 나열된 분량을 수강하고 `학습 목표`에 맞게 공부하시면 됩니다.

**6주차 과제는 강의 내용을 정리하는 것과 함께, 프로그래머스에서 제공하는 SQL 문제를 직접 풀어보는 실습도 병행합니다.** 강의에서는 **배운 내용을 정리하고 주요 쿼리 예제를 정리**하며, 프로그래머스 문제는 **직접 풀어본 뒤 풀이 과정과 결과, 배운 점을 함께 기록**해주세요. 완성된 과제는 Github에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**(수행 인증샷은 필수입니다.)** 

## SQL_BASIC_6th

### 섹션 6. 다량의 자료를 연결 : JOIN 

### 5-1. Intro

### 5-2. JOIN 이해하기

### 5-3. 다양한 JOIN 방법

### 5-4. JOIN 쿼리 작성하기 

### 5-5. JOIN을 처음 공부할 때 헷갈렸던 부분

### 5-6. JOIN 연습문제 1~2번

### 5-6. JOIN 연습문제 3~5번

### 5-7. 정리



## 🏁 강의 수강 (Study Schedule)

| 주차  | 공부 범위              | 완료 여부 |
| ----- | ---------------------- | --------- |
| 1주차 | 섹션 **1-1** ~ **2-2** | ✅         |
| 2주차 | 섹션 **2-3** ~ **2-5** | ✅         |
| 3주차 | 섹션 **2-6** ~ **3-3** | ✅         |
| 4주차 | 섹션 **3-4** ~ **4-4** | ✅         |
| 5주차 | 섹션 **4-4** ~ **4-9** | ✅         |
| 6주차 | 섹션 **5-1** ~ **5-7** | ✅         |
| 7주차 | 섹션 **6-1** ~ **6-6** | 🍽️         |

<!-- 여기까진 그대로 둬 주세요-->

<br>

---

# 1️⃣ 개념정리

## 5-2. JOIN 이해하기

~~~
✅ 학습 목표 :
* JOIN에 대한 정의와 필요성에 대해 설명할 수 있다.
~~~

#### JOIN:  **서로 다른 데이터 테이블을 연결하는 것**

- 공통적으로 존재하는 컬럼(=KEY)이 있다면, JOIN 가능

#### JOIN이 필요한 이유
- 관계형 데이터베이스 설계시 정규화 과정을 거침
- 정규화는 중복을 최소화하게 데이터를 구조화 따라서 데이터를 다양한 table에 저장해서 필요할 때 JOIN해서 사용

EX). trainer_pokemon 테이블의 trainer_id와 trainer 테이블의 id를 기준으로 두 테이블 연결

~~~
select
  tp *,
  t *
from trainer_pokemon as tp
left join trainer as t
 on tp.trainer_id=t.id
~~~

## 5-3. 다양한 JOIN 방법

~~~
✅ 학습 목표 :
* JOIN 방법들의 종류를 설명할 수 있다. 
* 각 JOIN 방법들의 차이점에 대해서 설명할 수 있다. 
~~~

#### (INNER) JOIN : 두 테이블의 공통 요소만 연결
#### LEFT/RIGHT JOIN : 왼쪽/오른쪽 테이블 기준으로 연결
#### FULL(OUTER) JOIN : 양쪽 기준으로 연결
#### CROSS JOIN : 두 테이블의 각각의 요소를 곱하기

<img width="956" height="460" alt="image" src="https://github.com/user-attachments/assets/641d2594-6c32-4633-bf2d-f3ff71b81382" />

<img width="956" height="327" alt="image" src="https://github.com/user-attachments/assets/670a1a6a-a96b-405c-9af1-e9d28a2e1398" />



## 5-4. JOIN 쿼리 작성하기 

~~~
✅ 학습 목표 :
* JOIN을 사용한 문법에 대해 이해하여 적용할 수 있다.
* JOIN 을 활용한 쿼리를 작성할 수 있다. 
~~~

#### JOIN 작성하는 흐름
1. 테이블 확인 - 테이블에 저장된 데이터. 컬럼 확인
2. 기준 테이블 정의 - 가장 많이 참고할 기준 테이블 정의
3. JOIN KEY 찾기 - 여러 Table과 연결할 KEY(ON) 정리
4. 결과 예상하기 - 결과 테이블을 예상해서 손 , 액셀로 작성
5. 쿼리 작성/ 검증 - 예상한 결과와 동일한 결과가 나오는지 확인

#### SQL JOIN 문법

- FROM 하단에 JOIN할 Table을 작성하고 ON 뒤에 공통된 컬럼을 작성
~~~
EX)
SELECT
  A.col1,
  A.col2,
  B.col1,
  B.col2
FROM table1 AS A
LEFT JOIN table2 AS B
ON A.key = B.key

~~~

<img width="646" height="340" alt="image" src="https://github.com/user-attachments/assets/95b73de5-1bb2-4136-81f1-edb320c38457" />


### SQL JOIN에서 헷갈릴 부분 

1. 여러 조인 중 어떤 것 사용할지
   - 교집합: inner
   - 모든 조합: cross
   - 그 외: left 추천
     
2. 어떤 Table을 왼쪽에 둘지
   - 기준이 되는 table이 왼쪽에
   - 여기서 기준은 **데이터 요소가 빠짐없이 존재하는지**

3. 여러 Table연결 가능한지
   - 여러 Table끼리 연결 가능하지만, 많이 연결할 경우 점검 필요
     
4. 컬럼은 모두 다 선택해야 하는지
   - 비용 발생을 고려하여 사용하지 않을 컬럼은 선택 X
     
5. NULL은 무엇인지
   - NULL: 값이 없음, 알 수 없음
   - 0이나 공백과 다르게 값이 아예 없는 것
   - JOIN에서는 연결할 값이 없는 경우 나타남


## 5-6. JOIN 연습문제 1~5번 

~~~
✅ 학습 목표 :
* 연습문제(3문제 이상) 푼 것들 정리하기
~~~

### 문제 1 트레이너가 보유한 포켓몬들은 얼마나 있는지 알 수 있는 쿼리를 작성해주세요

-- 보유했다는 정의는 status가 Active,Training인 경우를 의미
-- Released는 방출했다는 것을 의미
-- 쿼리 계산 방법 : trainer_pokemon + pokemon JOIN => 그 후에 GROUP BY 집계

코드 
~~~
SELECT
kor_name as pokemon_name, 
count(id) as pokemon_cnt
FROM(
SELECT
  tp.trainer_id,
  tp.pokemon_id,
  tp.status,
  t.id,
  p.id,
  p.kor_name
FROM basic.trainer_pokemon as tp 
LEFT JOIN basic.pokemon as p
on tp.pokemon_id = p.id
LEFT JOIN basic.trainer as t
on tp.trainer_id = t.id
where status in("Active", "Trainig")
)
group by kor_name

~~~

### 문제 2. 각 트레이너가 가진 포켓몬 중에서 'Grass' 타입의 포켓몬 수 계산

-- 쿼리 계산 방법 : 트레이너가 보유한 포켓몬 조건 설정 => Grass 타입으로 Where 조건 걸어서 COUNT
-- JOIN KEY : trainer_pokemon의 pokemon_id 와 pokemon의 id join

코드 
~~~
select
type1,
count(tp.id) as pokemon_cnt
from
(SELECT
id,
trainer_id,
pokemon_id,
status
FROM basic.trainer_pokemon 
where status in ("Active", "Training")
) as tp
left join basic.pokemon as p 
on tp.pokemon_id = p.id
where type1 = "Grass"
group by type1
~~~


### 문제 3. 트레이너의 고향과 포켓몬을 포획한 위치를 비교하여, 자신의 고향에서 포켓몬을 포획한 트레이너 수 계산

-- 쿼리 계산 방법: trainer(hometown), trainer_pokemon JOIN => hometown = location => 트레이너 수 카운트

-- JOIN KEY : trainer_pokemon의 trainer_id 와 trainer의 id join

코드 
~~~
select
  count(distinct tp.trainer_id) as trainer_uniq, 
  count(tp.trainer_id) as trainer_cnt
from basic.trainer_pokemon as tp
left join basic.trainer as t
on tp.trainer_id = t.id
where 
  tp.location is not null 
  and location = hometown
~~~

<br>

<br>

---

# 2️⃣ 확인문제 & 문제 인증

## 프로그래머스 문제 

https://school.programmers.co.kr/learn/courses/30/lessons/164673

> 조건에 부합하는 중고거래 댓글 조회하기 (JOIN)

https://school.programmers.co.kr/learn/courses/30/lessons/144854

> 조건에 맞는 도서와 저자 리스트 출력하기 (JOIN)

#### 조건에 부합하는 중고거래 댓글 조회하기
<img width="1080" height="531" alt="스크린샷 2025-11-10 오후 5 35 37" src="https://github.com/user-attachments/assets/89d9ea85-d53d-4ec1-87a0-f06a44a100a3" />


#### 조건에 맞는 도서와 저자 리스트 출력하기

<img width="1080" height="531" alt="스크린샷 2025-11-10 오후 5 39 17" src="https://github.com/user-attachments/assets/6d1e2970-5e13-412f-9a7f-dd130ba24aca" />

---

# 3️⃣ 참고자료

JOIN 에 대해서 그림으로 쉽게 이해할 수 있는 자료들도 있어서 첨부합니다. 아래의 블로그도 학습할 때 같이 참고해주세요.

1. https://data-marketing-bk.tistory.com/entry/SQL-JOIN-%ED%95%9C-%EB%B0%A9%EC%97%90-%EC%A0%95%EB%A6%AC-%EA%B0%9C%EB%85%90%EB%B6%80%ED%84%B0-%EC%BD%94%EB%93%9C%EA%B9%8C%EC%A7%80-%EC%9D%B4%EA%B2%83%EB%A7%8C-%EB%B3%B4%EC%9E%90



2. https://velog.io/@wijoonwu/JOIN

<br>

### 🎉 수고하셨습니다.
