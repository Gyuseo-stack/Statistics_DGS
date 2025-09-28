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
대표적인 오류 카테고리
syntax error
문법을 지키지 않아 생기는 오류.
에러 메세지를 보고 번역. 구글,챗지피티에 오류 메세지 물어보기
데이터 예시나 쿼리를 제공하고, 오류가 발생한 것을 말해보기

Number of arguments does not match for aggregate function count
집계 함수 count의 인자 수가 일치하지 않는다
SELECT list expression references column type1 a which is neither grouped nor aggregated
 select 목록 식은 다음에서 그룹화되거나 집계되지 않은 열을 참조
group by에 적절한 컬럼을 명시하지 않았을 경우 발생하는 오류
세미콜론을 안 붙히고 SELECT가 한 번 더 나오묜 오류가 나올 수 있음
<img width="506" height="170" alt="image" src="https://github.com/user-attachments/assets/7ec9a3ab-ecba-47d0-b3c9-c40df4ddca93" />


## 4-2. 데이터 타입과 데이터 변환(CAST, SAFE_CAST)

~~~
✅ 학습 목표 :
* 데이터 타입의 종류를 설명할 수 있다. 
* 데이터 타입을 변환하는 방법을 설명할 수 있다. 
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->

데이터 타입 종류: 숫자,문자, (시간,날짜), 부울(Bool) 이렇게 있음
데이터 타입이 중요한 이유는 보이는 것과 저장된 것의 차이가 존재할 수 있음
ex)액셀에서 보면 빈 갓ㅂ은 ''일 수도 있고 NULL일수도 있음
   2023-12-31 같은 경우 DATE 2023 12 31일 수도 있고 문자 2023 12 31일 수도 있음
내 생각과 다른 경우 데이터의 타입을 서로 변경해야 함
자료 타입을 변경하는 함수는 cast
-> 더 안전하게 데이터 타입 변경하기 SAFE_CAST 
SAFE_가 붙은 함수는 변환이 실패할 경우 NULL 반환


## 4-3. 문자열 함수(CONCAT, SPLIT, REPLACE, TRIM, UPPER)

~~~
✅ 학습 목표 :
* 문자열 함수들의 종류를 이해하고 어떠한 상황에서 사용하는지 설명할 수 있다. 
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->
문자열 붙이기 -> CONCAT
ex) SELECT
      CONCAT("안녕","하세요","!")AS result
->출력결과: 안녕하세요!

문자열 분리하기 -> SPILT
ex) SELECT
      SPILT("가,나,다,라",",")AS result
-> ,를 기준으로 나눔 SPILT(문자열원본, 나눌 기준이 되는 문자)

특정 단어 수정하기 -> REPLACE
ex) SELECT
      REPLACE("안녕하세요","안녕","실천")AS result
REPLACE(문자열 원본,찾을 단어,바꿀 단어)

문자열 자르기 ->TRIM
ex) SELECT
      TRIM("안녕하세요","하세요")AS result
TRIM(문자열 원본,자를 단어)

영어 소문자를 대문자로 변경->UPPER

## 4-4. 날짜 및 시간 데이터 이해하기(1) (타임존, UTC, Millisecond, TIMESTAMP/DATETIME)

~~~
✅ 학습 목표 :
* 날짜 및 시간 데이터 타입과 UTC의 개념을 설명할 수 있다. 
* DATE, DATETIME, TIMESTAMP 에 대해서 설명할 수 있다.
* 시간함수들의 종류와 시간의 차이를 추출하는 방법을 설명할 수 있다. 
~~~

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->
날짜 및 시간 데이터 타입 파악하기: DATE,DATETIME,TIMESTAMP
날짜 및 시간 데이터 관련 알면 좋은 내용: UTC,Millisecond
날짜 및 시간 데이터 타입 변환하기
시간 함수(두 시간의 차이,특정 부분 추출하기)
시간 데이터도 세부적으로 나눌 수 있음
DATE DATE만 표시하는 데이터(2023-12-31)
DATETIME: DATE와 TIME까지 표시하는 데이터, time zone 정보 없음(2023-12-31-14:00:00)
TIMESTAMP: 날짜와 무관하게 시간만 표시하는 데디터(23:59:59.00)

타임존 이해하는 것이 중요
UTC: 국제적인 표준 시간, 협정 세계시
타임존이 존재한다=특정 지역의 표준 시간대(ex 한국 시간:UTC+9)

TIMESTAMP: 시간 도장
UTC부터 경관한 시간을 나타내는 값. time zone 정보 있음

Millisecond(1000분의 1초),빠른 반응이 필요한 분야에서 사용
Millisecond => TIMESTAMP =>DATETIME으로 변경

microsecond(1000분의 밀리세컨즈)
많은 회사들의 Table에 시간이 TIMESTAMP로 저장된 경우가 많음(혹은 DATETIME)
TIMESTAMP->DATETIME변환을 해야할 수 있음

<img width="607" height="236" alt="image" src="https://github.com/user-attachments/assets/77c72b4b-dbce-4bfb-8e99-6020e1e14222" />

TIMESTAMP: 타임존에 UTC가 나옴, 한국 시간-9시간
DATETIME: T가 나옴,한국zone사용시 한국 시간과 동일



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

<!-- 정답을 맞추게 되면, 정답입니다. 라는 칸이 생성되는데 이 부분을 캡처해서 이 주석을 지우시고 첨부해주시면 됩니다. --> 



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
여기에 답을 작성해주세요!
~~~



### 🎉 수고하셨습니다.
