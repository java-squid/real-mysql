- 인덱스 보단 제약조건에 가깝다.
- 테이블이나 인덱스에 같은 값이 2개 이상 저장될 수 없음을 의미
	- `NULL` 도 저장될 순 있지만, `NULL` 은 특정 값이 아니므로 2개 이상 저장될 수 있다.
	- 그러므로 MySQL에서 [[primary-key]] 는 `NULL` 이 허용되지 않는 유니크 속성이 자동으로 부여됨
- [[myisam]], [[memory]] 에서는 [[primary-key]] 가 [[unique-index]] 와 동일하지만
	- [[innoDB]] 에서는 [[primary-key]] 가  [[clustering-key]] 의 역할도 하므로 다름.

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.9 유니크 인덱스