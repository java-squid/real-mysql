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

> 분석

![image](https://github.com/java-squid/real-mysql/assets/22140570/b96db4c3-4ef2-4fea-8d45-c6b8cf1cf082)

- id
	- 단위 `SELECT` 쿼리별 부여되는 식별자 값
	- 해당 컬럼이 테이블의 접근 순서를 의미하지 않는다.
- select_type
	- 쿼리가 어떤 타입의 쿼리인지 
		- [[SIMPLE]]
		- [[PRIMARY]]
		- [[UNION]]
		- [[DEPENDENT UNION]]
		- [[UNION RESULT]]
		- [[SUBQUERY]]
		- [[DEPENDENT SUBQUERY]]
		- [[DERIVED]]
		- [[DEPENDENT DERIVED]]
		- [[UNCACHEABLE SUBQUERY]]
		- [[UNCACHEABLE UNION]]
		- [[MATERIALIZED]]


---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.2 실행 계획 확인
	- 10.2.1 실행 계획 출력 포맷
	- 10.3.1 id 칼럼
	- 10.3.2 select_type 칼럼
- https://velog.io/@ddongh1122/MySQL-%EC%8B%A4%ED%96%89%EA%B3%84%ED%9A%8D-EXPLAIN