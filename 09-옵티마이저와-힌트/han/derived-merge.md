- 서브쿼리 사용하는 쿼리 성능 향상 목적
- 서브쿼리를 직접 조인 연산에 사용하여, 중간 테이블 생성과정을 생략하고 성능 향상
	- 기존에는 서브쿼리를 임스 테이블로 저장한 후 조인하는 방식을 사용했음

```sql
SELECT * FROM (
	SELECT * FROM employees WHERE first_name='Matt'
) derived_table
WHERE derived_table.hire_date ='1986-04-03'
```

- `derived_table` 이 임시 테이블
	- 임시 테이블을 생성하는 부분은 결국 레코드를 복사하고 읽는 과정이 있으므로 오버헤드 발생

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.3.1.16 파생 테이블 머지