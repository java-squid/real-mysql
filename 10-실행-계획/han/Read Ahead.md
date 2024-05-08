- [[index-dive]] 에서 사용되는 기술
- 쿼리 실행 과정에서 미래에 필요할 것으로 예상되는 데이터를 미리 읽어서 버퍼 풀에 저장하는 기술
- [[full-table-scan]] 이나 [[index-full-scan]]과 같은 대량의 I/O 를 유발하는 작업을 위해, 한꺼번에 많은 페이지를 읽어들이는 기술
- I/O 작업을 줄이고, 쿼리 성능 향상에 기여

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.3.5.12 ALL