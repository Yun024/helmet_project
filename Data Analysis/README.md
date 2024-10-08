# 데이터 전처리
- 가해자차종 또는 피해자차종이 이륜차인 교통사고 정보(2015 ~2019년)데이터 이용
- 피해자와 가해자 데이터셋을 따로 분류하여 데이터 분석 진행
- 신체상해정도 "없음"을 제거하고 Oversampling 진행
- 변수명을 일치시킨 후 병합하여 최종데이터셋 완성

-----------------------------------


# 데이터 분석
## 동별 EPDO지도 분석 *[바로가기](https://github.com/Yun024/Helmet_project/blob/main/Data%20Analysis/%EB%8F%99%EB%B3%84EPDO%EC%A7%80%EB%8F%84.R)*

※ EPDO : 사고피해정도(심각도)지수로 2010년부터 최근 몇 년간 발생한 교통사고 인명피해 누적발생건수 평균 상위 지점
- EPDO = (12 * 사망사고건수) + (3 * 부상사고건수) + 물피사고
- 물피사고는 원본 데이터에서 정확히 파악할 수 없기 때문에 제외하여 EPDO값 추출
- 2015 ~ 2019년 대전지역에서 사망과 부상사고 모두 일어난 지역은 약 20여개의 지역이다
- 또한 절반 이상의 지역이 사망사고건이 없는 곳은 부상이 없고, 부상사고건수가 있는 곳은 사망이 없다.
- 따라서 사망사고건이 있는 지역은 부상사고건수를 0으로, 부상사고건수가 있는 곳은 사망사고건수를 0으로 설정

  <img src="https://github.com/user-attachments/assets/ac277445-bbff-4399-a1fb-1394869277e6"  width="600" height="350"/><br>
  
  * 대전지역의 EPDO순위는 둔산동, 갈마동, 월평동, 가양동, 봉명동 순위로 계산된다. 

## Randomforest *[바로가기](https://github.com/Yun024/Helmet_project/blob/main/Data%20Analysis/Randomforest.R)*

※ Randomforest : 훈련을 통해 구성해놓은 다수의 나무들로부터 분류 결과를 취합해서 결론을 얻는 일종의 인기 투표
- 설명변수 : 신체상해정도, 요일, 보호장구, 법규위반, 기상상태, 당사차종별, 노면 상태 / 목표변수 : 부상정도

  <img src="https://github.com/user-attachments/assets/606ac765-19e0-4618-a1f8-876cf97a8144"  width="700" height="350"/><br>

  * 부상정도를 예측하는데 '보호장구착용유무'는 중요하다는 지표를 확인할 수 있음 

## 연관분석 
- 사고발생 시 부상정도와 안전모 착용 여부간의 연관 규칙 찾기
- 향상도 기준 정렬이후 연관 규칙 시각화
- Support(지지도) : X와 Y가 동시에 일어난 횟수 / 전체 일어난 횟수
- Confidence(신뢰도) : X와 Y가 동시에 일어난 횟수 / X가 일어난 횟수
- Lift(향상도) : X를 구매한 사람이 Y를 구매할 확률과 X의 구매와 상관없이 Y를 구매할 확률의 비
  
|향상도|의미|                                       
|-----|-----|
|Lift>1|A와 B가 서로 양의 상관관계|         
|Lift=1|A와 B가 서로 독립적인관계|
|Lift<1|A와 B가 서로 음의 상관관계|

※ 조건 : `최소 지지도: 0.001` , `최소 신뢰도: 0.009` , `최소 부분집합 크기: 3`


### 가해자 연관분석 *[바로가기](https://github.com/Yun024/Helmet_project/blob/main/Data%20Analysis/%EA%B0%80%ED%95%B4%EC%9E%90_%EC%97%B0%EA%B4%80%EB%B6%84%EC%84%9D.R)*

※가해자 안전모 미착용

<img src="https://github.com/user-attachments/assets/efbd7ad9-8857-4294-b967-e9d606960d5c"  width="600" height="300"/><br>
<img src="https://github.com/user-attachments/assets/e755ecee-661a-4858-8d49-5272092f40a2"  width="600" height="200"/><br>

※가해자 안전모 착용

<img src="https://github.com/user-attachments/assets/284a6c0b-88ac-4af0-8f2f-8fe952d291ca"  width="600" height="300"/><br>
<img src="https://github.com/user-attachments/assets/8facf3d7-2db8-405a-b5e9-e1564477734a"  width="600" height="200"/><br>

### 피해자 연관분석 *[바로가기](https://github.com/Yun024/Helmet_project/blob/main/Data%20Analysis/%ED%94%BC%ED%95%B4%EC%9E%90_%EC%97%B0%EA%B4%80%EB%B6%84%EC%84%9D.R)*
※피해자 안전모 미착용

<img src="https://github.com/user-attachments/assets/ab6859c9-2f67-4869-9808-4ccb687ee480"  width="600" height="300"/><br>
<img src="https://github.com/user-attachments/assets/d611a1d3-aac1-4ec6-bd23-7fa5824718ac"  width="600" height="200"/><br>

※피해자 안전모 착용

<img src="https://github.com/user-attachments/assets/855d723b-1916-4c66-b137-e905720baa6d"  width="600" height="300"/><br>
<img src="https://github.com/user-attachments/assets/55322783-f9e9-45fb-8cbd-661f395e25a2"  width="600" height="200"/><br>

## 결론
- 가해자
    * 안전모 미착용: 사망 > 상해 없음 > 부상 신고 => 부상 정도 높음
    * 안전모 착용: 상해 없음 > 부상 신고 > 사망 => 부상 정도 낮음
- 피해자
    * 안전모 미착용: 사망 > 중상 > 경상 => 부상 정도 높음
    * 안전모 착용: 중상 > 경상 > 사망 => 부상 정도 높음
- 안전모 착용이 부상 정도를 낮추며, 미착용시 부상 정도가 심해진다.
- 안전모 착용 여부와 부상 정도간의 연관 관계를 확인했으니 헬멧 분류 알고리즘의 타당성 확보 
