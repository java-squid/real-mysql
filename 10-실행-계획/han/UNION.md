- [[explain]] 에서 `select_type` 에 나올 수 있는 타입 중 하나
- `UNION` 으로 결합하는 단위 `SELECT` 쿼리 가운데, 첫 번쨰를 제외한 두 번째 이후 단위 `SELECT` 쿼리

> 예시

```sql
EXPLAIN SELECT * FROM (				 //PRIMARY
	(SELECT id FROM employees e1) UNION ALL	 //DERIVED
    (SELECT id FROM employees e2) UNION ALL	 //UNION
    (SELECT id FROM employees e3) ) tb;		 //UNION
```

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.3.2.3