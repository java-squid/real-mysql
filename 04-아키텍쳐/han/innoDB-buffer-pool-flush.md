- flush ?
	- [[dirty-page]] 를 디스크와 동기화 하는 부분

> 종류

- Flush list flush
	- flush-list에서 오래전 에 변경된 데이터 페이지를 순서대로 동기화 하는 작업
- LRU list flush
	- LRU 리스트 끝부분 부터 시작, [[dirty-page]] 디스크와 동기화, [[clean-page]] 는 즉시 free-page로 옮김

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.2.7.4 버퍼 풀 플러시(Buffer Pool Flush)