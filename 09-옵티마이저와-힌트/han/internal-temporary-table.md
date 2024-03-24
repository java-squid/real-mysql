- [[mysql-engine]] 이 [[storage-engine]] 으로 부터 받아온 [[record]] 를 정렬하거나 그루핑 할 때 사용되는 내부적인 임시 테이블
- 처음에는 메모리에 생성되었다가, 테이블의 크기가 커지만 디스크로 옮겨짐
- 처음 부터 디스크로 생성되는 케이스도 있음.
- 임시 테이블을 사용하는지 확인 하기 위해서는 `Extra` 컬럼에서 `Using temporary` 라는 메세지가 표시되는지 확인하기만 하면 됨
---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.2.6 내부 임시 테이블 활용