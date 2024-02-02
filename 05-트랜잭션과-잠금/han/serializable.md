- 가장 엄격한 격리수준
- 동시 처리 성능도 다른 격리수준에 비해 떨어진다
- 아무런 [[record]] [[lock]] 설정 없이 실행된다
	- `non-locking consistent read`, 잠금이 필요 없는 일관된 읽기
- [[phantom-read]] 발생하지 않음.
	- 해당 트랜잭션 실행 시, [[lock]] 을 획득하기 때문에, 동시에 다른 트랜잭션이 절대 접근 불가

> 그렇지만..

- [[innoDB]] 에서는 [[gap-lock]], [[next-key-lock]] 때문에 [[repeatable-read]] 격리 수준에서도 [[phantom-read]] 가 발생하지 않음.
- 그러므로 굳이 [[serializable]] 사용할 필요 없을듯
 ---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.4.4 SERIALIZABLE