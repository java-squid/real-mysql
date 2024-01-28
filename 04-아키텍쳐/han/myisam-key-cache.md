- [[innoDB-buffer-pool]] 과 비슷한 역할
- 키 버퍼라고도 불림
- 인덱스만을 대상으로 작동
	- 그러므로 [[myisam]] 은 디스크 검색 없이 충분히 빠르게 검색이 가능하도록 함
 - 인덱스의 디스크 쓰기 작업에 대해서만 부분적으로 버퍼링 역할

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.3.1 키 캐시