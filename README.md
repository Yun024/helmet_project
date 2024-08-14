# 안전모 관련 스마트 시티 프로젝트 

## 분석배경 관련 기사  
- 1인 가구 600만 돌파, 4년만에 15% 증가 _ 동아닷컴 2020.06.24
- 1인 가구를 겨냥한 배송 시장의 '비대면화' _ 중앙일보 2020.06.03
- 5초에 한번씩 콜, 코로나19 이후 배달 주문 폭주 _ 조선비즈 2020.04.29
- '언택트 소비'의 그늘, 오토바이 사고 사망자 14% 증가 _ 머니투데이 2020.08.12
- 오토바이 사고, 안전모 미착용 시 사망위험 증가 _ 매일안전신문 2020.02.24


## 연구 목표
- 연관 분석과 이미지 딥러닝을 이용한 안전모 착용 서비스 활성화 


## 프로젝트 기간
- 2020년 6월 22일 ~ 9월 18일
- 7인 1조 팀프로젝트 
  + 팀원 명 : 김민종, 김재민, 심병창, 윤여준, 이원경, 이호원, 정은비  
  
## 사용 기술 : [모듈 및 패키지]
`프로그램` : colab, jupyter lab, python, R, Excel

`EDA` 
- R : [ dplyr, reshape2, ggplot2, scales]

`Data Analysis`
- R : [ dplyr, arules, arulesViz, RColorBrewer, caret, randomForest, ggplot2, writexl, readxl, ggmap]

`Video Analysis`
- Python : [ colab, BeautifulSoup, selenium, glob, cv2, matplotlib, tensorflow, deep_sort, YoloV3]


## 데이터 설명 
|번호|활용 데이터|형식|행|데이터 소스|
|:------:|------|------|------|------|
|1|2017 ~ 2047 장래가구추계|csv|31|통계청|
|2|2020년 5월 온라인 쇼핑 동향|hwp|14|통계청|
|3|시도 시군구별 가해운전자 차량용도별 교통사고_2019|csv|4,267|도로교통공단|
|4|가해운전자 차종별 월별 교통사고(2010 ~ 2019)|csv|30|도로교통공단|
|5|교통사고건수(2015 ~ 2019)|csv|5|TAAS_교통사고분석시스템|
|6|WHO-COVID-19-global-data|csv|39,865|WHO|
|7|가해자차종 또는 피해자차종이 이륜차인 교통사고 정보(2015 ~ 2019년)|csv|160,133|도로교통공단|
|8|Helmet data|jpg|400|open image Dataset|
|8|Human hair data|jpg|400|open image Dataset|
|10|직접 촬영한 영상 데이터|mp4|-|직접촬영|



## Contents
### 1. EDA : *[바로가기](https://github.com/Yun024/helmet_project/tree/main/EDA)*
- 코로나19 동향 그래프
- 가구원수 별 현황 및 예측 그래프
- 분기별 온라인 쇼핑 합계액 그래프
- 상품군 별 거래액 변화율 그래프
- 시간에 따른 차종 별 사고 변화율 그래프
- 차종 별 사고발생시 사망자율 그래프

### 2. Data Analysis : *[바로가기](https://github.com/Yun024/helmet_project/tree/main/Data%20Analysis)*
- 데이터 전처리 방식
- 동별 EPDO지도 분석
- Randomforest
- 피해자와 가해자로 분류한 헬멧착용여부와 부상정도의 연관분석

### 3. Video Analysis : *[바로가기](https://github.com/Yun024/helmet_project/tree/main/Video%20Analysis)*
- Web crawling
- YOLO 알고리즘 및 Parameter
- Tracking

## 서비스 제안 
`이륜차 제조업`, `배달 대행 업체`, `보험사`
- 안전모 미착용 시 경고음 발생 서비스
  - 승용차 안전벨트 미착용 시 울리는 경고음 기능 벤치마킹
- 배달대행업체의 배달 수락시 모바일 어플을 이용한 안전모 인증 팝업 생성 서비스
- 보험사의 이륜자동차 보험에 대한 손해율을 안전모 착용여부를 확인하여 감소시킬 수 있음
  - 안전모 착용 확 => 부상 정도 감소 => 보험금 감소 => 보험료 할인

## 기대효과 
- 효과적인 단속환경을 위한 안전모 인식 기술
- 안전한 퍼스널 모빌리티 운행 환경
- 차세대 교통기술을 구현할 수 있는 미래 도로 개발
- 도로, 교통 측면에서 이용자를 보호할 수 있는 안전한 기술 

## 한계점 및 보완점
- 민머리의 경우 헬멧착용했다는 판정이 나올 수 있음
- 영상 품질이 낮을 경우 제대로 안전모 착용여부를 파악할 수 없음
- 더 많은 이미지 데이터셋을 통해 높은 정확성이 나오도록 모델을 훈련시킬 필요가 있음
- 정확성을 높일 수 있도록 더 많은 변수를 사용해야함