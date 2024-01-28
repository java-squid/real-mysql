- MySQL은 기본적으로 많은 스토리지 엔진을 가지고 있음.
- 그렇지만 기본적으로 제공되는 스토리지 엔진 이외의 부가기능을 제공하는 스토리지 엔진을 사용할 수 있음.
- 이러한 부가기능 스토리지 엔진은 사용자가 직접 개발할 수도 있음
- 위와 같은 아키텍쳐를 가지고 있는 것을 의미

> plugin 종류
- InnoDB storage engine 
- validate password component
- query rewrite plugin
- transparent data encryption plugin

> plugin 단점
- 플러그인끼리 통신 할 수 있음
- 플러그인은 MySQL 서버 변수, 함수를 직접호출 하기 때문에 안전하지 않음.
- 플러그인끼리 상호 의존 관계 설정할 수 없어 초기화가 어려움

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.1.4 플러그인 스토리지 엔진 모델