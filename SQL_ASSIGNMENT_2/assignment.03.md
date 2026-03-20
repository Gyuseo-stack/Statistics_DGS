# SQL_ADVANCED 3주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_3rd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=1YmWy-7-OhQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=10
https://www.youtube.com/watch?v=tuQFkzjqEGw&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=11
https://www.youtube.com/watch?v=IOCsreDYqFE&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=12
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_3rd_TIL

### 4장 SQL 고급 문법
#### 01. MySQL의 데이터 형식
#### 02. 두 테이블을 묶는 조인
#### 03. SQL 프로그래밍 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. MySQL의 데이터 형식

<!-- MySQL의 데이터 형식에 관해 배우게 된 점을 적어주세요. -->

<img width="531" height="159" alt="image" src="https://github.com/user-attachments/assets/efff18cb-d04f-412d-b762-74eb783ac66d" />
대용량의 데이터 같은 경우 이름 같은 것은 효율적인 관리를 위해 INT 대신에 TINYINT 쓰는게 좋음 


### 문자형
글자 크기가 고정인 경우 : CHAR (가나다 3글자만 저장해도 10자리 확보 후 앞 3자리 사용한 담 7자리 낭비)

글자 크기가 가변적인 경우 : VARCHAR

### 대량의 데이터 형식
<img width="531" height="133" alt="image" src="https://github.com/user-attachments/assets/f8d80101-ef32-47b1-9f50-e643ca3ae65e" />

### 날짜형
<img width="534" height="108" alt="image" src="https://github.com/user-attachments/assets/ee7f2abc-8593-42e7-9853-8ac0931653f3" />

### 변수의 선언과 값 대입

SET @변수이름 = 변수의 값;

SELECT @변수이름;

-> 이 경우에 MySQL 워크벤치를 재식작할 때까지는 유지되지만, 종료하면 없어짐

PREPARE 과 EXECUTE

**PREPARE은 실행하지 않고 SQL문만 준비해 놓고 EXECUTE에서 실행하는 방식**
<img width="534" height="93" alt="image" src="https://github.com/user-attachments/assets/0b1c2ce7-763b-4825-a1ab-35aaa60f3fb5" />

### 데이터형 변환

**CAST ( 값 AS 데이터_형식 [(길이)])**

**CONVERT ( 값,데이터_형식 [(길이)])**

<img width="541" height="93" alt="image" src="https://github.com/user-attachments/assets/1d11c44c-b5af-4b02-b206-bbf25018a979" />


> **확인문제: 다음 보기에서 데이터 형식의 변환에 사용되는 함수를 2개 고르세요.**

보기는 아래와 같습니다.
```
CONVERT() / DATA() / CAST() / MOVE() / TYPE() / SUM() / AVG() / CURRENT_DATE()
```

```
CONVERT() , CAST()
```


## 2. 두 테이블을 묶는 조인

<!-- 두 테이블을 묶는 조인에 관해 배우게 된 점을 적어주세요. -->

**두 테이블의 조인을 위해서는 테이블이 일대다(one to many) 관계로 연결되어야 함**

상호 조인(cross join) : 의미는 크게 없지만 대용량의 데이터를 만들 때 사용

- 상호 조인에서는 ON 구문을 사용할 수 없음. 
- 상호 조인의 주 용도는 테스트하기 위해 대용량의 데이터를 생성



> **확인문제: 다음 SQL은 회원으로 가입만 하고, 한 번도 구매한 적이 없는 회원의 목록을 조회하는 쿼리입니다. 빈칸에 들어갈 가장 적절한 구문을 고르세요..**

```sql
SELECT DISTINCT M.mem_id, B.prod_name, M.mem_name, M.addr
  FROM member M
    LEFT OUTER JOIN buy B
    ON M.mem_id = B.mem_id
  __________
  ORDER BY M.mem_id;
```
보기는 아래와 같습니다.
```
1. JOIN B.prod_name IS NULL
2. LIMIT B.prod_name IS NULL
3. HAVING B.prod_name IS NULL
4. WHERE B.prod_name IS NULL
```
```
4. WHERE B.prod_name IS NULL , 구매 이력이 없는 회원은 buy 테이블 값이 NULL로 나오기 때문에 WHERE B.prod_name IS NULL로 필터링해야 한다.
```

## 3. SQL 프로그래밍 

<!-- IF문, CASE문, WHILE문, 동적 SQL에 관해 배우게 된 점을 적어주세요. -->


IF 문은 조건식이 참이면 **SQL문장**들을 실행

여기서 SQL문장들이 두 문장 이상이 처리되어야 한다면 **BEGIN ~ END**로 묶어줘야 함

#### IF문 형식
<img width="529" height="84" alt="image" src="https://github.com/user-attachments/assets/012824cd-339c-4f58-a57b-4e667673a41d" />


IF문은 참 아니면 거짓 두 가지만 있기 때문에 2중 분기라는 용어를 사용하고,
**CASE문은 2가지 이상의 여러 가지 경우일 때 처리가 가능한 다중 분기**

#### CASE문 형식
<img width="512" height="216" alt="image" src="https://github.com/user-attachments/assets/40ca66f9-0ae7-429f-bdda-77dc0fe42d45" />

#### WHILE문
조건식이 참인 동안 SQL문장들 계속 반복
<img width="508" height="70" alt="image" src="https://github.com/user-attachments/assets/3e45909b-6827-4a23-8d5d-5724308e2031" />

- ITERATE[레이블] : 저장한 레이블로 가서 계속 진행
- LEAVE[레이블] : 지정한 레이블을 빠져 나감(WHILE문 종료)


> **확인문제: 다음은 CASE 문의 형식입니다. 빈칸에 들어갈 가장 적절한 명령어를 보기에서 고르세요..**

```sql
CASE
    (1) 조건 THEN
        SQL문장들1
    ELSE
        SQL문장들4
END (2);
```

보기는 아래와 같습니다.
```
WHEN / THEN / CURRENT / DATE / TIME / IF / END IF / CASE
```

```
여기에 답을 적어주세요!
(1) WHEN
(2) CASE
```


---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + shift + Enter)** 하여 데이터베이스를 구축하세요.

```sql
-- 1. 데이터베이스 생성
CREATE DATABASE IF NOT EXISTS week3_db;

-- 2. 사용할 데이터베이스 선택
USE week3_db;

-- 3. 기존 테이블 삭제 (초기화용)
DROP TABLE IF EXISTS orders;
DROP TABLE IF EXISTS customers;

-- 4. 테이블 생성 (조인 실습용)
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(20),
    signup_date_str VARCHAR(8) 
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,           
    order_date_str VARCHAR(8), 
    amount_str VARCHAR(10)     
);

-- 5. 데이터 삽입
INSERT INTO customers VALUES
(1, '진아', '20240218'),
(2, '혜인', '20230302'),
(3, '규서', '20220315'),
(4, '규영', '20210401'),
(5, '철원', '20230909'),
(6, '예운', '20240201'),
(7, '민서', '20220320'),
(8, '광윤', '20240105'); -- 주문 없는 고객(외부 조인용)

INSERT INTO orders VALUES
(101, 1, '20240220', '12000'),
(102, 1, '20240303', '30000'),
(103, 2, '20240111', '15000'),
(104, 3, '20221201', '9000'),
(105, 5, '20231111', '20000'),
(106, 7, '20220707', '5000'),
(107, 99, '20240210', '7000'); -- 고객 테이블에 없는 customer_id (외부 조인용)
```

## 2. 실습 문제

다음 SQL 문을 작성하고 실행 결과를 확인 후 인증 사진을 아래에 업로드하세요.

1. **데이터 형식 변환**
   - orders 테이블의 `order_date_str`을 DATE 형식으로 변환하여 조회하시오.
   (힌트: STR_TO_DATE 사용)

2. **데이터 형식 변환**
   - orders 테이블의 `amount_str`을 숫자형으로 변환하여 조회하시오.

3. **내부 조인 (INNER JOIN)**
   - customers와 orders를 customer_id 기준으로 내부 조인하여
     고객 이름(name)과 주문 번호(order_id)를 함께 조회하시오.

4. **외부 조인 (LEFT JOIN)**
   - customers를 기준으로 LEFT JOIN을 수행하여,
     주문이 없는 고객도 함께 조회하시오.

5. **스토어드 프로시저 (IF문 사용)**
   - 입력받은 금액이 10000 이상이면 '고액 주문',
     그렇지 않으면 '일반 주문'을 출력하는
     프로시저를 생성하시오.
   - 생성 후 CALL로 실행 결과를 확인하시오.


<!-- 이 부분을 지우고 인증사진을 제출해주세요.-->
1  <img width="676" height="315" alt="image" src="https://github.com/user-attachments/assets/f7c65296-a36e-40e8-96c5-12169b06f952" />

2 <img width="676" height="315" alt="image" src="https://github.com/user-attachments/assets/899c99bd-a624-47a4-903a-9b769993732a" />

3 <img width="676" height="315" alt="image" src="https://github.com/user-attachments/assets/0aa493f3-fa2c-4072-b40b-12673fe67f7b" />

4 <img width="676" height="315" alt="image" src="https://github.com/user-attachments/assets/1cc8efa2-f99e-44ed-958e-32c53b5616b8" />

5 <img width="676" height="462" alt="image" src="https://github.com/user-attachments/assets/e1d07cfa-a023-4b04-9944-687b1d288ba6" />


### 🎉 수고하셨습니다.
