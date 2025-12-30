# [영향 요인 분석] RuleFit 기반 설명가능 AI를 통한 MZ세대 공무원의 이직의도 분석 👉 [PPT](https://github.com/novicedata/Conference/blob/main/RuleFit_MZ_Turnover/source/%5B2025_KSPMA%5D%20%EA%B5%AC%EB%91%90%EB%B0%9C%ED%91%9C_%EC%8B%A0%EC%97%B0%EC%9A%B0.pdf)

## 목차

#### 1️⃣ 개요
#### 2️⃣ 데이터
#### 3️⃣ 분석
#### 4️⃣ 결과
#### 📌 정리 및 배운점
<br>

## 1️⃣ 개요
- **기간 및 인원**: 2025.10 - 2025.11
- **문제 정의**:
  - 2023년 국가공무원인재개발원에서 MZ세대 공무원을 대상으로 집중 연구를 할정도로 MZ세대와 외 세대는 가치관 및 방향성이 다름
  - 이로 인해인지 **실제 공채시험 지원자 수가 줄고 면직률이 증가하고 있음**
  - <img width="851" height="268" alt="image" src="https://github.com/user-attachments/assets/d4a23c0d-eebb-4c07-b3e3-7cd84245561f" />

  - 이에 대한 여러 대응 정책은 주로 개별 요인에 초점을 맞춰왔으며, 연구들 또한 대부분 일부 요인에 한하여 분석
  - **다요인 간의 상관, 상황과 맥락적 효과를 종합적으로 이해하는 방안으로 RuleFit을 적용하여 MZ세대의 이직의도 영향 요인을 분석하여 보자.**
  - <img width="868" height="467" alt="image" src="https://github.com/user-attachments/assets/70a4f5ee-9b50-4352-b8d3-3fde648efded" />
<br>

## 2️⃣ 데이터
- **데이터**
  - 조사 기간: 2024.08.17 - 2024.09.30
  - 조사 대상: 46개 중앙행정기관 및 17개 광역자치단체 소속 공무원
  - 표집 방식: 부처와 시도 단위 층화 표집
  - 분석 대상: 1981년 이후 출생자 MZ세대 4,142명

<img width="841" height="259" alt="image" src="https://github.com/user-attachments/assets/dc0fc411-a548-4ba1-b5c4-8b799e5b3a82" />
<br>

## 3️⃣ 분석
- **1. 독립변수 선정**
  - 분석 일관성과 타당성 확보를 위해 1) 명목형 응답(e.g. 원인 선택형 문항), 2) 특정 기관 종사자 혹은 특정 경험자(e.g. 재택근무 경험자)에게만 제시되는 조건부 문항 제외 모든 문항 포함
 
- **2. 다문항 요인 평균화**
  - 개별 문항이 지니는 측정 오차, 우연적 변동 상쇄 위함
 
- **3. 모델**
  - AutoML 기반 RuleFit 기저 모형 선정(Repeated stratified 10-fold CV)
  - 선정된 RF 파라미터 튜닝
  - RuleFit을 통해 규칙 추출 후 Elbow Method 기준 상위 5개 규칙 해석
<img width="871" height="472" alt="image" src="https://github.com/user-attachments/assets/273c0685-f50e-42bf-8e54-5373656a3fc8" />
<br>

## 4️⃣ 결과
- **Top 5 Rules**
  - <img width="562" height="255" alt="image" src="https://github.com/user-attachments/assets/ab29a7cd-08cc-4115-99f3-11ed6ec7c6f3" />
  - <img width="808" height="252" alt="image" src="https://github.com/user-attachments/assets/0f259372-412e-474e-aa1d-440e32db8270" />
  - RuleFit을 통해 단순 변수 영향이 아닌 이직의도 형성되는 조건 결합을 탐색
    - : 이직의도는 개인의 가치관과 조직환경이 얽혀 나타나는 맥락적 산물
<br>

## 📌 정리 및 배운점
- **seed 값에 따라 규칙 순위가 달라짐**
  - : 큰 틀은 비슷하나, seed에 따라 결과가 달라짐.
  - 여러 seed로 여러번 적용하여 **평균화 하는 방법이나, permutation 방법, 신뢰구간 측정 등 통계적으로 타당한 방법으로 접근하는 방식이 중요**하다라고 느낌
 
- **문항 요인 평균화의 필요성?**
  - : 해석의 편의성과 오차 위험을 대비하여 각 요인의 문항 점수를 평균화 하였으나, 이는 **정보손실을 야기**
  - 전체 문항을 사용하였을 때의 결과도 먼저 확인해보는 **deep한 자세가 필요할 것 같다.**
 
- **ML 파이프라인 생성 능력**
  - : 구조화된 파이프라인은 아니지만, 전체 모델을 비교하여 선정하는 과정에서 **파이프라인의 필요성을 느꼈음**
  - 이를 AutoML을 통해 쉽게 해결할 수 있었지만, **repeated CV를 통해 타당성을 더하는 방안 학습**
