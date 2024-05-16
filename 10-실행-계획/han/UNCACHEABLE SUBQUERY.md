- [[explain]] 에서 `select_type` 에 나올 수 있는 타입 중 하나
- 서브쿼리는 내부 캐시 공간에 결과를 담아둠.
- [[UNCACHEABLE SUBQUERY]] 는 서브쿼리가 캐싱되지 않았음을 의미.
	- 즉 쿼리 실행 시, 서브쿼리는 매번 다시 계산되어야함을 의미한다

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.3.2.10