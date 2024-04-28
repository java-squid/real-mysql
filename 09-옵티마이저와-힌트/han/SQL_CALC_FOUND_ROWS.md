- [[SQL_CALC_FOUND_ROWS]] 힌트가 포함된 쿼리의 경우 `LIMIT` 에 만족하는 수 만큼의 레코드를 찾았더하더라도 끝까지 검색을 수행한다
- `LIMIT` 를 사용하는 경우, 조건을 만족하는 레코드가 `LIMIT` 에 명시된 수보다 많다고 하더라도 `LIMIT` 에 명시된 수만큼 만족하는 레코드를 찾으면 즉시 검색 작업을 멈춘다.
- 사용하지 않는 것을 추천
	- 왜?
	- 인덱스 활용을 못함. 다량의 I/O 발생할 수 있음.

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.4.1.3 SQL_CALC_FOUND_ROWS