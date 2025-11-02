# SQL_BASIC 5주차 정규 과제 

📌SQL_BASIC 정규과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고 간단한 문제를 풀면서 학습하는 것입니다. 이번주는 아래의 **SQL_Basic_5th_TIL**에 나열된 분량을 수강하고 `학습 목표`에 맞게 공부하시면 됩니다.

**5주차 과제는 문제 풀이를 중심으로**, 강의에서 제시된 예제 문제 중 **3 문제 이상을 선택하여 직접 풀어본 뒤**, 강의 영상의 풀이와 비교해 **틀린 부분, 맞은 부분, 새롭게 배운 개념**을 구체적으로 정리해주세요. (적어도 4문제는 정리해야 합니다.) 완성된 과제는 Gihub에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**(수행 인증샷은 필수입니다.)** 

<img width="687" height="388" alt="image" src="https://github.com/user-attachments/assets/c38e188f-a650-4cdf-bc4e-32a52e6a3f1a" />


## SQL_BASIC_5th

### 섹션 5. 데이터 탐색 - 변환

### 4-4. 날짜 및 시간 데이터 이해하기(2) (EXTRACT, DATETIME_TRUNC, PARSE_DATETIME, FROMAT_DATETIME)

### 4-5. 시간 데이터 연습문제 1~2번

### 4-5. 시간 데이터 연습문제 3~5번

### 4-6. 조건문 (CASE WHEN, IF)

### 4-7. 조건문 연습 문제

### 4-8. 정리

### 4-9. BigQuery 공식 문서 확인하는 법

(강의에서 연습문제가 많아서 따로 프로그래머스 문제 과제는 없습니다.)



## 🏁 강의 수강 (Study Schedule)

| 주차  | 공부 범위              | 완료 여부 |
| ----- | ---------------------- | --------- |
| 1주차 | 섹션 **1-1** ~ **2-2** | ✅         |
| 2주차 | 섹션 **2-3** ~ **2-5** | ✅         |
| 3주차 | 섹션 **2-6** ~ **3-3** | ✅         |
| 4주차 | 섹션 **3-4** ~ **4-4** | ✅         |
| 5주차 | 섹션 **4-4** ~ **4-9** | ✅         |
| 6주차 | 섹션 **5-1** ~ **5-7** | 🍽️         |
| 7주차 | 섹션 **6-1** ~ **6-6** | 🍽️         |

<br>



<!-- 여기까진 그대로 둬 주세요-->

---

# 4-4. 날짜 및 시간 데이터 이해하기(2) (EXTRACT, DATETIME_TRUNC, PARSE_DATETIME, FROMAT_DATETIME)

~~~
✅ 학습 목표 :
* 날짜 및 시간 데이터에 대해서 더 자세히 설명할 수 있다. 
* CURRENT_TIME, EXTRACT, DATETIME_TRUNC, PARSE_DATETIME, FROMAT_DATETIME 을 설명할 수 있다. 
~~~


### 1. CURRENT_DATETIME()

**설명:**  

현재의 날짜와 시간을 반환  

**예시**
```sql
SELECT CURRENT_DATETIME();
-- 결과: 2025-11-02 17:30:00
```
**활용 예시**
- 데이터 적재 시점 기록
- 로그 생성 시간 표시

### 2. EXTRACT()

**설명:**
DATETIME 값에서 특정 부분(연, 월, 일, 요일 등)을 추출

**예시**
```sql
SELECT EXTRACT(DAYOFWEEK FROM DATETIME '2024-05-15 12:00:00') AS day;
-- 결과: 4 
```
**활용 예시**
- 요일별 주문 수 집계
- 월별/연도별 매출 분석
- 
### 3. DATETIME_TRUNC()

**설명:**
DATETIME 값을 지정한 단위(연, 월, 일, 시 등)로 잘라내고 나머지를 0으로 채움

**예시**
```sql
SELECT DATETIME_TRUNC(DATETIME '2024-03-15 14:45:10', HOUR);
-- 결과: 2024-03-15 14:00:00
```
**활용 예시**
- 시간 단위별 수요 분석 (예: 1시간 단위 주문량 집계)
- 일자 단위별 방문자 수 측정

- 
📌 TIP:
**EXTRACT는 “값을 꺼낼 때”
DATETIME_TRUNC는 “시간 단위를 자를 때” 사용**

### 4. PARSE_DATETIME()
**설명:**
문자열 형태의 날짜·시간 데이터를 DATETIME 타입으로 변환

**예시**
```sql
SELECT PARSE_DATETIME('%Y-%m-%d %H:%M:%S', '2024-02-05 15:30:00') AS dt;
-- 결과: 2024-02-05 15:30:00
```
**활용 예시**
- CSV 등 외부 데이터에서 문자열로 저장된 시간 데이터를 변환
- 
### 5. FORMAT_DATETIME()
**설명:**
DATETIME 값을 특정 형식의 문자열로 변환
(PARSE_DATETIME의 반대 개념)

**예시**
```sql
SELECT FORMAT_DATETIME('%Y-%m-%d %H:%M:%S', DATETIME '2024-02-05 15:30:00');
-- 결과: '2024-02-05 15:30:00'
```

**활용 예시**
- UI나 리포트용 날짜 포맷 지정

### 6. LAST_DAY()
설명:
해당 날짜가 속한 달의 마지막 날짜를 반환한다.
**예시**
```sql
SELECT LAST_DAY('2024-02-05');
-- 결과: 2024-02-29
```
**활용 예시**
- 월말 결산, 급여 정산, 월별 보고서 작성

### 7. DATETIME_DIFF()
**설명:**
두 DATETIME 간의 차이를 지정한 단위(DAY, HOUR, MONTH 등)로 계산
**예시**
```sql
SELECT DATETIME_DIFF('2024-03-15 14:00:00', '2024-03-14 14:00:00', DAY) AS day_diff;
-- 결과: 1
```
**활용 예시**
- 체류 시간 계산
- 이벤트 간격 분석
- 주문 주기 측정
### EXTRACT vs DATETIME_TRUNC 비교

- EXTRACT	특정 값만 추출	EXTRACT(HOUR FROM datetime)	14
- DATETIME_TRUNC	단위별로 잘라 0으로 채움	DATETIME_TRUNC(datetime, HOUR)	2024-03-15 14:00:00
- 
**활용 구분:**
- EXTRACT → “요일별, 월별 통계”
- DATETIME_TRUNC → “시간 단위 집계”


# 4-6. 조건문(CASE WHEN, IF)

~~~
✅ 학습 목표 :
* 조건문 함수의 기능을 이해하고, 설명할 수 있다. 
~~~

## 개념
- **조건문**은 “특정 조건이 충족되면 어떤 행동을 수행하자”는 논리를 구현할 때 사용된다.  
- 특정 조건이 참(True)일 때 A, 거짓(False)일 때 B를 수행하도록 분기 처리한다.  
- 데이터 분석 시 **카테고리 통합**, **전처리**, **조건 기반 그룹화** 등에 자주 활용된다.  



## 조건문이 필요한 이유
- 데이터 저장 시에는 원본 형태를 유지하고,  
  **분석 시점에서 조건을 걸어 변형하는 것이 더 유용**  
- 저장 단계에서 합쳐버리면, 나중에 세분화된 분석이 어려워짐.  
  → 따라서 **조건문으로 분석 단계에서 처리**하는 것이 이상적.



## 조건문 사용 방법
1. `CASE WHEN` : 여러 조건이 있을 때  
2. `IF` : 단일 조건일 때  


##  1. CASE WHEN

### 설명
- 여러 조건을 순차적으로 검사하여 해당 조건이 참일 때 결과를 반환한다.  
- **조건 순서가 매우 중요**하다.  
  → 조건1과 조건2 모두 참일 경우, **앞선 조건(조건1)**이 우선 적용
- 문자열 비교나 구간 분류 시 자주 사용됨.



### 문법
```sql
SELECT 
  CASE 
    WHEN 조건1 THEN '조건1이 참일 경우 결과'
    WHEN 조건2 THEN '조건2가 참일 경우 결과'
    ELSE '그 외 조건일 경우 결과'
  END AS 새로운_컬럼_이름
FROM 테이블명;
```
##  2. IF
### 설명
단일 조건 판단 시 간단하게 사용할 수 있는 함수.
조건이 TRUE면 첫 번째 값을, FALSE면 두 번째 값을 반환한다.


### 문법
```sql
SELECT
  IF(조건문, TRUE일 때의 값, FALSE일 때의 값) AS 새로운_컬럼_이름
FROM 테이블명;
```


 # 4-5. 시간 데이터 연습문제 & 4-7. 조건문 연습 문제

~~~
✅ 학습 목표 :
* 4-5, 4-7 각각에서 두 문제 이상 (최소 4문제) 푼 내용 정리하기
~~~

## 시간 데이터 연습문제

### 1. 트레이너가 포켓몬을 포획한 날짜(catch_date)를 기준으로, 2023년 1월에 포획한 포켓몬의 수를 계산해주세요.

**데이터 검증을 위한 코드**
```sql
SELECT 
  id,
  catch_date,
  DATE(DATETIME(catch_datetime, "Asia/Seoul")) AS catch_datetime_kr_date
FROM basic.trainer_pockemon
WHERE
  catch_date = DATE(DATETIME(catch_datetime, "Asia/Seoul"))
```
**컬럼의 이름은 datetime인데 데이터셋 확인 시 TIMESTAMP 타입으로 저장되어 있음**
- 컬럼의 이름만 믿고 바로 쿼리를 작성하는 것이 아니라 꼭 데이터를 확인해야 함
- catch_date가 UTC 기준인지,KR 기준인지 확인 필요
- 
catch_date 컬럼 
catch_date != DATE(DATETIME(catch_datetime,"Asia/Seoul")) ==>
있다면 catch_date는 사용하기 어려울 수 있음

**문제 코드**
```sql
SELECT
Count(DISTINCT id) AS cnt
From basic.trainer_pockemon
Where
EXTRACT(YEAR From DATETIME(catch_datetime,"Asia/Seoul"))=2023
AND EXTRACT(MONTH FROM DATETIME(catch_datetime,"Asia/Seoul"))=1
```
---

### 2. 배틀이 일어난 시간(battle_datetime)을 기준으로, 오전 6시에서 오후 6시 사이에 일어난 배틀의 수를 계산해주세요

**문제 코드**
```sql
SELECT
COUNT(DISTINCT id) AS battle_cnt
FROM basic.battle
WHERE
EXTRACT(HOUR FROM battle_datetime)>=6
AND EXTRACT (HOUR FROM battle_datetime)<18
```
**시간대별로 몇 건이 있는가?**
```sql
 SELECT
hour,
count(DISTINCT id) AS battle_cnt
FROM(
  SELECT *,
  EXTRACT(HOUR FROM battle_datetime) AS hour
  FROM basic.battle
)
GROUP BY
hour
ORDER BY
hour  
```

---

## 조건문 연습문제

### 1. 포켓몬의 'Speed'가 70이상이면 '빠름', 그렇지 않으면 '느림'으로 표시하는 새로운 컬럼 'Speed_Category'를 만들어 주세요

**문제 코드**
```sql
SELECT
*,
IF(speed>=70,'빠름','느림')AS Speed_category
From basic.pockemon
```

### 2. 포켓몬의 'type1'에 따라 'Water','Fire','Electric'타입은 각각 '물','불','전기'로 그 외 타입은 '기타'로 분류하는 개로운 컬럼 'type_Korean'을 만들어 주세요

```sql
SELECT
id,
kor_name,
type1,
CASE
WHEN type1="Water" THEN "물"
WHEN type1="Fire" THEN "불"
WHEN type1="Electric" THEN "전기"
Else "기타"
END AS type1_Korean
From basic.pockemon
```

### 3. 각 포켓몬의 총점을 기준으로 300이하면 'LOW', 301에서 500사이면 'Medium',501이상이면 'High'로 분류해주세요

```sql
SELECT
id,
kor_name,
total,
CASE
WHEN total>=500 THEN "High"
WHEN total BETWEEN 300 AND 500 THEN "Medium"
Else "Low"
END AS total_grade
From basic.pockemon
```


### Bigquery 공식 문서 확인하는 법

- 개발 공식 문서는 해당 기술을 어떻게 사용하면 좋을 지에 대하여 참고하는 문서
- "기술명+documnetation"으로 검색
- 공식 문서에서 찾기(ctrl+f)를 통해 검색

<br>


<br>

---

# 확인문제

## 문제 1

> **🧚Q. 광윤이는 사용자 로그 데이터에서, 2021년에 접속한 사용자 수를  집계하려고 했습니다. 그는 여러 SQL 쿼리들을 실행해봤지만, 그 중 일부는 문법적으로 잘못되어 실행되지 않았습니다. 다음 보기 중 틀린 쿼리를 모두 골라보세요 (복수 선택 가능)**

~~~sql
1. SELECT COUNT(*)  
   FROM user_log  
   WHERE EXTRACT(YEAR FROM login_date) = 2021;

2. SELECT EXTRACT(YEAR FROM login_date), COUNT(*)  
   FROM user_log  
   GROUP BY EXTRACT(YEAR FROM login_date);

3. SELECT COUNT(*)  
   FROM user_log  
   WHERE login_date = '2021';

4. SELECT COUNT(*)  
   FROM user_log  
   WHERE login_date BETWEEN '2021-01-01' AND '2021-12-31';
~~~

<!-- 틀린쿼리에 대한 오류의 원인도 같이 작성해주세요. 문제에서 제공된 login_data 컬럼은 DATE type의 데이터를 가지고 있다고 가정하시면 됩니다. -->

~~~
3번.
login_date는 DATE 타입인데 '2021'은 유효한 DATE 형식이 아님
-DATE 타입은 반드시 'YYYY-MM-DD' 형식이어야 함-
~~~



## 문제 2

> **🧚Q. 혜성이는 포켓몬 타입에 따라 설명을 부여하는 쿼리를 작성했습니다. type 1 컬럼의 값에 따라 조건을 분기했으며, 다음 SQL 쿼리를 실행했습니다.**

~~~sql
SELECT name,
       CASE 
         WHEN type1 = 'Fire' THEN 'Hot'
         WHEN type1 = 'Water' THEN 'Cool'
         ELSE 'Normal'
       END AS type_description
FROM pokemon;
~~~

> **다음 중 type_description의 결과가 'Normal'로 출력될 포켓몬은?**

| **name**   | **type1** |
| ---------- | --------- |
| Pikachu    | Electric  |
| Charmander | Fire      |
| Squirtle   | Water     |
| Bulbasaur  | Grass     |

<!-- 근거와 함께 답을 작성해주세요 -->

~~~
type1이 'Fire'나 'Water'가 아닌 경우 ELSE 절에 의해 'Normal'이 출력되므로, 타입이 Electric인 Pikachu와 Grass인 Bulbasaur가 해당한다.
~~~



<br>

### 🎉 수고하셨습니다.
