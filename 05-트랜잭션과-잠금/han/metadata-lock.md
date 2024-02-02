- 데이터베이스 객체 (e.g. [[table]] or [[view]]) 의 이름이나 구조를 변경할 때 획득하는 [[lock]]
- 명시적으로 획득, 해제할 수 없음
	- 즉 자동으로 획득한다.
	- `RENAME TABLE table_a TO table_b` 와 같은 경우, 자동으로..


---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.2.4 테이블 락