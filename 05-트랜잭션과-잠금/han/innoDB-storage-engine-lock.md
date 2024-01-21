- [[storage-engine]] 내부에서 [[record]] 기반 [[lock]] 방식을 탑재하고 있음.
- 잠금 정보가, 상당히 작은 공간으로 관리
	- 락 에스컬레이션 되는 경우는 없음
	- 락 에스컬레이션?
		- record lock -> page lock or table lock

> 종류
- [[record-lock]]
- [[gap-lock]]
- [[next-key-lock]]
- [[auto-increment-lock]]
---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.3 InnoDB 스토리지 엔진 잠금
	- 5.3.1 InnoDB 스토리지 엔진 잠금