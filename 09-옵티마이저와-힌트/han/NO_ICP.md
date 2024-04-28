- [[index-condition-pushdown]] 은 항상 성능 향상에 도움이 되므로, [[optimizer]] 는 최대한 [[index-condition-pushdown]] 을 사용하는 방향으로 실행계획을 수립함.
- 하지만 [[index-condition-pushdown]] 으로 인해서 여러 실행 계획의 비용 계산이 잘못된다면, 잘못된 실행 계획을 수립할 수도 있음.
	- 이러한 상황을 해결하기 위해 나온 [[optimizer-hint]]

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.4.2.10 NO_ICP