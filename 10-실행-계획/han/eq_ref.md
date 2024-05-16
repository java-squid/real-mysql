- [[explain]] 의 type
- 여러 테비을이 조인되는 쿼리 실행계획에서 사용됨
- 조인에서 처름 읽은 데이블의 칼럼값을, 그 다음 읽어야 할 테이블의 [[primary-key]] 나 [[unique-key]] 칼럼의 검색 조건에 사용할 때 사용되는 타입
	- 두번째 이후에 읽는 테이블의 `type` 칼럼에 [[eq_ref]] 라고 표시됨

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.3.5.1 system