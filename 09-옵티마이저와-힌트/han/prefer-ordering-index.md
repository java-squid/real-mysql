- `ORDER BY` 또는 `GROUP BY` 를 [[08-인덱스/han/index|index]] 를 사용해 처리가능한 경우, 쿼리의 실행계획에서 인덱스 가중치를 높이 설정해서 실행되고 있음
	- 가끔 [[optimizer]] 가 실수함 (비효율적인 방법으로)
- [[optimizer]] 가 `ORDER BY` 를 위한 인덱스에 너무 가중치를 부여하지 않도록 하는 옵션

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.3.1.20 인덱스 정렬 선호