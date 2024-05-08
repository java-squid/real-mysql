- 레코드를 대표하는 칼럼의 값으로 만들어진 [[08-인덱스/han/index|index]]
- 식별자
- `NULL` 허용 하지 않고, 중복을 허용하지 않음

## mysql primary-key

- [[innoDB]] 에서 테이블의 각 레코드를 고유하게 식별하는 데 사용하는 칼럼
- 특징
	- 유일하게 식별
	- 중복값 허용하지 않아 데이터 무결성 보장
	- [[clustering-index]] 역할 (데이터를 정렬, 저장)
	- 자동 증가 속성

---
## Reference
 - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.2 인덱스란?