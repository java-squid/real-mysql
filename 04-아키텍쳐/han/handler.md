- [[mysql-engine]] 이 [[storage-engine]] 을 조정하기 위해 사용하는 것
	- 즉 [[mysql-engine]] 이 각 스토리지 엔진에게 데이터를 읽어오거나, 저장하도록 명령하려면 반드시 [[handler]] 를 통해야 한다.
- [[mysql-server]] 의 가장 밑단
- [[execution-engine]] 의 요청에 따라, 데이터를 디스크에 저장하고 디스크로부터 읽어오는 역할

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.1.6.5 핸들러(스토리지 엔진)