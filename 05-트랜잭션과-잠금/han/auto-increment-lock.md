- `AUTO-INCREMENT` ?
	- 저장되는 각 [[record]] 가 중복되지 않고, 저장된 순서대로 일련번호 값을 가져야함
- 이를 위해서 사용되는 테이블 수준의 [[lock]]
- `UPDATE` , `DELETE` 쿼리에는 사용되지 않음
	- `INSERT`, `REPLACE` 쿼리 문장과 같이 새로운 [[record]] 를 저장하는 쿼리에서만 사용됨
- [[auto-increment-lock]] 은 명시적으로 획득하고 해제하는 방법은 없음

---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.3.1.4 자동 증가 락