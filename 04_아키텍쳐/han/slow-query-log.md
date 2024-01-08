![image](https://i0.wp.com/mysql.wisborg.dk/wp-content/uploads/2019/01/log_slow_extra.png?fit=582%2C220&ssl=1)

- `Time` : 쿼리가 종료된 시점
	- 쿼리가 언제 시작되었는지 아려면 `Time` - `Query_time` 해야함
- `User@Host` : 쿼리를 실행한 사용자 계정
- `Query_time` : 쿼리를 실행하는데 걸린 전체 시간
- `Lock_time` 
	- MySQL 엔진 레벨에서 관장하는 테이블 잠금에 대한 대기 시간
	- 0이 아니라고 해서, 무조건 잠금대기가 있었다고 판단하기 어려움
		- 왜?
			- 실제 쿼리가 실행되는 데 필요한 잠금 체크와 같은 코드 실행 부분까지 모두 포함하기 떄문
			- 그러므로 아주 작은값이라면 무시해도 무방
- `Row_examined` : 이 쿼리가 처리되기 위해 몇 건의 레코드에 접근했는지를 의미
- `Row_sent` : 실제 몇 건의 처리 결과를 클라이언트에게 보냈는지
	- 만약 `Row_examined` 의 레코드 건수는 높지만 `Row_sent` 의 건수가 상당히 적다면 튜닝할만하다.
	- 좀 더 적은 수의 레코드에 접근하도록 (`Row_examined` 를 줄이도록..)


--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.43 슬로우 쿼리 로그
- https://mysql.wisborg.dk/2019/01/31/more-statistics-for-slow-queries-log_slow_extra/