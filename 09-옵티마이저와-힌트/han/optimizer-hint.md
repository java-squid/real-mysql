- SQL 쿼리에서 [[optimizer]] 에게 쿼리 실행 방식을 제안하는 형식
- 영향 범위에 따라 4개 그룹
	1. 인덱스 : 특정 인덱스의 이름을 사용할 수 있는 옵티마이저 힌트
	2. 테이블 : 특정 테이블의 이름을 사용할 수 있는 옵티마이저 힌트
	3. 쿼리 블록 : 특정 쿼리 블록에 사용할 수 있는 옵티마이저 힌트, 특정 쿼리 블록의 이름을 명시하는 것이 아닌 힌트가 명시된 쿼리 블록에 대해서만 영향을 미치는 방식임
	4. 글로벌 : 전체 쿼리에 대해서 영향을 미치는 힌트

> 글로벌

- `MAX_EXECUTION_TIME`
	- 
- `SET_VAR`


> 쿼리 블록

- `SUB_QUERY`
- `HASH_JOIN`

> 테이블

- `MERGE`
- `NO_MERGE`


> 인덱스

- `INDEX_MERGE`
	- [[index-merge]]
- `NO_INDEX_MERGE
- 모든 인덱스 수준의 힌트는 반드시 테이블명이 선해되어야함

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.4.2 옵티마이저 힌트
	- 9.4.1. 옵티마이저 힌트 종류