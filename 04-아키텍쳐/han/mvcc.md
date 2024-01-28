- Muti Version Concurrency Control
- 일반적으로 record 레벨의 트랜잭션을 지원하는 DBMS에서 제공하는 기능
- 가장 큰 목적은 잠금을 사용하지 않는 **일관된 읽기** 를 제공하는 데 있음
- [[innoDB]] 는 undo log를 이용해 이 기능을 구현
	- 즉 하나의 record에 대해 2개의 버전이 유지되고, 필요에 따라 (격리 수준) 어느 데이터가 보여지는지 상황에 따라 달라지는 구조

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.2.3 MVCC(Muti Version Concurrency Control)