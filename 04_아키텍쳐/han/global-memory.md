- [[mysql-server]] 가 시작되면서 운영체제로 부터 해당 메모리 할당.
- 모든 스레드에 의해서 공유되는 영역

> 예시
- table cache
- InnoDB buffer pool
- InnoDB adaptive hash index
- InnoDB redo log buffer

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.1.3.1 글로벌 메모리 영역