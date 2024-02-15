![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbcLKRw%2FbtrX1OtXSpe%2F1ZDUlSdkNQKs1aESaagGMk%2Fimg.png)

- [[mysql-server]] 와 디스크 사이의 데이터를 읽고 쓰는 지점에서만 암호화, 복호화가 수행됨
- 즉 [[mysql-server]] ([[innoDB]]) 의 I/O 레이어에서만 데이터의 암호화 및 복호화 과정이 실행됨
- 하지만 사용자는 이러한 여부를 신경쓸 필요가 없음
	- 이러한 방식의 암호화를  [[TDE]] 라 함

---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 7.1 MySQL 서버의 데이터 암호화