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
- type
	- [[mysql-server]] 가 각 테이블의 레코드를 어떤 방식으로 읽었는지 알려줌
		- [[system]]
		- [[const]]
		- [[eq_ref]]
		- [[ref]]
		- [[full_text]]
		- [[ref_or_null]]
		- [[unique_subquery]]
		- [[index_subquery]]
		- [[range]]
		- [[index_merge]]
		- [[10-실행-계획/han/index|index]]
		- [[ALL]]
- possible_keys
	- [[optimizer]] 가 최적의 실행계획을 만들기 위해 후보로 선정했던 접근 방법에서 사용되는 인덱스 목록
	- 사용될법했던 [[08-인덱스/han/index|index]] 목록이다.
	- 무시해도 무방
- key
	- 최종 선택될 실행계획에서 사용하는 [[08-인덱스/han/index|index]]
	- 쿼리 튜닝 시, 해당 칼럼에 의도했던 [[08-인덱스/han/index|index]] 가 표시되는 지 확인하는 것이 **중요**
	- [[ALL]] 과 같은 `type` 이면 해당 칼럼은 `null` 로 표시된다.
- key_len
	- 쿼리를 처리하기 위해 다중 칼럼으로 구성된 [[08-인덱스/han/index|index]] 에서 몇 개의 칼럼 까지 사용했는지 알려주는 칼럼
	- `byte` 로 알려준다.
- ref
	- 참조 조건으로 어떤 값이 제공되었는지 보여둠
	- 상수값 -> `const`
- rows
	- 얼마나 많은 [[record]] 를 읽고 비교해야하는 지 예측한 값
	- 예측한 값이므로 정확하진 않음.
- filtered
	- 필터링되고 남은 [[record]] 의 비율
	- e.g. rows = 233, filtered = 16.03 일때, 인덱스 조건에 일치하는 [[record]] 가 233건이며 (대략), 16.03 % 만 인덱스를 사용하지 못하고, 조건에 일치하는 것
		- 즉 233 * 16.03 = 37건 정도가 인덱스를 사용하지 못하지만 일치했다는 의미
	


---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.2 실행 계획 확인
	- 10.2.1 실행 계획 출력 포맷
	- 10.3.1 id 칼럼
	- 10.3.2 select_type 칼럼
	- 10.3.6 possible_keys 칼럼
	- 10.3.7 key 칼럼
	- 10.3.8 key_len 칼럼
	- 10.3.9 ref 칼럼
	- 10.3.10 row 칼럼
	- 10.3.11 filtered 칼럼
- https://velog.io/@ddongh1122/MySQL-%EC%8B%A4%ED%96%89%EA%B3%84%ED%9A%8D-EXPLAIN