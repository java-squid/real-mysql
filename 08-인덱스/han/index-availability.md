- B-tree 인덱스의 특징은 왼쪽 값에 기준해서 오른쪽 값이 정렬되어 있다는 것
- 하나의 컬럼으로 검색해도 값의 왼쪽 부분이 없으면 [[index-range-scan]] 을 사용할 수 없음

> 예시
- 케이스 A: index(first_name)
- 케이스 B: index(dept_no, emp_no)

`SELECT * FROM employees WHERE first_name LIKE %mer`
- [[index-range-scan]] 사용할 수 없음
- 조건절의 `%mer` 에는 왼쪽 부분이 고정되지 않았기 때문

`SELECT * FROM employees WHERE emp_no>=10144`
- 인덱스 효율적으로 사용할 수 없음
- 케이스 B는 다중칼럼 인덱스
	- dep_no 로 정렬한 뒤에, emp_no로 정렬되었기 떄문에


---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.3.7.2 인덱스의 가용성