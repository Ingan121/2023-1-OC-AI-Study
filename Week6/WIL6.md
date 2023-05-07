# What I Learned

## 회귀와 분류
* 회귀: 종속변수가 숫자일 때 사용
* 분류: 종속변수가 숫자가 아닐 때 사용

## Classification Matrics
```
                                예상값
    +------------+--------------------+---------------------+
    |            |      Positive      |       Negative      |
    |------------|--------------------|---------------------|
 실 |  Positive  | True Positive (TP) | False Negative (FN) |
 제 |------------|--------------------|---------------------|
 값 |  Negative  | False Positive (FP)|  True Negative (TN) |
    +------------+--------------------+---------------------+
```
[comment]: <> (ㄴ 손으로 만든 노가다 표)

* 정확도 (Accuracy): (TP + TN) / (TP + FN + FP + TN)
  * 전체중에 정답을 맞춘 비율
* 정밀도 (Precision): TP / (TP + FP)   |   재현율 (Recall): TP / (TP + FN)
  * 둘다 1에 가까울수록 좋음
* F1 Score: 2 * Precision * Recall / (Precision + Recall)
  * Precision과 Recall의 조화평균
  * 이게 좋아야 성능이 좋음
* AOC - ROC Curve (Area Under the Curve - Receiver Operating Characteristic)
  * y축을 TPR(Recall), x축을 FPR(TN / (TN + FP))

[ref1](https://statinknu.tistory.com/35)

## Regression Metrics
* MSE (Mean Squared Error): 평균 오차 제곱합
  * 실제값과 오차의 차를 제곱한 뒤 평균을 한 값
* RMSE (Root Mean Squared Error): MSE에 루트를 씌운 값
  * 단순 오차 제곱합의 오차율 값이 큰 것을 보정해줌
  * 대표적인 회귀 척도로 많이 사용
* RMSLE (Root Mean Squared Log Error): RMSE의 각 인자에 로그화를 취해준 값
  * 연속적인 값의 분포가 치우쳐져 있거나 정규 분포를 따르지 않고 불균형한 모형일 때 사용
  * RMSE보다 비대칭성에 강함
* MAE (Mean Absolute Error): 실제값과 예측값의 차이의 절대값 합이 평균
* R^2 (R2, R-Squared): 총제곱합(SST)에 대한 회귀제곱합(SSR), 결정계수라고도 함
  * 1에 가까울수록 설명력이 높음

[ref2](https://shinminyong.tistory.com/32)

## 마무리 숙제
* RandomForest: DecisionTree를 bagging 앙상블
* GBM (Gradient Boosting Machine): 경사하강법에 기반하여 boosting하는 기법
  * 순차적으로 분류기들을 학습하기 때문에 학습시간이 상대적으로 오래걸림
* XGBoost (eXtra Gradient Boosting): DecisionTree를 boosting 앙상블, GBM 기반
  * boosting: 한개의 예측 모델에 대한 error를 줄이는 방식의 앙상블 기법
  * 병렬 처리가 가능하여 GBM보다 빠름
  * 데이터 수가 적을 경우 추천 (과적합 방지)
* LightGBM: GBM모델 기반
  * 한층이 끝나야 다음층 가지 만드는 일반적인 DecisionTree와는 달리 층에 대한 제약 없이 잎에서 가지를 치고 또 가지를 치는 방식
  * 적은 메모리 사용, 빠른 모델 생성, 높은 성능
  * 과적합에 취약
* CatBoost: LightGBM의 과적합 문제 방지 위해 만들어진 모델

* 코드 및 비교 결과는 ipynb 맨밑에 넣어놨다.
* 돌려보고 실행 시간과 정확도를 비교해본 결과 LightGBM이 가장 좋은 것 같다.

[ref3](https://jhkim0759.tistory.com/12)
[ref4](https://techblog-history-younghunjo1.tistory.com/102)
[ref5](https://techblog-history-younghunjo1.tistory.com/102)