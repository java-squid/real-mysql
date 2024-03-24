- 특정 칼럼의 유니크한 값만 조회하기 위해서 사용됨
- 집합함수 `min()`, `max()` `count()` 와 같이 사용하는 경우에 만약 실행 계획에서 인덱스 사용하지 못하면 항상 임시 테이블이 필요하다는 점이 있음

```sql
SELECT DISTINCH first_name, last_name FROM employees;
```
- `first_name` 이 유니크한 것들만 가져오는 것이 아닌 `first_name`, `last_name` 조합 전체가 유니크한 레코드를 가져오는 것
	- 즉 `SELECT` 절에 사용된 [[distinct]] 는 조회되는 모든 칼럼에 영향을 미친다.

> 집합함수와 사용되었을 때는 또 다르다.

- 집합 함수 내에서 사용된 [[distinct]] 는 그 집합 함수의 인자로 전달된 칼럼값이 유니크한 것들을 가져옴

```sql
SELECT COUNT(DISTINCT s.salary) FROM employees e, salaries s
WHERE e.emp_no = s.emp_no;
```
- 즉 `salary` 가 유니크한 것들만.
	- `salary` 칼럼 값만 저장하기 위한 임시테이블을 만들어서 사용됨
	- 상당히 느려질 수 있음

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.2.5 DISTINCT 처리
	- 9.2.5.2 집합 함수와 함께 사용된 DISTINCT