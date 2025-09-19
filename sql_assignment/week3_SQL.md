# SQL_BASIC 3주차 정규 과제 

📌SQL_BASIC 정규과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고 간단한 문제를 풀면서 학습하는 것입니다. 이번주는 아래의 **SQL_Basic_3rd_TIL**에 나열된 분량을 수강하고 `학습 목표`에 맞게 공부하시면 됩니다.

**3주차 과제는 문제 풀이를 중심으로**, 강의에서 제시된 예제 문제 중 **7 문제 이상을 선택하여 직접 풀어본 뒤**, 강의 영상의 풀이와 비교해 **틀린 부분, 맞은 부분, 새롭게 배운 개념**을 구체적으로 정리해주세요. (적어도 3문제는 정리해야 합니다.) 완성된 과제는 Gihub에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**(수행 인증샷은 필수입니다.)** 

## SQL_BASIC_3rd

### 섹션 3. 데이터 탐색 - 조건, 추출, 요약

### 2-6. 연습문제 1~3번

### 2-6. 연습문제 7~9번

### 2-6. 연습문제 10~12번

### 2-6. 연습문제 13~17번

### 2-7. 정리 

### 2-8. 새로운 집계함수



## 섹션 4. 쿼리 잘 작성하기, 쿼리 작성 템플릿 및 오류를 잘 디버깅하기

### 3-1. INTRO

### 3-2. SQL 쿼리 작성하는 흐름

### 3-3. 쿼리 작성 템플릿과 생산성 도구 



## 🏁 강의 수강 (Study Schedule)

| 주차  | 공부 범위              | 완료 여부 |
| ----- | ---------------------- | --------- |
| 1주차 | 섹션 **1-1** ~ **2-2** | ✅         |
| 2주차 | 섹션 **2-3** ~ **2-5** | ✅         |
| 3주차 | 섹션 **2-6** ~ **3-3** | ✅         |
| 4주차 | 섹션 **3-4** ~ **4-4** | 🍽️         |
| 5주차 | 섹션 **4-4** ~ **4-9** | 🍽️         |
| 6주차 | 섹션 **5-1** ~ **5-7** | 🍽️         |
| 7주차 | 섹션 **6-1** ~ **6-6** | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념정리

## 2-6. 연습문제

~~~
✅ 학습 목표 :
* 연습문제(7문제 이상) 푼 것들 정리하기
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->

### 문제 2. type2가 없는 포켓몬의 type1과 type1의 포켓몬 수를 알려주는 쿼리를 작성해주세요. 단 type1의 포켓몬 수가 큰 순으로 정렬해주세요

코드.
SELECT 
  type1,
  COUNT(id) As pockemon_cnt
FROM basic.pockemon
WHERE 
  type2 IS NULL
GROUP BY
  type1
ORDER BY
  pockemon_cnt DESC

 **집계 함수는 GROUP BY와 같이 다님**. 집계하는 기준(칼럼)이 없으면 COUNT만 쓸 수 있으나 집계하는 기준이 있다면 
 그 기준 칼럼을 GROUP BY에 써줘야 함

 ### 문제 3. type2 상관없이 type1의 포켓몬 수를 알 수 있는 쿼리를 작성해주세요
 코드 
SELECT 
  type1,
  COUNT(id) As pockemon_cnt
FROM basic.pockemon
GROUP BY
  type1
type2상관없이: 이건 조건이 아님.

--- distinct 언제 쓸까? 고유한 값만 보고 싶을 때 사용함. unique한 값만 알고 싶은 경우 사용. 
--- count(id) = count(distinct id)
--- 이 데이터 같은 경우에는 id를 설계할 때 중복이 없게 설계했음 그래서 두 개의 결과가 동일
--- 어떤 컬럼은 중복이 있게 설계되곤 함
--- distinct도 걸어서 보고 어떤 값이 더 맞을까 보면 됨


### 5. 동명 이인이 있는 이름은 무엇일까요?

조건은 동명이인( 같은 이름이 2개 이상) -> COUNT(name) >= 2개 이상

코드 
SELECT 
 name,
 COUNT(name) as trainer_cnt
FROM basic.trainer
Group by
 name 
HAVING
 trainer.cnt>=2

**집계 후 조건은 HAVING인 점을 기억**
다시 정리하면
WHERE은 원본 데이터 from절에 있는 데이터에 조건을 설정하고 싶은 경우
HAVING은 GROUP BY와 함께 집계 결과에 조건을 설정하고 싶은 경우


### 7. trainer테이블에서 "IRIS","Whitney","Cynthia" 트레이너의 정보를 알 수 있는 쿼리를 작성하세요

코드 
SELECT 
 *
FROM `basic.trainer`
WHERE
(name="IRIS")
OR (name="Cynthia")
OR (name="Whitney")

정보를 가져온다 했을 때 * 사용
OR 연산자 사용시 괄호 치는 습관 들여야 실수 방지
OR 조건으로 쓰는 것이 너무 길다 -> IN 사용 가능
name IN("IRIS","Cynthia","Whitney")
이런 식으로

### 8. 전체 포켓몬 수는 얼마나 되나요?

코드

SELECT 
 COUNT(id) AS pockemon_cnt
FROM `basic.pockemon`
WHERE
(name="IRIS")
OR (name="Cynthia")
OR (name="Whitney")



### 11. type2가 있는 포켓몬 중에 제일 많은 type1은 무엇인가요? 

코드
SELECT 
 type1,
 COUNT(id) AS pockemon_cnt
FROM `basic.pockemon`
Where
 type2 is NOT NULL
Group BY 
 type1
Limit 1

제일 많은 것을 확인하는 것이기 때문에 Limit 1로 확인

### 13. 포켓몬의 이름에 '파'가 들어가는 포켓몬은 어떤 포켓몬이 있을까요?
코드
SELECT 
 kor_name,
FROM `basic.pockemon`
Where
 kor_name LIKE "%파%"
칼럼 LIKE "특정단어%. %는 앞에도 붙을 수 있고, 뒤에도 붙을 수 있음."
--"%파": 파로 끝나는 단어, "%파%":파가 들어간 단어
--문자열 칼럼에서 특정 단어가 포함되어 있는지 알고 싶은 경우에 LIKE를 사용하면 편함


### 17.트레이너 별로 풀어준 포켓몬의 비율이 20% 넘는 포켓몬 트레이너는 누구일까요? 
 풀어준 포켓몬의 비율=(풀어준 포켓몬 수/전체 포켓몬 수)
코드


SELECT 
 COUNTIF(status="Released") AS released_cnt, #풀어준 포켓몬의 수
 COUNT(pokemon_id) AS pockemon_cnt,
 COUNTIF(status="Released")/COUNT(pokemon_id) AS released_ratio
FROM `basic.trainer_pockemon`
Group By
 trainer_id
HAVING
 released_ratio >= 20

특정 조건을 바탕으로 집계를 할 시에 COUNTIF 함수 사용 가능


## 2-8. 새로운 집계함수

~~~
✅ 학습 목표 :
* SQL 쿼리 구조를 이해할 수 있다. 
* SELECT, FROM, WHERE을 활용하는 방법을 설명할 수 있다. 
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->

GROUP BY ALL: 컬럼을 명시할 필요 없이 추론해서 출력해줌

## 3-2. 쿼리를 작성하는 흐름

~~~
✅ 학습 목표 :
* 쿼리를 작성하는 흐름을 설명할 수 있다.
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->

쿼리를 작성하는 흐름
1.지표 고민- 어떤 문제를 해결하기 위해 데이터가 필요한가?(문제 정의)
2.지표 구체화 - 추상적이지 않고, 구체적인 지표 명시(분자,분모 표시) 이름을 구체적으로 작성해야 함
3.지표 탐색 - 유사한 문제를 해결한 케이스가 있나 확인, 비슷한 문제는 비슷한 지표를 사용하기 때문
4.쿼리 작성(유사한 케이스가 없을 경우) - 데이터가 잇는 테이블 찾기 - 테이블이 2개 이상일 경우 연결 방법을 고민(JOIN)
5.데이터 정합성 확인- 예상한 결과화 동일한지 확인
6.쿼리 가독성 (나중을 위해 깔끔하게 쿼리 작성)
7.쿼리 저장 - 쿼리는 재사용되므로 문서로 저장



## 3-3. 쿼리 작성 템플릿과 생산성 도구

~~~
✅ 학습 목표 :
* 생산성 도구를 만들 수 있다.
~~~
쿼리 작성 템플릿
쿼리를 작성하는 목표, 확인할 지표
쿼리 계산 방법
데이터의 기간
사용할 테이블
Join Key
데이터 특징

Espanso
특정 단어가 감지되면 정의된 것으로 바꿈
<img width="557" height="279" alt="image" src="https://github.com/user-attachments/assets/3399df09-bfdd-4fe7-bc72-8bf4ef812f3d" />




<br>
<br>

---

# 2️⃣ 학습 인증란

<img width="559" height="509" alt="image" src="https://github.com/user-attachments/assets/ccf88d5b-b539-4478-9eba-23f6a059d50d" />




<br><br>



---

# 3️⃣ 확인문제

## 문제 1

> **🧚Q. 포켓몬 게임에 재미를 느낀 동혁은 포켓몬 도감에서 강력한 포켓몬 타입을 미리 선점하기 위해, 먼저 어떤 포켓몬들이 있는지 포켓몬 수를 기준으로 내림차순 정렬하여  확인하고자 했습니다.**
>
> 그래서 다음과 같은 필요한 정보를 미리 정리해보았습니다. 

~~~
조건 : type2는 상관없이
보고 싶은 컬럼 : type1
집계 내용 : 각 type1 별 포켓몬 수
정렬 기준 : 포켓몬 수를 기준으로 내림차순 정렬
~~~

> **이 목표를 바탕으로 동혁이 아래와 같은 쿼리를 잘 작성했지만, 일부 SQL 문법 요소를 빼먹었습니다. 비어 있는 부분인 ㄱ,ㄴ,ㄷ 에 들어갈 알맞은 SQL 구문을 채워보세요:**

~~~sql
SELECT type1, (ㄱ)
FROM pokemon
(ㄴ) type1
ORDER BY (ㄱ) (ㄷ);
~~~



~~~
여기에 답을 작성해주세요!
~~~



### 🎉 수고하셨습니다.
