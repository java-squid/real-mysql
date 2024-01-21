- 외래 키
- 해당 설정이 되어이으면, 변경 시에는 반드시 부모, 자식 테이블에 데이터가 있는지 체크하는 작업이 필요
	- 그러므로 잠금이 여러 테이블로 전파 -> 데드락 발생

---
## Reference
- https://dev.mysql.com/doc/refman/8.0/en/create-table-foreign-keys.html