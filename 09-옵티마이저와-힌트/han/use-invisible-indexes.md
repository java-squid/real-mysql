- `use_invisible_indexes` 옵션을 사용하면 `INVISIBLE` 로 설정된 인덱스라 하더라도 옵티마이저가 사용하게 제어할 수 있음

- MySQL 8.0 에는 인덱스를 삭제하지 않고, 해당 인덱스를 사용하지 못하게 제어하는 기능이 있음.
	- 즉 인덱스 가용 상태를 변경할 수 있음
		- invisible -> 사용하지 못하게
		- visible -> 사용할 수 있도록

---

## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.3.1.17 인비저블 인덱스