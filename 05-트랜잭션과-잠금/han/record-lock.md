- [[record]] 자체만을 잠그는 것 (기본적으로..)
- [[innoDB-storage-engine-lock]] 에서는 **인덱스의 [[record]] 를 잠근다**
	- 다른 DBMS와의 차이

> p170.. InnoDB의 잠금은 레코드를 잠그는 것이 아닌, 인덱스를 잠근다

```sql
UPDATE employees SET hire_date = NOW() WHERE first_name='Georgi' AND last_name='Klassen';
```
- 위 SQL은 1건의 [[record]] 업데이트 하는 쿼리
- 이 1건 업데이트를 위해 몇 개의 레코드에 락이 걸릴까?
	- `first_name` 에 인덱스가 걸려있다는 조건
- 인덱스를 사용할 수 있는 조건
	- `first_name='Georgi'` .. 253건 (예시) 이 모두 잠긴다.
	- 만약 적절한 인덱스가 없다면, 각 클라이언트 간 [[concurrency]] 는 상당히 떨어질 것
	- 그러면 다른 클라이언트에서 기다리는 상황이 발생
- 만약에 하나도 인덱스가 없다면 ?
	- `full scan` 해야하므로, 해당 테이블의 모든 [[record]] 가 잠긴다

---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.3.1.1 레코드 락
	- 5.3.2 인덱스와 잠금
	- 5.3.3 레코드 수준의 잠금 확인 및 해제 
		- *레코드 수준에서 잠금과 해제가 어떤 방식으로 일어나는지 다시 보면 좋을듯*