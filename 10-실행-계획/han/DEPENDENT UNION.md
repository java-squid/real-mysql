- [[explain]] 에서 `select_type` 에 나올 수 있는 타입 중 하나
- `DEPENDENT` ?
	- `UNION` 이나 `UNION ALL` 로 결합된 단위 쿼리가 외부 쿼리에 의해 영향 받는 것을 의미

> 예시

```sql
EXPLAIN 
SELECT * 							//PRIMARY
FROM employees e1 WHERE e1.id IN (
	SELECT e2.id FROM employees e2 WHERE e2.name='MATT'	//DEPENDENT SUBQUERY
	UNION
	SELECT e3.id FROM employees e3 WHERE e3.name='MATT'     //DEPENDENT UNION
);
```

- [[optimizer]] 는 `IN` 이하 서브쿼리를 먼저 처리하지 않고, 외부 `employees` 먼저 읽은 다음 서브 쿼리를 실행
- 이때 `employees` 테이블의 칼럼 값이 서브쿼리에 영향 주므로 -> `DEPENDENT`


---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.3.2.4