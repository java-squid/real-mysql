- `client thread`
- 최소한 [[mysql-server]] 에 접속한 클라이언트 수 만큼 존재한다.
- 클라이언트가 요청한 쿼리 문장을 처리한다.
- 주로 데이터를 데이터 버퍼, 캐시로 부터 가져오며, 버퍼나 캐시에 없는 경우에 직접 디스크 데이터나 인덱스 파일로부터 데이터를 읽어온다.

> 참고
- [[storage-engine]] 에 따라 하는 역할이 다르다.
- `innodb` 의 경우, `foreground`, `background` 역할이 나눠져 있지만, `myisam` 의 경우 `foreground` 가 `background` 가 하는 일까지 처리하는듯

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.1.2.1 포그라운드 스레드 (클라이언트 스레드)