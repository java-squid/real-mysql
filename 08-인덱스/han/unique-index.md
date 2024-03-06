- 인덱스 보단 제약조건에 가깝다.
- 테이블이나 인덱스에 같은 값이 2개 이상 저장될 수 없음을 의미
	- `NULL` 도 저장될 순 있지만, `NULL` 은 특정 값이 아니므로 2개 이상 저장될 수 있다.
	- 그러므로 MySQL에서 [[primary-key]] 는 `NULL` 이 허용되지 않는 유니크 속성이 자동으로 부여됨
- [[myisam]], [[memory]] 에서는 [[primary-key]] 가 [[unique-index]] 와 동일하지만
	- [[innoDB]] 에서는 [[primary-key]] 가  [[clustering-key]] 의 역할도 하므로 다름.


> 인덱스 읽기

- 유니크 인덱스는 빠르지 않다.
- [[secondary-index]] 가 [[unique-index]] 보다 느린것 맞는듯.
	-  [[secondary-index]] 는 중복을 허용하여 읽어야할 레코드가 많아서 느린 것

> 인덱스 쓰기

- [[unique-index]] 는 키 값을 쓸 때, 중복된 값이 있는지 없는지 체크하는 과정이 필요.
- 그러므로 [[secondary-index]] 의 쓰기보다 느림
- 또한 mysql 에서는 쓰기 할 때 쓰기잠금, 중복된 값 체크를 위해 읽기 잠금 사용
	- [[dead-lock]] 빈번히 발생
- 반드시 중복체크 해야하므로, [[innoDB-change-buffer]] 를 사용하지 못함.

> 주의사항

- 성능이 좋아질 것으로 생각하고, 생성하는 것은 별로 좋지 않음

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.9 유니크 인덱스
	- 8.9.1.1 유니크 인덱스 읽기
	- 8.9.1.2 유니크 인덱스 쓰기