- `local memory area`
- 클라이언트 스레드가 쿼리를 처리하는 데 사용하는 메모리 영역
- 각 스레드별로 독립적으로 할당. 
	- 즉 절대로 서로 공유되지 않는다.

> 예시
- sort buffer
- join buffer
- binary log cache
- network buffer

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.1.3.2 로컬 메모리 영역