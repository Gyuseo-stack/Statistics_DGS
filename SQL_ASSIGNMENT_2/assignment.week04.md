# SQL_ADVANCED 4주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_4th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=DMNpkj_bZIs&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=13
https://www.youtube.com/watch?v=BUHj-behLyc&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=14
https://www.youtube.com/watch?v=JrXWxku7ZIM&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=15
-->

**교재 실습 예제 파일은 07_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_4th_TIL

### 5장 테이블과 뷰
#### 01. 테이블 만들기
#### 02. 제약조건으로 테이블을 견고하게
#### 03. SQL 가상의 테이블: 뷰 


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | ✅         |
| 4주차 | p.216~271 | ✅         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 테이블 만들기 

<!-- 이번 챕터에서 제시된 실습을 흐름에 맞게 진행한 후, 실습 과정이 보일 수 있도록 인증 사진을 2장 이상 제출해 주세요. -->

<!-- 이 부분을 지우고 인증사진을 제출해주세요.-->


## 2. 제약조건으로 테이블을 견고하게 

<!-- 제약조건에 관해 배우게 된 점을 적어주세요. -->

### 제약 조건
데이터의 무결성을 지키기 위해 제한하는 조건

#### 기본 키
- 중복되지 않고 비어 있지도 않은게 기본 키의 조건, 대표적으로 회원 아이디
- 테이블은 기본 키를 1개만 가질 수 있음
- CREATE TABLE에서 설정하는 법
<img width="539" height="177" alt="image" src="https://github.com/user-attachments/assets/cd39ea30-16ac-4317-978a-f530e6619ad1" />
- ALTER TABLE에서 설정하는 법
<img width="327" height="198" alt="image" src="https://github.com/user-attachments/assets/f66f4d6e-d4fe-4a62-9d94-32ff63aacc28" />

#### 외래 키 제약조건
- 참조 테이블이 참조하는 기준 테이블의 열은 반드시 기본 키나 고유 키로 설정되어 있어야 함
- CREATE TABLE에서 설정하는 법
<img width="347" height="262" alt="image" src="https://github.com/user-attachments/assets/432962ae-6777-4bec-b389-f5d73066ff76" />
- ALTER TABLE에서 설정하는 법
<img width="347" height="214" alt="image" src="https://github.com/user-attachments/assets/4b054a56-e915-4207-82ad-3d5f622d3c1e" />

**기준 테이블의 열이 변경되는 경우**

- **ON UPDATE CASCADE** : 기준 테이블의 열 이름이 변경될 때 참조 테이블의 열 이름이 자동으로 변경되는 것을 지원
- **ON DELETE CASCADE** : 기준 테이블의 데이터가 삭제되면 참조 테이블의 데이터도 삭제되는 기능

#### 기타 제약 조건

**고유 키 제약조건** : 중복되징 않는 유일한 값을 입력해야 하는 조건. 기본 키 제약조건과 거의 비슷하지만 차이점은 고유 키 제약조건은 NULL값을 허용
**체크 제약조건** : 입력되는 데이터를 점검 
EX)평균 키는 반드시 100 이상의 값만 입력되도록 설정
<img width="431" height="114" alt="image" src="https://github.com/user-attachments/assets/626529e3-fedd-4c59-9d3d-d4e00b7abbad" />

**기본값 정의** : 값을 입력하지 않았을 때 자동으로 입력될 값을 미리 지정
<img width="431" height="157" alt="image" src="https://github.com/user-attachments/assets/584113cb-43d4-44e8-bf9a-d3403a67dfc4" />

> **확인문제: 다음 보기 중에서 각 문항이 설명하는 것을 고르세요.**

보기는 아래와 같습니다.
```
CHECK / DEFAULT / PRIMAY KEY / UNIQUE / NOT NULL / FOREIGN KEY
```

```
여기에 답과 그 이유를 적어주세요!
1. 입력되는 데이터가 조건에 맞는지 검사하는 기능: Check, 특정 조건을 만족하는지 검증하는 제약조건
2. 값을 입력하지 않으면 자동으로 들어갈 값: DEFAULT, 값이 없을 때 미리 설정된 기본값을 자동으로 넣어줌
3. 빈 값을 입력하는 것을 허용하지 않음: NOT NULL, NULL을 아예 허용하지 않는 제약조건
```


## 3. 가상의 테이블: 뷰 

<!-- 뷰에 관해 배우게 된 점을 적어주세요. -->
뷰는 데이터베이스 개체 중에 하나임

**단순 뷰**: 하나의 테이블과 연관된 뷰

**복합 뷰**: 2개 이상의 테이블과 연관된 뷰
#### 뷰의 실체는 SELECT문

### 뷰를 만드는 형식
~~~
CREATE VIEW 뷰_이름
AS
   SELECT 문;
~~~
#### 뷰의 장점
- 보안에 도움이 됨
- 복잡한 SQL을 단순하게 만들 수 있음

### 뷰의 실제 작동
| 용어                     | 설명                                                         |
|--------------------------|--------------------------------------------------------------|
| CREATE VIEW              | 뷰를 생성하는 SQL                                            |
| 별칭                     | 뷰에서 사용될 열의 이름을 별칭을 사용해서 테이블과 다르게 지정할 수도 있음 |
| 백틱                     | 뷰를 조회할 때 열 이름에 공백이 있으면 붙여주는 기호          |
| ALTER VIEW               | 뷰를 수정하는 SQL                                            |
| DROP VIEW                | 뷰를 삭제하는 SQL                                            |
| CREATE OR REPLACE VIEW   | 기존에 뷰가 있으면 덮어쓰고, 없으면 새로 생성하는 SQL         |
| DESCRIBE                 | 뷰 또는 테이블의 정보를 조회하는 SQL                         |
| SHOW CREATE VIEW         | 뷰의 소스 코드를 보여주는 SQL                                |
| WITH CHECK OPTION        | 뷰에 설정된 조건만 입력되도록 지정하는 SQL                   |
| CHECK TABLE              | 뷰 또는 테이블의 상태를 확인하는 SQL                         |



> **확인문제: 다음은 뷰의 특징입니다. 거리가 먼 것을 하나 고르세요.**

보기는 아래와 같습니다.
```
1️⃣ 뷰에는 테이블의 모든 열을 포함시켜야 합니다.
2️⃣ 뷰는 복잡한 SQL을 단순하게 만드는 효과가 있습니다.
3️⃣ 뷰는 보안에 도움이 됩니다.
4️⃣ 일부 사용자가 테이블에는 접근하지 못하게 하고, 뷰에만 접근하도록 설정할 수 있습니다.
```

```
1. 뷰에는 테이블의 모든 열을 포함시켜야 합니다.
뷰는 필요한 열만 선택해서 만들 수 있기 때문이다.
```

---

# 2️⃣ 실습과제

## 1. 데이터베이스 구축

아래 코드를 MySQL Workbench에 붙여넣은 후,  
**전체 드래그 → 실행 (Ctrl + Shift + Enter)** 하여 데이터베이스를 생성하세요.

```sql
CREATE DATABASE IF NOT EXISTS week4_db;
USE week4_db;
```

## 2. 실습문제

1. 다음 조건을 만족하는 `users` 테이블을 생성하시오.
```
- user_id는 INT이며 **기본키(Primary Key)**로 설정합니다.
- name은 VARCHAR(20)이며 NULL을 허용하지 않습니다.
- email은 VARCHAR(50)이며 중복을 허용하지 않습니다.
- signup_date는 DATE 타입으로 설정합니다.
- grade는 INT이며 기본값(Default)을 1로 설정합니다.
```

<img width="491" height="381" alt="image" src="https://github.com/user-attachments/assets/82a72599-71b6-46ad-a961-7573349b7184" />

2. 다음 조건을 만족하는 orders 테이블을 생성하시오.
```
- order_id는 INT이며 기본키(Primary Key)로 설정합니다.
- user_id는 INT이며 NULL을 허용하지 않습니다.
- amount는 INT이며 0보다 커야 합니다.
- order_date는 DATE 타입으로 설정합니다.
```
<img width="491" height="291" alt="image" src="https://github.com/user-attachments/assets/2cb26b9e-3bc9-486a-9876-45093ed9d558" />

3. 다음 조건을 만족하여 데이터를 삽입하시오.
```
- users 테이블에 3명 이상의 데이터를 직접 INSERT 하시오.
- orders 테이블에 3건 이상의 데이터를 직접 INSERT 하시오.
```
<img width="604" height="192" alt="image" src="https://github.com/user-attachments/assets/596623d8-d354-4e92-9404-c13eb0316905" />

4. users와 orders 테이블을 활용하여 다음 컬럼을 보여주는 뷰 user_order_view를 생성하시오.
```
- user_id
- name
- amount
```
<img width="604" height="170" alt="image" src="https://github.com/user-attachments/assets/575da571-0a11-467d-9bcb-cf2110b6ac6f" />

5. 생성한 user_order_view를 조회하시오.
<img width="604" height="199" alt="image" src="https://github.com/user-attachments/assets/643280be-add5-4683-800d-e31dc5370405" />


## 3. 제출 방법

1. 각 문제의 실행 결과가 보이도록 화면을 캡처합니다.
2. 테이블 생성 결과, 데이터 삽입 결과, 뷰 생성 및 조회 결과가 모두 보이도록 제출합니다.



### 🎉 수고하셨습니다.
