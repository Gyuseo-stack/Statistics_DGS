# Tableau 3주차 정규과제

📌Tableau 정규과제는 매주 정해진 **유튜브 강의를 통해 태블로 이론 및 기능을 학습한 후, 실습 문제를 풀어보며 이해도를 높이는 학습 방식**입니다. 

이번주는 아래의 **Tableau_3rd_TIL**에 명시된 유튜브 강의를 먼저 수강해주세요. 학습 중에는 주요 개념을 스스로 정리하고, 이해가 어려운 부분은 강의 자료나 추가 자료를 참고해 보완하세요. 과제 작성이 끝난 이후에는 **Github에 TIL과 실습 인증 결과를 업로드 후, 과제 시트에 제출해주세요.**



**(수행 인증샷은 필수입니다.)** 

> 태블로를 활용하는 과제인 경우, 따로 캡쳐도구를 사용하여 이미지를 첨가해주세요.



## Tableau_3rd_TIL

### 20. 파이와 도넛차트

### 21. 워드와 버블차트

### 22. 이중축과 결합축

### 23. 분산형 차트

### 24. 히스토그램

### 25. 박스 플롯

### 26. 영역차트

### 27. 간트차트

### 28. 필터

### 29. 그룹



<br>

## 주차별 학습 (Study Schedule)

| 주차  | 공부 범위          | 완료 여부 |
| ----- | ------------------ | --------- |
| 1주차 | **강의 1 ~ 9강**   | ✅         |
| 2주차 | **강의 10 ~ 19강** | ✅         |
| 3주차 | **강의 20 ~ 29강** | ✅         |
| 4주차 | **강의 30 ~ 39강** | 🍽️         |
| 5주차 | **강의 40 ~ 49강** | 🍽️         |
| 6주차 | **강의 50 ~ 59강** | 🍽️         |
| 7주차 | **강의 60 ~ 69강** | 🍽️         |

<!-- 여기까진 그대로 둬 주세요-->



---

# 학습 내용 정리

## 20강: 파이와 도넛차트
<!-- 파이와 도넛차트에 관해 배우게 된 점을 적어주세요 -->
### 파이차트
1. 필드 클릭 후 표현 방식에서 파이차트 클릭
2. 상단 툴바에 전체 보기로 변경
3. 내림차순 정렬
4. 이중 축 활용 (열 선반에 빈 공간 더블 클릭,0 입력)
5. 시트에서 마우스 오른쪽 클릭 후 서식 클릭 상단 격자무늬에서 선 없음 선택

> **🧞‍♀️ 도넛차트를 생성하는 법을 포함해주세요.**


## 21강: 워드와 버블차트

<!-- 워드와 버블차트에 관해 배우게 된 점을 적어주세요 -->
버블 차트 -> 수치적 데이터를 원의 크기로 표현
### 워드 클라우드
- 문서 내에서 등장하는 키워드가 얼마나 자주 등장하는지를 텍스트 크기로 표현
- 히트맵으로 표현된 차트를 워드 클라우드로 변경하기 위해 마크에서 텍스트로 변경

## 22강: 이중축과 결합축

<!-- 이중축과 결합축에 관해 배우게 된 점을 적어주세요 -->

### 이중 축
- 하나의 뷰 안에서 축을 이중 축으로 사용
- 합치고자 하는 필드의 수익 필드에 마우스 우클릭 혹은 역삼각형 버튼을 통해 이중 축 선택
- 이중 축에서는 독립적으로 마크를 수정할 수 있음

### 결합 축
- 필드 드래그 후 왼쪽 축에 끌고 갈 시 결합 축 생성

## 23강: 분산형 차트

<!-- 분산형 차트에 관해 배우게 된 점을 적어주세요 -->
분산형 차트는 파라미터 간의 상관관계를 파악하는데 유용
- 분석 탭에서 모델의 추세선을 드롭할 시 필드 간의 추세선이 그려짐
#### 추세선 이중축 활용
<img width="676" height="364" alt="image" src="https://github.com/user-attachments/assets/a187f05e-ff19-466b-a28a-7c6d8fb19d86" />
<img width="676" height="364" alt="image" src="https://github.com/user-attachments/assets/a762db89-ee97-482a-957e-fbe6d70b9793" />
<img width="676" height="290" alt="image" src="https://github.com/user-attachments/assets/9d74822d-5ffe-4a07-842e-d9e7a96a64a2" />


```js
강의 영상과 달리, 우리 파일에는 '제조 업체' 필드가 없습니다. 필요한 경우, 계산된 필드를 이용해 'SPLIT([제품 이름], ' ', 1)'를 '제조 업체'로 정의하시고 세부 정보에 놓아주세요.
```



## 24강: 히스토그램

<!-- 히스토그램에 관해 배우게 된 점을 적어주세요 -->

히스토스램은 분포형태를 표시하는 차트, 불연속형이 아닌 연속형 측정값을 범위 혹은 구간 차원으로 그룹화한다는 점에서 막대그래프와 차원이 있음
구간 차원은 일정한 크기의 포맷을 만들어 값을 담아 표현하기 위한 도구

### 구간 차원 만들기
필드 우클릭 -> 만들기 -> 구간차원 클릭

**자체 생성ㄷ괸 구간 차원의 값 크기를 조정하고 싶을 경우**
<img width="676" height="290" alt="image" src="https://github.com/user-attachments/assets/9e08f510-9511-4a7e-85b3-9b90e4b268b3" />
편집 클릭 후 값 입력으로 전환
<img width="676" height="290" alt="image" src="https://github.com/user-attachments/assets/3ccbaa9a-3455-40cd-aabc-99a0d1d189b3" />



## 25강: 박스플롯

<!-- 박스플롯에 관해 배우게 된 점을 적어주세요 -->

<img width="681" height="346" alt="image" src="https://github.com/user-attachments/assets/6d87e4a6-3559-440b-b9b7-39d331e43d05" />
### 실습 화면
<img width="731" height="618" alt="image" src="https://github.com/user-attachments/assets/30141260-5009-4cd9-9e3f-90552e9e9b28" />


## 26강: 영역차트

<!-- 영역차트에 관해 배우게 된 점을 적어주세요 -->
영역차트는 라인과 축 사이의 공간이 색상으로 채워진 라인 차트
**주로 연속형 데이터의 누계를 표현하는데 사용됨**

#### 실습 화면
<img width="923" height="570" alt="image" src="https://github.com/user-attachments/assets/236d071d-f3a0-4866-ab11-a4b81bc8db1a" />


## 27강: 간트차트

<!-- 간트차트에 관해 배우게 된 점을 적어주세요 -->

간트차트는 주로 시간 경과에 따른 기간을 시각화하는데 사용

1. 분석 -> 계산된 필드 만들기 후 배송 기간 필드 생성
<img width="518" height="298" alt="image" src="https://github.com/user-attachments/assets/faa51e65-ca8d-4ac6-9cc4-e21e558191b1" />
2. 마크에서 월별 합계 배송기간을 평균으로 변경, 위 자동을 간트 차트로 변경
<img width="161" height="229" alt="image" src="https://github.com/user-attachments/assets/2e4712f0-b534-43ae-bdf6-040602993f46" />
3. 고객 이름으로 필터에 드래그
<img width="1058" height="592" alt="image" src="https://github.com/user-attachments/assets/82f6cd3d-0cd8-4c8a-a90a-ca403f9d2bbb" />


## 28강: 필터

<!-- 필터에 관해 배우게 된 점을 적어주세요 -->

**Tableau의 필터링은 추출, 데이터원본, 컨텍스트, 차원, 측정값, 필터 순으로 동작**

### 추출
이전 강의 참고(라이브와의 차이)
### 데이터 원본 필터
작업을 위한 데이터 중 일부만 워크 스페이스에 불러올 때 사용 우측에 필터를 통해 추가 가능
<img width="635" height="336" alt="image" src="https://github.com/user-attachments/assets/d2cc252b-dae5-4b20-85d5-64be3375c52d" />
### 컨텍스트 필터
- 필터 중 상위 필터
- 다른 필터가 컨텍스트 필터에 적용
- 필터 상세 페이지에서 상위 클릭 후 설정 가능
<img width="471" height="591" alt="image" src="https://github.com/user-attachments/assets/92b69517-125d-4eaa-a76d-aaf49844f4f2" />
- 원하는 필터 내 필드 우클릭 후 컨텍스트 추가 클릭

### 차원 필터
ex) 와일드 카드에서 값 일치에 배송 입력 후 끝 문자 클릭 시 끝 문자에 배송인 필드만 가져옴
<img width="471" height="591" alt="image" src="https://github.com/user-attachments/assets/ac1553ac-1fe7-41f7-a215-c497ca52a180" />


## 29강: 그룹

<!-- 그룹에 관해 배우게 된 점을 적어주세요 -->

데이터를 표시하는 방법에는 그룹,계층,집합이 있음

그룹을 이용해 수동으로 필드에 있는 항목들을 묶을 수 있으며 기존 데이터 원본에 없는 사용자 지정 그룹 필드를 만들 수 있음

### 그룹화 하는 법 
1. 특정 부분을 드래그하여 우클릭 후 그룹화 가능
<img width="302" height="522" alt="image" src="https://github.com/user-attachments/assets/31bb8d33-179b-4599-b3d4-02d3af659ed6" />
2. 필드 우클릭 -> 만들기 -> 그룹
   <img width="442" height="541" alt="image" src="https://github.com/user-attachments/assets/97fa1f38-1fe4-44a7-8a94-be7d9158254d" />


# 확인문제

## 문제 1.

```js
푸앙이는 superstore 데이터셋에서 '주문' 테이블을 보고 있습니다.
1) 국가/지역 - 시/도- 도시 의 계층을 생성했습니다. 계층 이름은 '위치'로 설정하겠습니다.
2) 날짜의 데이터 타입을 '날짜'로 바꾸었습니다.

코로나 시기의 도시별 매출 top10을 확인하고자
1) 배송 날짜가 코로나시기인 2021년, 2022년에 해당하는 데이터를 필터링했고
2) 위치 계층을 행으로 설정해 펼쳐두었습니다.
이때, 매출의 합계가 TOP 10인 도시들만을 보았습니다.
```

![alt text](https://raw.githubusercontent.com/DArt-B-Official/07_Tableau_Template/main/images/Week2-1.png)



```
겉보기에는 전체 10개로, 잘 나온 결과처럼 보입니다. 그러나 푸앙이는 치명적인 실수를 저질렀습니다.
오늘 배운 '컨텍스트 필터'의 내용을 고려하여 올바른 풀이 및 결과를 구해주세요.
```

배송 날짜 필터(2021~2022년)와 TOP 10 필터가 모두 일반 필터로 설정되어 있기 때문에, TOP 10 필터는 전체 기간 기준으로 설정되어 있는 상태입니다.
배송 날짜 필터(2021~2022년)를 컨텍스트 필터로 설정 후, 필터 선반의 배송 날짜 필터를 우클릭 후 "컨텍스트에 추가" 를 선택하면, 해당 필터가 가장 먼저 실행되어 2021~2022년 데이터만의 임시 데이터셋을 만들고, TOP 10 필터는 그 임시 데이터셋을 기준으로 작동합니다. 이렇게 해야 코로나 시기(2021~2022년) 매출 기준 진짜 TOP 10 도시를 올바르게 구할 수 있습니다.
<!-- DArt-B superstore가 아닌 개인 superstore 파일을 사용했다면 값이 다르게 표시될 수 있습니다.-->



## 문제 2.

```js
규서는 관심이 있는 제품사들이 있습니다. '제품 이름' 필드에서 '삼성'으로 시작하는 제품들을 'Samsung group'으로, 'Apple'으로 시작하는 제품들을 'Apple group'으로, 'Canon'으로 시작하는 제품들을 'Canon group'으로, 'HP'로 시작하는 제품들을 'HP group', 'Logitech'으로 시작하는 제품들을 'Logitech group'으로 그룹화해서 보려고 합니다. 나머지는 기타로 설정해주세요. 이 그룹화를 명명하는 필드는 'Product Name Group'으로 설정해주세요.

(이때, 드래그보다는 멤버 찾기 > 시작 문자 설정하여 모두 찾아 한번에 그룹화해 확인해보세요.)
```

![alt text](https://raw.githubusercontent.com/DArt-B-Official/07_Tableau_Template/main/images/Week2-2.png)

<img width="457" height="460" alt="image" src="https://github.com/user-attachments/assets/23605ba0-9b97-48ba-99bd-621538d8426b" />

```js
해당 그룹별로 어떤 국가/지역이 주문을 많이 차지하는지를 보고자 합니다. 매출액보다는 주문량을 보고 싶으므로, 주문Id의 카운트로 계산하겠습니다.

기타를 제외하고 지정한 5개의 그룹 하위 목들만을 이용해 아래와 같이 지역별 누적 막대그래프를 그려봐주세요.
```

<img width="983" height="473" alt="image" src="https://github.com/user-attachments/assets/a96f3200-37e3-47eb-9606-0e8ad3a3ede2" />


![alt text](https://raw.githubusercontent.com/DArt-B-Official/07_Tableau_Template/main/images/Week2-3.png)

<br>

<br>

### 🎉 수고하셨습니다.
