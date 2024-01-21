 - 격리수준이 `SERIALIZABLE` 이 아닌 경우 SELECT 는 다른 트랜잭션의 변경 작업과 관계없이 항상 잠금을 대기하지 않고 바로 실행
 - [[innoDB]]에서는 [[undo-log]] 를 이용

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.2.4 잠금 없는 일관된 읽기(Non-Locking Consistent Read)