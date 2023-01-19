# **제9회 산업통상자원부 공공데이터 활용 BI 공모전**
코트라 데이터활용 빅데이터 분석 경진대회 : 기업 특성에 따른 잠재 파트너 매칭 

<br/>

## 1. 배경 & 목적

- KOTRA의 빅테이터 분석결과를 토대로 사회현안 이슈 해결, 수출금액 예측
- 업무프로세스 전반에 데이터 이용으로 데이터기반 행정혁신 촉진
- 평가지표 : RMSE

<br/>

## 2. 주최/주관 & 참가 대상 & 성과

- 주최: 산업통상자원부
- 주관: 대한무역투자진흥공사
- 후원: 한국전력공사, 한국가스공사, 한국수력원자력, 한국동서발전, 한국중부발전, 한국남동발전, 한국남부발전, 한국서부발전, 한국산업기술평가관리원, 한국산업기술진흥원, 한국지역난방공사, 한전KPS
- 운영: (사)한국지능정보시스템학회
- 참가 대상: 공공데이터 분석 능력을 보유한 개인 또는 팀 (팀당 3명 이내)
- 성과: **우수상 (약 200팀 중)**

<br/>

## 3. 대회 기간

- 제출마감: 2021년 7월 20일
- 1차 서류심사: 2021년 7월 22일~28일
- 2차 현장발표: 2021년 8월 11일

<br/>

## 4. 내용

<img src='https://user-images.githubusercontent.com/75362328/212464638-74181530-3ec6-4280-9a1a-4868450036bb.png' width='100%' height='80%'>

&nbsp;&nbsp;&nbsp;&nbsp; KOTRA 수입 예측분석 데이터를 이용하여 ‘**2019년도에 특정국가가 특정 품목을 한국에서 얼마큼 수입할지 예측**’하고자 한다. 특정국가가 해당 품목을 한국에서 얼마큼 수입할지는 한 가지 요소로 결정되지 않으므로, 데이터 탐색 및 시각화를 통해 선정된 큰 관점인 **'나라', '대륙', '품목', '10대 품목'** 에 따라 분석을 진행하였다. 

&nbsp;&nbsp;&nbsp;&nbsp; 먼저 정보력을 위해서 기본 17년 데이터뿐만 아니라 12년도까지 10가지 종류의 데이터를 권장된 사이트(Comtrade, DataBank)에서 추가적으로 수집하였고, 합쳐진 데이터를 바탕으로 앞서 나온 관점에 따라 피처를 생성하였다. 가장 먼저 원본 데이터를 활용해 기본 피처를 생성하였고, 이후부터 피처 생성 시 다양한 관점을 적용하였다. 

&nbsp;&nbsp;&nbsp;&nbsp; 국가별 구매 특성이 다름에 따라 **국가 관점**으로 피처에 접근하였고, 같은 이유로 국가보다 더 큰 관점인 **대륙**으로 데이터를 바라보고 피처를 생성하였다. 후에는 관점을 바꾸어 **품목 별**로 피처에 접근하였다. 품목별로 수입 특성이 다르기 때문이고, 특히 다양한 품목 중에서도 우리나라 10대 수출품에 해당하는 물품들은 더 자세히 피처를 뽑아내도록 하였다. 

&nbsp;&nbsp;&nbsp;&nbsp; 피처 생성 이후에는 그 안에서 의미 있는 데이터를 선정하고 가공하고자 다양한 전처리 방법을 거쳤다. 회귀분석에 있어서 예측력을 방해할 수 있는 **다중공선성**을 먼저 제거하고, **주성분분석, 이상치 탐색, 스케일링, 로그화**를 거쳐서 분석을 위한 피처를 만들고, 마지막으로 **피처 셀렉션** 과정을 거쳐서 그중에서도 적정한 정도의 피처를 뽑아내도록 하였다. 모델링은 기본적으로 **성능이 잘 나오는 4가지 모델(ExtraTrees, XGB, LGBM, CatBoost)을 이용**하였다. 여러 앙상블 또한 거쳤지만 결과적으로 튜닝된 단일 모델인 LGBM의 성능이 제일 뛰어나 해당 모델을 가지고 최종 서브미션을 구하였다.

<br/>

## 5. 프로젝트 담당 역할

- 외부 데이터 Crawling 및 전처리 & EDA
- LGBM, ExtraTree, DNN 모델 학습 및 최적화
- Stacking, Voting 및 Seed Ensemble 진행
- 품목/국가/대륙 별 사업 파트너 매칭

<br/>

## 6. Process

### ch1. Preparation

- 라이브러리
- 크롤링 데이터 합치기
- 결측치 처리

---

### ch.2 Making Features

- 기본
- 국가별
- 대륙별
- 품목이름별
- 10대 주요물품별

---

### ch.3 Preprocessing

- 다중공선성 제거
- 주성분 분석
- 이상치 탐색
- 스케일링
- 로그화
- 피쳐 설렉션

---

### ch.4 Modeling

- ExtraTrees, XGB, LGBM, CatBoost
- 단일 모델 기본성능 확인
- 단일 모델 튜닝성능 확인 (BayesianOptimization)

---

### ch.5 Ensemble

- 모델별 상관관계
- Averaging
- Stacking
    - VotingRegressor as MetaModel
    - LGBM as MetaModel
- Seed Ensemble

<br/>

## 7. 발표 자료

[KOTRA 최종 발표자료](https://drive.google.com/file/d/1EDkXvKUp2k8tOp5DhhiGhCuS2AW9jyRu/view)  
[KOTRA 분석보고서](https://drive.google.com/file/d/1YaerP9CdZEshwCFb7PUbA5G7QbBqSz0s/view)

<br/>

## 8. 증빙자료

[KOTRA 홈페이지](https://datacontest.kr/board/view/97533073/3458)

<img src='https://user-images.githubusercontent.com/75362328/212464637-8c7fbbeb-cc10-421d-8c59-5c021262a872.jpg' width='60%' height='40%'>
<img src='https://user-images.githubusercontent.com/75362328/212464635-51445fa6-229b-46c6-b569-4faa13593353.jpg' width='60%' height='40%'>
