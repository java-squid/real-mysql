### Architecture
![image](https://dev.mysql.com/doc/refman/8.0/en/images/innodb-architecture-8-0.png)

- [[storage-engine]] 중 하나
- Primary key를 기준으로 clustering
	- 즉 PK 순으로 디스크에 저장됨.
- PK 기준으로 range scan은 상당히 빨리 처리됨.
	- 즉 쿼리 실행계획에서 다른 보조 인덱스보다 PK가 비중이 높게 설정되어있음.

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.2 InnoDB 스토리지 엔진 아키텍처