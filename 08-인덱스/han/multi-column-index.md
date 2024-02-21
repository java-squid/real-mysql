- 두 개 이사의 칼럼으로 구성된 인덱스를 의미 
- 복합 칼럼 인덱스라고도 부름
- Concatenated Index
- 다중 컬럼 인덱스에서는 인덱스 내에서 각 칼럼의 위치가 중요하다.
	- 왜?
	- dep_no, emp_no 로 다중 칼럼이 있다면, dep_no를 기준으로 emp_no가 정렬되어있음
	- 즉 두번째 칼럼은 첫번째 칼럼에 의존해서 정렬됨

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.3.5 다중 칼럼 인덱스