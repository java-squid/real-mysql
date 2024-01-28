- MySQL Enterprise Edition 에서 제공하는 기능
- MySQL Community Edition 에서는 해당 기능을 제공하지 않는다.
- 내부적으로 사용자의 요청을 처리하는 스레드 개수를 줄여서 동시 처리되는 요청이 많다하더라도 [[mysql-server]] 의 CPU가 제한된 개수의 스레드 처리에만 집중하게 해줌.
	- 즉 서버의 자원 소모를 줄이는 목적
- 그렇지만 해당 기능이 실제 서비스에서 눈에 띄는 성능 향상을 보여준 경우는 드물다.
	- 왜?
		- 스레드가 실행에 필요한 CPU 시간을 적절하게 확보하지 못하면, 너무 잦은 context-switching 때문에 결과적으로 비효율이 발생하는듯

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.1.9 스레드 풀