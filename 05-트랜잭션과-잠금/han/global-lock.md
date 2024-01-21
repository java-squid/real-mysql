---

---
- `FLUSH TABLES WITH READ LOCK` 으로 획득 가능.
- [[DDL]], [[DML]] 문장의 경우, [[global-lock]] 이 해제될 때 까지 대기 상태로 된다.
- MySQL에서 제공하는 [[lock]]  가운데, 가장 범위가 크다.
	- [[mysql-server]] 전체에 영향을 미친다.
	- 즉 작업하는 테이블이나, 데이터베이스가 달라도 영향이 간다

> backup-lock ?
- 가벼운 [[global-lock]]
- [[xtrabackup]], [[enterprise-backup]] 의 안정적인 실행을 위해 도입된 락
- [[DDL]] 명령 실행 시, 뒤 툴들을 통한 복제가 잠시 중단되도록 돕는 역할을 한다.

---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.2.1 어댑티브 해시 인덱스