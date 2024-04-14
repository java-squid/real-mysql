- [[optimizer-hint]] 인 동시에 조인 키워드
- `SELECT`, `UPDATE`, `DELETE` 쿼리에서 여러 개의 테이블이 조인되는 경우, 조인 순서를 고정하는 역할을 함
- 일반적으로 조인을 하기 위한 칼럼들의 인덱스 여부로 조인의 순서가 결정되며, 조인 칼럼의 인덱스에 아무런 문제가 없는 경우는 [[record]] 수가 적은 테이블을 드라이빙으로 선택한다
	- '[[record]] 수가 적은' 이라는 의미는 테이블 전체의 [[record]] 건수를 의미하진 않는다. 
		- 인덱스를 사용할 수 있는 `WHERE` 조건까지 포함해서 그 조건을 만족하는 [[record]] 건수를 의미한다.
	- 그런데 [[STRAIGHT_JOIN]] 을 이용할 경우, 조인의 순서를 결정할 수 있다.
- 이와 비슷한 역할을 하는 [[optimizer-hint]] 는 다음과 같다.
	- `JOIN_FIXED_ORDER`
	- `JOIN_ORDER`
	- `JOIN_PREFIX`
	- `JOIN_SUFFIX`

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.4.1.1 STRAIGHT_JOIN