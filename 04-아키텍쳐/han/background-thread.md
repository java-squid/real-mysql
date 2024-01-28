- `insert buffer` 를 병합
- 로그를 디스크에 기록
- InnoDB 버퍼 풀의 데이터를 디스크에 기록
- 데이터를 버퍼로 읽어옴.
- 잠금이나 데드락을 모니터링

> 중요
- log thread
- write thread
	- 버퍼의 데이터를 디스크로 내려 쓰기하는 스레드
- 쓰기 작업은 버퍼링해서 일괄 처리하는 기능이 탑재
	- 반면 읽기 작업은 절대 지연될 수 없음

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.1.2.2 백그라운드 스레드