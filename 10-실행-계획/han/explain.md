- `DESC`, `EXPLAIN` 
- 실행 계획을 확인하는 키워드

> 예시

- 테이블 포맷

```sql
EXPLAIN
SELECT *
FROM employees e
WHERE first_name = 'ABC';
```

- 트리 포맷

```sql
EXPLAIN FORMAT=TREE
SELECT *
FROM employees e
WHERE first_name = 'ABC';
```

- Json 포맷

```sql
EXPLAIN FORMAT=JSON
SELECT *
FROM employees e
WHERE first_name = 'ABC';
```

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.2 실행 계획 확인
	- 10.2.1 실행 계획 출력 포맷