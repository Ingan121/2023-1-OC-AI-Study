# What I Learned

## fit_transform()과 transform()
* ```fit_transform()```은 학습 데이터에만, ```transform()```은 검증용이나 테스트 데이터에 사용한다.
* fit_transform을 테스트 데이터에 사용하면 모델이 테스트 데이터도 학습하게 되는데, 이러면 테스트 데이터를 이용하여 모델의 성능을 측정하는 의미가 없다.

## 트리모델에 스케일링이 필요없는 이유
* 의사결정나무, 랜덤 포레스트 등의 트리 기반 모델은 변수의 크기에 민감하지 않으므로 스케일링이 필요없다.

## Decision Tree vs Random Forest
* 앙상블(Ensemble): 의견을 통합하거나 여러 가지 결과를 합치는 방식
* 랜덤 포레스트는 하나의 거대한 결정 트리를 만드는 것이 아니라 여러 개의 작은 결정 트리를 만드는 것
* 여러 개의 작은 결정 트리가 예측한 값들 중 가장 많은 값 혹은 평균값을 최종 예측 값으로 정하는 것
* 비유: 한명의 똑똑한 사람보다 100명의 평범한 사람이 더 잘 푸는 원리

[reference]: <> (https://bkshin.tistory.com/entry/%EB%A8%B8%EC%8B%A0%EB%9F%AC%EB%8B%9D-5-%EB%9E%9C%EB%8D%A4-%ED%8F%AC%EB%A0%88%EC%8A%A4%ED%8A%B8Random-Forest%EC%99%80-%EC%95%99%EC%83%81%EB%B8%94Ensemble)