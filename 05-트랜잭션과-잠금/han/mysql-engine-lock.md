- [[mysql-engine]] 에서 사용하는 [[lock]] 은 크게 2가지
	1. [[storage-engine]] 레벨
	2. [[mysql-engine]] 레벨
- [[mysql-engine]] 레벨의 잠금은 모든 [[storage-engine]] 에 영향
	- 그 반대는 아니다.
- [[table-lock]], [[metadata-lock]], [[named-lock]] 을 제공함
---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.2 MySQL 엔진의 잠금