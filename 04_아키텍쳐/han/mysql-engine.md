![image](https://docs.oracle.com/cd/E17952_01/mysql-8.0-en/images/mysql-architecture.png)

- 클라이언트로부터의 접속 및 쿼리 요청 처리하는 역할
- 커넥션 핸들러, SQL 파서(Parser), 전처리기, 옵티마이저(Optimizer)
	- 즉 SQL 문장을 분석, 최적화

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.1.1.1 MySQL 엔진
- https://docs.oracle.com/cd/E17952_01/mysql-8.0-en/pluggable-storage-overview.html