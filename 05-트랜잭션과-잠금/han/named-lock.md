- `GET_LOCK()` 함수를 이용하여, 임의의 문자열에 대한 잠금 설정하는 방식
- 즉 단순하게 사용자가 지정한 문자열에 대해 락을 획득하고, 반납하는 잡금 방식
- 여러 클라이언트가 상호 동기화를 처리해야할 때, [[named-lock]] 을 이용한다.

---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.2.3 네임드락