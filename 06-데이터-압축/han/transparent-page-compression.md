- 페이지 압축
	- [[mysql-server]] 가 디스크에 저장하는 시점에 데이터 페이지가 압축되어 저장
	- 반대로 [[mysql-server]] 가 디스크에서 데이터 페이지를 읽어 올때는 압축이 해제
	- 즉 디스크에 들어가는 페이지는 압축된 페이지임
- [[mysql-server]] 페이지 압축의 문제
	- [[punch-hole]] 기능이 운영체제 뿐만 아니라, 하드웨어 자체에서도 해당 기능을 지원해야 사용가능하다는 점
	- 그래서 많이 사용되진 않는다

---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 6.1 페이지 압축