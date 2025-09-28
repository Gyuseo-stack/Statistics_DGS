# SQL_BASIC 4주차 정규 과제 

📌SQL_BASIC 정규과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고 간단한 문제를 풀면서 학습하는 것입니다. 이번주는 아래의 **SQL_Basic_4th_TIL**에 나열된 분량을 수강하고 `학습 목표`에 맞게 공부하시면 됩니다.

**4주차 과제부터는 강의 내용을 정리하는 것과 함께, 프로그래머스에서 제공하는 SQL 문제를 직접 풀어보는 실습도 병행합니다.** 강의에서는 **배운 내용을 정리하고 주요 쿼리 예제를 정리**하며, 프로그래머스 문제는 **직접 풀어본 뒤 풀이 과정과 결과, 배운 점을 함께 기록**해주세요. 완성된 과제는 Github에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**(수행 인증샷은 필수입니다.)** 

## SQL_BASIC_4th

### 섹션 4. 쿼리 잘 작성하기, 쿼리 작성 템플릿 및 오류를 잘 디버깅하기

### 3-4. 오류를 잘 디버깅하는 방법



## 섹션 5. 데이터 탐색 - 변환

### 4-1. INTRO

### 4-2. 데이터 타입과 데이터 변환(CAST, SAFE_CAST)

### 4-3. 문자열 함수(CONCAT, SPLIT, REPLACE, TRIM, UPPER)

### 4-4. 날짜 및 시간 데이터 이해하기(1) (타임존, UTC, Millisecond, TIMESTAMP/DATETIME)



## 🏁 강의 수강 (Study Schedule)

| 주차  | 공부 범위              | 완료 여부 |
| ----- | ---------------------- | --------- |
| 1주차 | 섹션 **1-1** ~ **2-2** | ✅         |
| 2주차 | 섹션 **2-3** ~ **2-5** | ✅         |
| 3주차 | 섹션 **2-6** ~ **3-3** | ✅         |
| 4주차 | 섹션 **3-4** ~ **4-4** | ✅         |
| 5주차 | 섹션 **4-4** ~ **4-9** | 🍽️         |
| 6주차 | 섹션 **5-1** ~ **5-7** | 🍽️         |
| 7주차 | 섹션 **6-1** ~ **6-6** | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념정리

## 3-4. 오류를 디버깅하는 방법

~~~
✅ 학습 목표 :
* 오류의 정의에 대해 설명할 수 있다. 
* 오류 메시지를 보고 디버깅이라는 과정을 수행할 수 있다. 
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->
## 대표적인 오류와 해결 방법

### 1. Syntax Error (문법 오류)
- **설명**: SQL 문법을 지키지 않았을 때 발생하는 오류.
- **대처법**: 에러 메시지를 번역하거나 구글·ChatGPT에 그대로 검색해 원인을 파악하고,
  데이터 예시와 쿼리를 함께 점검한다.
### 2. 집계 함수 인자 수 불일치
- **오류 메시지**: Number of arguments does not match for aggregate function COUNT
집계 함수 count의 인자 수가 일치하지 않는다
### 3. GROUP BY 누락 오류
- **오류 메시지**: SELECT list expression references column type1 a which is neither grouped nor aggregated
집계 함수 count의 인자 수가 일치하지 않는다
COUNT(*) 같은 집계 함수와 같은 일반 컬럼을 함께 SELECT할 때,
일반 컬럼을 GROUP BY에 포함하지 않으면 발생.
-> 그룹 기준으로 묶을 컬럼을 GROUP BY에 명시.
<img width="506" height="170" alt="image" src="https://github.com/user-attachments/assets/7ec9a3ab-ecba-47d0-b3c9-c40df4ddca93" />


## 4-2. 데이터 타입과 데이터 변환(CAST, SAFE_CAST)

~~~
✅ 학습 목표 :
* 데이터 타입의 종류를 설명할 수 있다. 
* 데이터 타입을 변환하는 방법을 설명할 수 있다. 
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->

## 데이터 타입의 종류
- **숫자(Numeric)** : 정수형, 실수형 등 수치 연산이 가능한 데이터
- **문자(String/Text)** : 문자, 문자열 데이터
- **시간/날짜(Date/Time)** : 날짜(`DATE`), 시간(`TIME`), 타임스탬프(`TIMESTAMP`) 등
- **부울(Boolean)** : 참(`TRUE`)/거짓(`FALSE`) 값을 갖는 데이터

## 데이터 타입이 중요한 이유
- 화면에 보이는 값과 실제로 **저장된 데이터 타입이 다를 수 있음**.
- 예시
  - 엑셀에서 빈 값은 `''`(빈 문자열)일 수도 있고 `NULL`일 수도 있음.
  - `2023-12-31` 은 `DATE` 타입일 수도 있고, 단순 문자열 `"2023-12-31"`일 수도 있음.

→ 데이터 분석이나 처리 과정에서 **의도한 타입으로 변환**해야 정확한 연산과 비교가 가능.

## 데이터 타입 변환 방법
- **CAST 함수**  CAST(값 AS 원하는_타입)
  지정한 타입으로 변환 시도.
- **SAFE_CAST 함수**  
SAFE_CAST(값 AS 원하는_타입)
변환이 실패할 경우 **오류 대신 `NULL`**을 반환하여 안전하게 변환.

> `SAFE_` 가 붙은 함수는 변환 오류를 방지하고, 데이터 파이프라인의 안정성을 높여줌.

---

## 4-3. 문자열 함수(CONCAT, SPLIT, REPLACE, TRIM, UPPER)

~~~
✅ 학습 목표 :
* 문자열 함수들의 종류를 이해하고 어떠한 상황에서 사용하는지 설명할 수 있다. 
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->
## 문자열 관련 주요 함수와 예제

### 1. 문자열 붙이기 → **CONCAT**
여러 문자열을 하나로 합칠 때 사용.

```sql
SELECT CONCAT("안녕", "하세요", "!") AS result;
```
### 2. 문자열 분리하기 → SPLIT
특정 구분자를 기준으로 문자열을 나눌 때 사용.
```sql
SELECT SPLIT("가,나,다,라", ",") AS result;
```
### 3.특정 단어 수정하기 → REPLACE
문자열에서 특정 단어를 다른 단어로 치환.
```sql
SELECT REPLACE("안녕하세요", "안녕", "실천") AS result;
```

### 4.문자열 자르기 → TRIM
문자열 양쪽에서 특정 문자나 단어를 제거.
```sql
SELECT TRIM("안녕하세요", "하세요") AS result;
```

### 5.영어 소문자를 대문자로 변경 → UPPER
영문 문자열을 모두 대문자로 변환.
```sql
SELECT UPPER("hello world") AS result;
```

## 4-4. 날짜 및 시간 데이터 이해하기(1) (타임존, UTC, Millisecond, TIMESTAMP/DATETIME)

~~~
✅ 학습 목표 :
* 날짜 및 시간 데이터 타입과 UTC의 개념을 설명할 수 있다. 
* DATE, DATETIME, TIMESTAMP 에 대해서 설명할 수 있다.
* 시간함수들의 종류와 시간의 차이를 추출하는 방법을 설명할 수 있다. 
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->
## 날짜 및 시간 데이터 정리

### 날짜 및 시간 데이터 타입
| 타입 | 특징 | 예시 |
|------|------|------|
| **DATE** | 날짜만 저장 | `2023-12-31` |
| **DATETIME** | 날짜 + 시간 저장, **타임존 정보 없음** | `2023-12-31 14:00:00` |
| **TIMESTAMP** | UTC(협정 세계시)를 기준으로 한 **시간 도장**, 타임존 정보 포함 | `2023-12-31 23:59:59.00` |

---

### 알아두면 좋은 개념
- **UTC (Coordinated Universal Time)**  
  국제 표준시로, 전 세계가 참조하는 기준 시간.  
  - 예: 한국 표준시(KST)는 `UTC+9` (UTC 기준으로 9시간 빠름)
  - 타임존이란 각 지역이 사용하는 표준 시간대를 의미.

- **Millisecond**  
  1초의 1/1000 단위 시간. 빠른 반응이나 정밀한 로그 기록 등에서 사용.

- **Microsecond**  
  1밀리초(1/1000초)의 1/1000 단위 시간.

---

### TIMESTAMP와 DATETIME 차이
| 구분 | TIMESTAMP | DATETIME |
|------|----------|---------|
| **타임존** | UTC 기준으로 저장되며, 조회 시 설정된 로컬 타임존으로 변환 | 타임존 정보 없음 |
| **표현** | UTC 기준 시간 값 | 지역 시간 값 |
| **변환 필요성** | 글로벌 서비스에서는 TIMESTAMP를 주로 사용, 필요 시 DATETIME으로 변환 | 한국 시간 기준으로 그대로 표시 가능 |


<img width="607" height="236" alt="image" src="https://github.com/user-attachments/assets/77c72b4b-dbce-4bfb-8e99-6020e1e14222" />





<br>

<br>

---

# 2️⃣ 확인문제 & 문제 인증

## 프로그래머스 문제 

> 조건에 맞는 회원 수 구하기 (SELECT, COUNT) 
>
> **먼저 문제를 풀고 난 이후에 확인 문제를 확인해주세요**
>
> 문제 링크 
>
> :  https://school.programmers.co.kr/learn/courses/30/lessons/131535#

<!-- 문제를 풀기 위하여 로그인이  필요합니다. -->

<img width="631" height="319" alt="스크린샷 2025-09-28 오후 9 01 47" src="https://github.com/user-attachments/assets/41f49c60-51b1-4b50-b6c7-f000d37030be" />



## 문제 1

> **🧚Q. 프로그래머스 문제를 풀던 서현이는 여러 번의 시행착오 끝에 결국 혼자 해결하기 어려워 오류 메시지를 공유하며 도움을 요청했습니다. 여러분들이 오류 메시지를 확인하고, 해당 SQL 쿼리에서 어떤 부분이 잘못되었는지 오류 메시지를 해석하고 찾아 설명해주세요.**

~~~sql
# 조건에 맞는 회원 수 구하기 (SELECT, COUNT) 
# 서현이의 SQL 첫 번째 풀이
SELECT COUNT(AGE, JOINED)
FROM USER_INFO
WHERE AGE BETWEEN 20 AND 29
  AND JOINED BETWEEN '2021-01-01' AND '2021-12-31';
  
오류 메시지 : Error: Number of arguments does not match for aggregate function COUNT
 
# 수정하고 난 이후 두 번째 풀이
SELECT AGE, COUNT(*)
FROM USER_INFO
WHERE AGE BETWEEN 20 AND 29
  AND JOINED BETWEEN '2021-01-01' AND '2021-12-31';
  
오류 메시지 : SELECT list expression references column AGE which is neither grouped nor aggregated
~~~



~~~
1. `COUNT()` 집계 함수는 인수를 0개(`COUNT(*)`) 또는 1개(`COUNT(컬럼명)`)만 받을 수 있습니다.
그런데 `COUNT(AGE, JOINED)`처럼 두 개 이상의 인수를 전달했기 때문에 오류가 발생

2. `COUNT(*)`처럼 집계 함수와 `AGE`처럼 일반 컬럼을 함께 `SELECT`할 때는  
일반 컬럼을 반드시 `GROUP BY` 절에 포함해야 함.
하지만 현재 쿼리에는 `GROUP BY AGE`가 없어서
“AGE가 집계되거나 그룹화되지 않았다”라고 에러 발생
나이별 인원 수를 집계하려면 `GROUP BY AGE`를 추가해야 한다.
~~~



### 🎉 수고하셨습니다.
