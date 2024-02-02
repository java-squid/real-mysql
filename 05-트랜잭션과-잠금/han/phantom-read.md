- 다른 [[transaction]] 에서 수행한 변경 작업에 의해, 레코드가 보였다가 안보이는 현상
- `select .. for update` 를 사용하는 경우에도 발생
	- [[undo-log]] 에 잠금을 걸 수 없기 때문에, 현재 [[record]] 값을 가져오게 된다

![image](https://vladmihalcea.com/wp-content/uploads/2018/06/PhantomRead-1024x672.png)
- Bob이 최초 select 쿼리 했을 경우, 레코드 3개 (id=1,2,3)
- Alice가 Insert - commit 한 후에, Bob이 여전히 그 트랜잭션에서 select 쿼리를 하면 (id =1,2,3,4)
- 즉 total [[record]] 가 달라지는 현상을 의미


---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.4.3 REPEATABLE READ
- https://vladmihalcea.com/phantom-read/