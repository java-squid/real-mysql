- 정렬 대상 칼럼과, [[primary-key]] 만 [[sort-buffer]] 에 담아서 정렬 수행
- 정렬된 순서대로 다시 [[primary-key]] 를 기반으로 테이블을 읽어서 SELECT 할 칼럼을 가져옴.
- 테이블을 2번 읽음
	- 상당히 불합리..?
- `BLOB`, `TEXT` 타입의 칼럼이 `SELECT` 대상에 포함될 때 [[two-path]] 방식의 정렬이 사용됨

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.2.3.2.2 투 패스 정렬 방식