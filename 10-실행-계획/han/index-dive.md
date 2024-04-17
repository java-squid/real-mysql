- [[mysql-server]] 에서 쿼리 실행 계획을 수립 할 때 사용 가능한 [[index]] 들로 부터 조건절에 일치하는 [[record]] 건수를 대략 파악하고, 최종적으로 가장 나은 실행계획을 선택하는데.. 
- 이때 조건절에 일치하는 [[record]] 건수를 예측하기 위해서 [[optimizer]] 는 실제 [[index]] 의 B-tree를 샘플링해서 살펴보는 작업이 [[index-dive]] 임

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.1.2.3 히스토그램과 인덱스