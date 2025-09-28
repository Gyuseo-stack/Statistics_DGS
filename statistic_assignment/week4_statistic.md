# 통계학 4주차 정규과제

📌통계학 정규과제는 매주 정해진 분량의 『*데이터 분석가가 반드시 알아야 할 모든 것*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **Statistics_4th_TIL**에 나열된 분량을 읽고 `학습 목표`에 맞게 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 추가자료와 교재를 다시 참고하여 보완하는 것이 좋습니다.

4주차는 `2부-데이터 분석 준비하기`를 읽고 새롭게 배운 내용을 정리해주시면 됩니다


## Statistics_4th_TIL

### 2부. 데이터 분석 준비하기

### 10. 데이터 탐색과 시각화

<!-- 10. 데이터 탐색과 시각화에서 10.1 탐색적 데이터 분석부터 10.4 비교 시각화 파트까지 진행해주시면 됩니다. -->



**(수행 인증샷은 필수입니다.)** 

<!-- 이번주는 확인 문제가 없고, 교재의 실습에 있는 부분을 따라해주시면 됩니다. 데이터셋과 참고자료는 노션의 정규과제란에 있는 깃허브를 활용해주시면 됩니다. -->



## Study ScheduleStudy Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | 1부 p.2~46    | ✅         |
| 2주차 | 1부 p.47~81   | ✅         |
| 3주차 | 2부 p.82~120  | ✅         |
| 4주차 | 2부 p.121~167 | ✅         |
| 5주차 | 2부 p.168~202 | 🍽️         |
| 6주차 | 3부 p.203~250 | 🍽️         |
| 7주차 | 3부 p.251~299 | 🍽️         |

<!-- 여기까진 그대로 둬 주세요-->



---

# 1️⃣ 개념 정리 

## 10. 데이터 탐색과 시각화

```
✅ 학습 목표 :
* EDA의 목적을 설명할 수 있다.
* 주어진 데이터셋에서 이상치, 누락값, 분포 등을 식별하고 EDA 결과를 바탕으로 데이터셋의 특징을 해석할 수 있다.
* 공분산과 상관계수를 활용하여 두 변수 간의 관계를 해석할 수 있다.
* 적절한 시각화 기법을 선택하여 데이터의 특성을 효과적으로 전달할 수 있다.
```

<!-- 새롭게 배운 내용을 자유롭게 정리해주세요.-->

## 1. EDA의 목적
- **ML 모델의 성능**은 알고리즘보다 데이터를 올바르게 파악하고 **효과적으로 가공**하는 데서 더 큰 영향을 받음.
- **EDA와 데이터 시각화는 구별**해야 함:
  - EDA 단계에서 시각화를 활용해 데이터를 **효율적으로 파악**.
  - 데이터 시각화의 **궁극적 목적**은 분석 결과를 **명확히 커뮤니케이션**하는 것.
- **EDA 주요 목표**:
  - 데이터의 형태와 척도가 분석 목적에 알맞은지 확인.
  - 데이터의 **평균, 분산, 분포, 패턴** 등 특성 파악.
  - **결측값, 이상치** 확인 및 보완.
  - **변수 간 관계성** 파악 및 분석 방향 점검·보정.
  - 극단적 해석이나 **자의적 추론을 지양**.

---

## 2. 데이터 탐색 및 기초 통계
- `info()` : 숫자형 칼럼이 문자형으로 잘못 지정되었는지, 반대의 경우가 없는지 확인.
- `describe()` : 평균, 표준편차, 최대·최소값 등 기초 통계값을 한 번에 확인.
- `skew()`, `kurtosis()` : **왜도(skewness)**와 **첨도(kurtosis)**를 통해 분포 모양 파악.
- `seaborn.displot()` : 각 칼럼의 분포를 시각화하여 데이터 형태 파악.

---

## 3. 공분산과 상관분석
### 3.1 개념
- **공분산**: 두 변수의 변동이 얼마나 함께 움직이는지.
  - 양의 값: X1 ↑ → X2 ↑
  - 음의 값: X1 ↑ → X2 ↓
  - **단점**: 변수의 단위·척도에 따라 값의 크기가 달라져 **상관성 정도를 직접 비교하기 어려움**.

- **피어슨 상관계수**:
  - 공분산을 각 변수의 표준편차로 나눈 값.
  - -1 ~ +1 범위:
    - 0.4 이상: 어느 정도 상관.
    - 0.7 이상: 매우 높은 상관.
  - **주의**:
    - 산점도의 **기울기와 상관계수는 무관**.
    - 상관계수가 높다는 것은 예측 정확도(설명력)가 높음을 의미.
    - 상관계수 제곱 = **결정계수(R²)** → 독립변수가 종속변수 변동을 설명하는 정도.

### 3.2 분석 시 유의사항
- 상관관계가 0이더라도 **비선형 관계**가 존재할 수 있음.
- 이상치(outlier)에 민감 → 반드시 **산점도 시각화** 병행.
- `seaborn.clustermap()` : 히트맵 기반으로 변수 간 상관계수 한눈에 파악 가능.

---

## 4. 시계열 시각화
- **연속형 시간 데이터**:
  - 선그래프(Line plot)로 추세 파악.
  - 데이터가 많거나 변동이 심하면 **추세선(이동평균)** 삽입해 안정적 패턴 표현.
- **분절형 시간 데이터** (월/분기 단위 등):
  - **누적 막대 그래프**: 한 시점에 2개 이상의 세부 항목이 있을 때 유용.

---

## 5. 비교 시각화
- **히트맵(Heatmap)**:
  - 그룹과 비교 요소가 많을 때 사용.
  - 각 그룹의 높은/낮은 값과 요소 간 관계를 효과적으로 파악 가능.
- **방사형 차트(Radar Chart)**:
  - 다변수를 **평행 좌표**로 배치해 집단별 차이 수준을 시각화.
  - 값의 **정규화 필요**.
  - 집단의 **전체적 경향성**을 한눈에 표현.

---


<br>
<br>

---

# 2️⃣ 확인 과제

> **교재에 있는 실습 파트를 직접 따라 해보세요. 실습을 완료한 뒤, 결과화면(캡처 또는 코드 결과)을 첨부하여 인증해 주세요.단순 이론 암기보다, 직접 손으로 따라해보면서 실습해 보는 것이 가장 확실한 학습 방법입니다.**
>
> > **인증 예시 : 통계 프로그램 결과, 시각화 이미지 캡처 등**

### 10.1.2 탐색적 데이터 분석
<img width="872" height="303" alt="image" src="https://github.com/user-attachments/assets/dd118de1-d705-44d7-8fbc-64e1e83227f7" />

<img width="614" height="577" alt="image" src="https://github.com/user-attachments/assets/f6a43cda-e445-4b55-8368-04a54460b31c" />

<img width="899" height="353" alt="image" src="https://github.com/user-attachments/assets/0a2bef6e-50ea-4d1e-90ff-76060230c17f" />

<img width="411" height="353" alt="image" src="https://github.com/user-attachments/assets/45881375-f0b8-40ee-9ddf-0d552b7086ed" />

<img width="411" height="431" alt="image" src="https://github.com/user-attachments/assets/df640c1d-ab43-41be-bdb0-8162161410b7" />

<img width="777" height="510" alt="image" src="https://github.com/user-attachments/assets/a65d6604-46fd-4e2f-ab7c-3fe61b16ea26" />


### 10.2.3 공분산과 상관성 분석

<img width="654" height="627" alt="image" src="https://github.com/user-attachments/assets/9824c54f-4b96-4bff-a043-ddd74ee8f2dc" />

<img width="654" height="511" alt="image" src="https://github.com/user-attachments/assets/4d4b58c6-54f9-46bb-862c-b76546fdef4e" />

<img width="654" height="612" alt="image" src="https://github.com/user-attachments/assets/d32890f8-1552-4145-ad4e-aaac543c9767" />

<img width="654" height="495" alt="image" src="https://github.com/user-attachments/assets/8a55f913-0008-4906-b8cf-a4b45176ff49" />

### 10.3.1 시간 시각화

<img width="654" height="429" alt="image" src="https://github.com/user-attachments/assets/78b3b150-4738-475c-92ae-64092561add3" />

<img width="654" height="342" alt="image" src="https://github.com/user-attachments/assets/0ffa3625-04bb-4f5e-badc-53c5a5852e75" />

<img width="654" height="443" alt="image" src="https://github.com/user-attachments/assets/b3ebdf6f-65b5-4aa9-b1a9-9bb736c4d854" />

### 10.4.1 비교 시각화

<img width="654" height="581" alt="image" src="https://github.com/user-attachments/assets/6424446e-07d4-415c-a6ac-f25085a7ae9c" />

<img width="654" height="547" alt="image" src="https://github.com/user-attachments/assets/cf34d037-2a9a-4de4-9d54-9c495dbfb78c" />

<img width="654" height="567" alt="image" src="https://github.com/user-attachments/assets/5d575567-1bf5-49a0-9856-3118f766296d" />

<img width="654" height="597" alt="image" src="https://github.com/user-attachments/assets/f2070a5a-c2af-462e-b677-84b509014092" />

<img width="654" height="402" alt="image" src="https://github.com/user-attachments/assets/6fa4a25b-d0a1-4626-8344-e3fd04209210" />

~~~
인증 이미지가 없으면 과제 수행으로 인정되지 않습니다.
~~~





### 🎉 수고하셨습니다.
