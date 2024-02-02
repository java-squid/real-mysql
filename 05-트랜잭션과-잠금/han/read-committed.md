- [[dirty-read]] 발생하지 않음
- [[commit]] 이 완료된 데이터만 다른 [[transaction]] 에서 조회할 수 있다
- 하지만 [[non-repeatable-read]] 문제는 발생가능
---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.4.2 READ COMMITTED