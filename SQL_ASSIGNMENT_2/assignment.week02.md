# SQL_ADVANCED 2주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_2nd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=_JURyg_KzHE&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=7
https://www.youtube.com/watch?v=6qkPy7RfLqQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=8
https://www.youtube.com/watch?v=WWAFAm9op2U&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=9
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_2nd_TIL

### 3장 SQL 기본 문법
#### 01. 기본 중에 기본 SELECT ~ FROM ~ WHERE
#### 02. 좀 더 깊게 알아보는 SELECT문
#### 03. 데이터 변경을 위한 SQL문


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | 🍽️         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 기본 중에 기본 SELECT ~ FROM ~ WHERE

<!-- 기본적인 SQL 문법에 관해 배우게 된 점을 적어주세요. -->

<!-- 이번 챕터에서 제시된 실습을 흐름에 맞게 진행한 후, 실습 과정이 보일 수 있도록 인증 사진을 3~4장 제출해 주세요. -->
<img width="754" height="496" alt="스크린샷 2026-03-11 오전 2 49 45" src="https://github.com/user-attachments/assets/d37110d3-2e16-4471-875b-86717f3962ca" />

<img width="793" height="528" alt="스크린샷 2026-03-11 오전 2 55 28" src="https://github.com/user-attachments/assets/d5ba2667-a573-4ce1-999b-0596ba352ad5" />

<img width="793" height="528" alt="스크린샷 2026-03-11 오전 2 57 35" src="https://github.com/user-attachments/assets/90bc9860-b185-493f-9a85-427b2b997dd5" />

<img width="793" height="528" alt="스크린샷 2026-03-11 오전 3 00 44" src="https://github.com/user-attachments/assets/63877a40-67ad-40ed-93c3-8f39698c45e3" />



> **확인문제: 다음 SQL문의 빈칸에 들어갈 WHERE절의 문법으로 틀린 것을 고르세요.**

```sql
SELECT *
FROM table_name
WHERE ________;
```

보기는 아래와 같습니다.
```
1. mem_number == 4
2. mem_number >= 4
3. mem_number <= 4
4. mem_number = 4
```

```
1.mem_number == 4
SQL에서는 같다라는 비교를 할 때 = 연산자를 사용
```


## 2. 좀 더 깊게 알아보는 SELECT문

<!-- ORDER BY절과 GROUP BY절에 관해 배우게 된 점을 적어주세요. -->
#### ORDER BY

- **데이터 조회 결과를 정렬하는 절**
- 기본 정렬 방식은 ASC(오름차순)이며, DESC(내림차순)으로도 정렬 가능

#### GROUP BY
- 같은 값을 가진 데이터들을 그룹으로 묶는 절
- 주로 집계 함수(COUNT, SUM, AVG, MAX, MIN)와 함께 사용

> **확인문제: 다음 표는 주요 집계함수를 정리한 것입니다. 각 설명에 해당하는 올바른 함수명을 기호에 맞게 작성하세요.**

| 함수명 | 설명 |
|--------|------|
| SUM() | 합계를 구합니다. |
| (ㄱ) | 평균을 구합니다. |
| (ㄴ) | 최소값을 구합니다. |
| MAX() | 최대값을 구합니다. |
| (ㄷ) | 행의 개수를 셉니다. |
| (ㄹ) | 행의 개수를 셉니다 (중복은 1개만 인정). |

```
여기에 답을 적어주세요!
(ㄱ) AVG()
(ㄴ) MIN()
(ㄷ) COUNT()
(ㄹ) COUNT(DISTINCT)
```


## 3. 데이터 변경을 위한 SQL문

<!-- INSERT문, UPDATE문, DELETE문에 관해 배우게 된 점을 적어주세요. -->

#### INSERT

- **테이블에 새로운 데이터를 추가하는 SQL 문**
- 컬럼을 지정하거나 전체 컬럼 순서대로 값을 넣을 수 있음
- **AUTO_INCREMENT**가 설정된 컬럼은 값을 입력하지 않아도 **자동으로 증가하는 값이 생성**

~~~
INSERT INTO member (mem_name, mem_number)
VALUES ('블랙핑크', 4);
~~~
#### UPDATE
기존 데이터를 수정하는 SQL 문
보통 WHERE절과 함께 사용하여 특정 행만 수정
**WHERE를 사용하지 않으면 테이블 전체 데이터가 수정**

~~~
UPDATE member
SET mem_number = 5
WHERE mem_name = '블랙핑크';
~~~

#### DELETE
테이블의 데이터를 삭제하는 SQL 문
WHERE절을 사용해 특정 데이터만 삭제 가능

~~~
DELETE FROM member
WHERE mem_name = '블랙핑크';
~~~

> **확인문제: 다음이 설명하는 SQL이 무엇인지 쓰세요.**

```
* 데이터를 삭제합니다.
* DELETE와 동일한 효과를 내지만 속도가 무척 빠릅니다.
* 삭제 후에 빈 테이블이 남아 있습니다.
```

```
TRUNCATE
```


---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + shift + Enter)** 하여 데이터베이스를 구축하세요.

```sql
-- 1. 데이터베이스 생성
CREATE DATABASE IF NOT EXISTS week2_db;

-- 2. 사용할 데이터베이스 선택
USE week2_db;

-- 4. 테이블 생성
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(20),
    major VARCHAR(30),
    grade INT,
    age INT,
    gpa DECIMAL(3,2),
    admission_year INT
);

-- 5. 데이터 삽입
INSERT INTO students VALUES
(1, '진아', 'Statistics', 1, 19, 3.85, 2024),
(2, '혜인', 'Computer Science', 2, 20, 3.20, 2023),
(3, '규서', 'Business', 3, 22, 2.95, 2022),
(4, '규영', 'Statistics', 4, 23, 3.60, 2021),
(5, '철원', 'Economics', 2, 21, 3.75, 2023),
(6, '예운', 'Computer Science', 1, 19, 3.10, 2024),
(7, '민서', 'Statistics', 3, 22, 3.45, 2022);
```
## 2. 실습 문제

다음 SQL 문을 작성하고 실행 결과를 확인 후 인증 사진을 아래에 업로드하세요.

1. 모든 학생의 정보를 조회하시오.
2. 전공이 'Statistics'인 학생을 조회하시오.
3. 현재 students 테이블에 존재하는 서로 다른 전공의 개수를 구하시오.
4. 나이가 20 이상이고 GPA가 3.5 이상인 학생을 조회하시오.
5. students 테이블에 본인의 정보를 직접 INSERT 하시오. (INSERT 실행 후, 데이터가 정상적으로 추가되었는지 확인할 수 있도록 조회 결과까지 포함하여 캡처하시오.)

1
<img width="520" height="458" alt="image" src="https://github.com/user-attachments/assets/1844093e-3827-405b-81e9-21a7c6139e7a" />

2
<img width="520" height="458" alt="image" src="https://github.com/user-attachments/assets/a6bfe8cd-1a9e-496e-8a12-1b7887241b09" />

3
<img width="520" height="458" alt="image" src="https://github.com/user-attachments/assets/839513a1-669e-49f6-9f3e-b0fbfc25abea" />

4
<img width="520" height="458" alt="image" src="https://github.com/user-attachments/assets/d3577076-1cab-4d32-b27e-3ded5156dd48" />

5
<img width="520" height="458" alt="image" src="https://github.com/user-attachments/assets/87908a0a-1fd0-4a05-a22f-b28af595b1bd" />

### 🎉 수고하셨습니다.
