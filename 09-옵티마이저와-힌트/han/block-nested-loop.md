- [[nested-loop-join]] 와 가장 큰 차이점은 [[join-buffer]] 를 사용하는 것
- 그리고 조인에서 드라이빙 테이블과 드리븐 테이블이 어떤 순서로 조인되느냐
- `Extra` `Using Join buffer` 는 그 실행 계획에서 [[join-buffer]] 를 사용함을 의미

--- 
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.3.1.2 블록 네스티드 루프 조인