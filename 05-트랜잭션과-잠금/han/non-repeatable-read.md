- 하나의 [[transaction]] 에서 동일한 쿼리를 사용했을 때, 결과가 달라지는 현상
- 부정합의 문제

![image](https://vladmihalcea.com/wp-content/uploads/2018/06/NonRepeatableRead-1024x646.png)

- Bob의 첫번째 select 쿼리에서는 title = 'Transactions'
- Alice가 [[commit]] 한 이후에도 여전히 위 [[transaction]] 진행 중이던 Bob이 다시 select 했을 때, title = 'ACID'

> 언제 문제가 발생할까?

- 금전적인 처리가 필요한 경우

---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.4.2 READ COMMITTED
- https://vladmihalcea.com/non-repeatable-read/