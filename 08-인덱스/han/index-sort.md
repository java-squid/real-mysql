- 인덱스는 생성될 떄, 설정한 정렬규칙에 따라서 인덱스의 키 값은 항상 오름차순 이거나 내림차순으로 정렬되어 저장됨.

> MySQL 5.7

- 칼럼 단위로 정렬순서를 혼합(ASC, DESC) 인덱스를 생상헐 수 없었음

> MySQL 8.0

- `CREATE INDEX ix_teamname_userscore ON employees (team_name ASC, user_score DESC)` 와 같이 혼합 인덱스 생성 가능

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.3.6.1 인덱스의 정렬