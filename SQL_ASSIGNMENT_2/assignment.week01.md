# SQL_ADVANCED 1주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_1st_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=0cRhit1EJM0&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=1
https://www.youtube.com/watch?v=6JFEJWLcKUc&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=2
https://www.youtube.com/watch?v=8r1W_7nuo2U&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=3
https://www.youtube.com/watch?v=j2DAiY-OXGs&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=4
https://www.youtube.com/watch?v=EftIRlr6rPI&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=5
https://www.youtube.com/watch?v=lBk5YhLZevs&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=6
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_1st_TIL

### 1장 데이터베이스와 SQL
#### 01. 데이터베이스 알아보기
#### 02. MySQL 설치하기
### 2장 실전용 SQL 미리 맛보기
#### 01. 건물을 짓기 위한 설계도: 데이터베이스 모델링
#### 02. 데이터베이스 시작부터 끝까지
#### 03. 데이터베이스 개체 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | 🍽️         |
| 3주차 | p.158~213  | 🍽️         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 데이터베이스 알아보기

<!-- 데이터베이스와 DBMS에 관해 배우게 된 점을 적어주세요. -->
## 1. 데이터베이스 알아보기

### DBMS란?

**DBMS**는
데이터베이스를 **관리하고 운영하는 소프트웨어**를 의미

사용자는 DBMS를 통해 데이터를 저장, 조회, 수정, 삭제할 수 있으며  
대량의 데이터를 효율적으로 관리할 수 있음

**대표적인 DBMS 예시**
- MySQL
- Oracle
- SQL Server
- MariaDB

---

### DBMS의 유형

| 유형 | 설명 |
|---|---|
| 계층형 DBMS | 트리 구조 형태로 데이터를 관리 |
| 망형 DBMS | 데이터 간 관계가 네트워크 형태로 연결 |
| 관계형 DBMS | 데이터를 테이블 형태로 관리 |
| 객체지향 DBMS | 객체 개념을 기반으로 데이터 저장 |

현재는 **관계형 DBMS(RDBMS)** 가 가장 널리 사용되고 있음

---

### 관계형 DBMS (RDBMS)

**RDBMS** 는  
모든 데이터를 **테이블(Table) 형태로 관리하는 데이터베이스 시스템**

데이터는 **행** 과 **열** 로 구성된 구조로 저장

대표적인 RDBMS
- MySQL
- Oracle
- PostgreSQL
- SQL Server
- MariaDB

> **확인문제: 다음 소프트웨어 중에서 DBMS가 아닌 것을 모두 고르세요.**

> MySQL / Excel / Oracle / SQL Server / MariaDB

```
Excel
```


## 2. MySQL 설치하기

<!-- 이번 챕터는 개념정리 없이 MySQL 설치 후 인증사진으로 대체합니다. -->

<img width="1019" height="817" alt="image" src="https://github.com/user-attachments/assets/867d4414-7714-4145-97ac-85c37917ea8a" />



## 3. 건물을 짓기 위한 설계도: 데이터베이스 모델링

<!-- 데이터베이스 모델링에 관해 배우게 된 점을 적어주세요. -->
### 소프트웨어 개발 절차

소프트웨어 개발은 일반적으로 **폭포수 모델** 을 기반으로 설계
(폭포수 모델은 각 단계가 **순차적으로 진행되는 개발 방식**)

#### 소프트웨어 개발 단계

1. **프로젝트 계획**  

2. **업무 분석**  

3. **시스템 설계**  

4. **프로그램 구현**  

5. **테스트**  

6. **유지보수**  

---

## 3. 데이터베이스 모델링

**데이터베이스 모델링** 은  
현실 세계에서 사용되는 **사물이나 업무를 데이터베이스 구조로 변환하는 과정**

즉, 현실에서 사용하는 정보를 **DBMS에서 관리할 수 있도록 데이터베이스 객체로 설계하는 작업**




> **확인문제: 다음은 폭포수 모델의 절차입니다. 차례대로 나열해보세요.**

> 시스템 설계 / 테스트 / 프로그램 구현 / 프로젝트 계획 / 업무 분석 / 유지보수

```
프로젝트 계획 -> 업무 분석 -> 시스템 설계 -> 프로그램 구현 -> 테스트 -> 유지보수
```


## 4. 데이터베이스 시작부터 끝까지 

<!-- 이번 챕터는 개념정리 없이 실습 인증사진으로 대체합니다. 강의를 수강하고, 실습 과정이 보이도록 인증사진 3-4장을 아래에 제출해주세요. -->

<img width="632" height="496" alt="스크린샷 2026-03-09 오전 2 47 16" src="https://github.com/user-attachments/assets/fdd45f8b-33a5-48ea-b1f9-d8ce8ab73484" />

<img width="632" height="496" alt="스크린샷 2026-03-09 오전 2 49 57" src="https://github.com/user-attachments/assets/78ea108a-9314-4104-957c-edfbd78cb30d" />

<img width="536" height="496" alt="스크린샷 2026-03-09 오전 2 53 21" src="https://github.com/user-attachments/assets/c8b51672-0d41-40ab-82f2-07d60ec684b2" />


## 5. 데이터베이스 개체

<!-- 데이터베이스 개체에 관해 배우게 된 점을 적어주세요. -->

<!-- 인덱스, 뷰, 스토어드 프로시저 실습을 각각 진행한 후, 각 실습에 대한 인증 사진을 1장씩 제출해 주세요. -->

### 인덱스

<img width="536" height="496" alt="스크린샷 2026-03-09 오전 2 59 56" src="https://github.com/user-attachments/assets/349cec3a-0c14-48b0-9842-b24131f6d87c" />

### 뷰

<img width="536" height="393" alt="스크린샷 2026-03-09 오전 3 02 44" src="https://github.com/user-attachments/assets/7cc20882-95e5-45fc-8cff-ca8d3e60b51e" />

### 스토어드 프로시저

<img width="653" height="341" alt="스크린샷 2026-03-09 오전 3 11 59" src="https://github.com/user-attachments/assets/cf86b6e8-82ba-4701-9af8-d77a99047b2f" />


---

# 2️⃣ 실습과제

> SQL ADVANCED 과정은 별도의 확인문제가 없습니다. 다음 주부터는 확인문제 대신 제공되는 실습용 테이블을 활용하여, 배운 내용을 직접 적용하는 실습형 과제로 진행됩니다.

> 이번주는 개강과 함께 새로운 학기가 시작된 만큼, 학기 초 일정에 천천히 적응하시며 부담 없는 한 주 보내시길 바랍니다. 😊

### 🎉 수고하셨습니다.
