- [[innoDB]] 에서 기본으로 사용하는 격리 수준
- [[non-repeatable-read]] 가 발생하지 않는다.
- [[mvcc]] 를 위한 [[undo-log]] 영역을 기반으로 동일한 [[transaction]] 에서 동일한 조회 쿼리가 나오도록 보장한다
- [[phantom-read]] 가 발생할 수 있다.

![image](https://nesoy.github.io/assets/posts/img/2019-05-08-21-52-08.png)
- Transaction 1에서, 해당 트랜잭션 id와 함께 변경 사항을 [[undo-log]] 에 저장

## [[repeatable-read]] vs [[read-committed]] ?
- [[undo-log]] 영역의 백업된 레코드의 여러버전 가운데, 몇번째 이전 버전까지 찾아들어가냐에 있음
- [[repeatable-read]] 의 경우, [[mvcc]] 를 보장하기 위해, 실행 중인 트랜잭션 가운데 가장 오래된 트랜잭션 번호보다 앞선 [[undo-log]] 영역을 삭제할 수 없음
---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.4.3 REPEATABLE READ