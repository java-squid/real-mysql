- 다른 테이블과 실제 조인을 수행하지 않고, 단지 다른 테이블에서 조건에 일치하는 레코드가 있는지 없는지 체크하는 형태의 조인
- MySQL 5.7 에서는 아래 쿼리가 어떻게 실행 될까?

```sql
SELECT *
FROM employees e
WHERE e.emp_no IN (SELECT de.emp_no FROM dept_emp de WHERE de.from_date='1995-01-01')
```

- `employees` 테이블을 풀 스캔하면서, 한 건 한건 서브쿼리의 조건과 일치하는 지 비교한다.
	- 즉 서브쿼리가 먼저 실행되고, 이를 기반으로 `employees` 에 일치하는 레코드만 검색하지 않는다.

> 세미 조인 최적화

- [[table-pull-out]]
- [[first-match]]
- [[loose-scan]]
- [[materialization]]
- [[duplicated-weed-out]]

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.3.1.9 세미조인