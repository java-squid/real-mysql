- [[optimizer]] 에게 특정 테이블의 [[index]] 를 사용하도록 권장
- 대부분의 경우 [[optimizer]] 는 위 힌트가 주어지면, 해당 인덱스를 사용하지만 항상 그런것은 아니다.

> 인지해야 할것

- 인덱스의 사용법이나 좋은 실행 계획이 어떤 것인지 판단하기 힘든 상황이라면 힌트를 사용해 강제로 [[optimizer]] 의 실행 계획에 영향을 미치는 것은 피하는 것이 좋다
- 최적의 실행 계획은 데이터의 성격에 따라서 시시각각 변하므로, 지금 좋은 계획이었다고 하더라도, 내일은 달라질 수 있기 때문에

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.4.1.2 USE INDEX / FORCE INDEX / IGNORE INDEX