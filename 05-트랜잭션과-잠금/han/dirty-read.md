- 어떤 [[transaction]]에서 처리한 작업이 완료되지 않았든데도,  다른 [[transaction]]에서 볼 수 있는 현상

> 예시
![image](https://vladmihalcea.com/wp-content/uploads/2018/05/DirtyRead-1024x560.png)

- Alice의 트랜잭션이 끝나지 않았는데도,
- Bob은 post.title = 'ACID' 인 상태 (uncommitted) 가 조회가능하다.

---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.4.1 READ UNCOMMITTED
- https://vladmihalcea.com/dirty-read/