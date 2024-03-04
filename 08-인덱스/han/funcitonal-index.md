- MySQL 8.0부터 함수 기반 인덱스 지원
- 구현 방식은 2가지
	1. 가상 칼럼을 이용
	2. 함수를 이용


> 가상 칼럼을 이용한 인덱스

- `VIRTUAL` 로 생성된 컬럼에 인덱스를 생성할 수 있음

> 함수를 이용한 인덱스

- 테이블 구조를 변경하지 않고, 계산된 결괏값의 검색을 빠르게 만들어줌
- 제대로 활용하려면 반드시 조건절에 함수 기반 인덱스에 명시된 표현식이 그대로 사용되어야함.


---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.6 함수 기반 인덱스
	- 8.6.1 가상 칼럼을 이용한 인덱스
	- 8.6.2 함수를 이용한 인덱스
- https://blogs.oracle.com/mysql/post/functional-indexes-in-mysql