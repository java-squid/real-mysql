- [[semi-join]] 최적화가 사용되지 못할 때 사용하는 최적화 방법
- 2가지 방법이 있음
	- In-to-EXISTS -> `SUBQUERY(INTOEXISTS)`
	- Materialization -> SUBQUERY(MATERIALIZATION)

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.4.2.5 SUBQUERY