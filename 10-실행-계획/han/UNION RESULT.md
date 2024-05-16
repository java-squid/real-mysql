- [[explain]] 에서 `select_type` 에 나올 수 있는 타입 중 하나
- `UNION` 결과를 담아두는 테이블의 의미
- 실제 쿼리에서 단위 쿼리가 아니기 때문에 별도의 `id` 값이 부여되지 않는다.

> 예시

```sql
EXPLAIN
SELECT id FROM salaries WHERE salary > 100000		//PRIMARY
UNION DISTINCT
SELECT id FROM dept_emp WHERE from_date > '2001-01-01';	//UNION
// id = NULL, select_type = UNION RESULT 인 ROW 추가됨.
```

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.3.2.5