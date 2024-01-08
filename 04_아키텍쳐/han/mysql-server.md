![image](https://velog.velcdn.com/images%2Ffortice%2Fpost%2Fd869f1e2-246c-49cf-9315-a98b2156b17e%2Fimage.png)
- [[mysql-engine]] + [[storage-engine]]
- **스레드 기반** 동작
	- 스레드는 [[foreground-thread]], [[background-thread]] 로 구분됨

> 참고
- 스레드 모델은 MySQL 에디션에 따라 사용 모델이 다른듯.
	- community -> Foreground, background thread model
	- enterprise -> thread pool

## Memory allocation
![image](https://velog.velcdn.com/images/ddangle/post/f8246847-7f05-46b3-bb73-c3da331a8d1c/image.png)
- [[global-memory]] + [[session-memory]]

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.1 MySQL 엔진 아키텍처
	- 4.1.2 MySQL 스레딩 구조
	- 4.1.3 메모리 할당 및 사용구조