- 운영체제, 하드웨어 제약 없이 사용 가능
- 단점
	- 버퍼풀 공간 활용률 낮고,
	- 쿼리 성능이 낮고
	- 빈번한 데이터 변경 시, 압축률이 떨어지고
- [[innoDB]] 페이지 크기 (innodb_page_size) 가 32kb, 64kb인 경우엔 테이블 압축 적용 불가
	- 16kb인 경우에만 사용가능
	- 한계가 있다

![image](http://ymeet.me/techblog/wp-content/uploads/2018/12/Untitled-drawing-2.png)
- 목표 크기 (8KB 될 때 까지) split 을 계속함
- 즉 KEY_BLOCK_SIZE (목표 크키) 설정이 잘못되면, 처리 성능이 급격히 떨어질 수 있음

---
## Reference
 - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 6.2 테이블 압축
	- 6.2.1 압축 테이블 생성
	- 6.2.2 KEY_BLOCK_SIZE 결정
	- 6.2.3 압축된 페이지의 버퍼 풀 적재 및 사용
- https://ymeet.me/techblog/2018/12/14/compressing-mysql-table/