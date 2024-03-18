- 정렬을 처리하는 방법은 [[index]] 를 이용하는 방법과, 쿼리가 실행될 때 `Filesort` 라는 별도의 처리를 이용하는 방법


### [[index]] 이용

- 장점
	- 이미 정렬되어있어서, 읽기만 하면 됨
	- 매우 빠르다
- 단점
	- INSERT, UPDATE, DELETE 작업시 부가적인 인덱스 추가/삭제 작업이 필요
	- 인덱스 -> 디스크 공간 더 필요
	- 인덱스 갯수가 늘어날수록 [[innoDB-buffer-pool]] 을 위한 메모리 더 필요

### [[filesort]] 이용

- 장점
	- 인덱스 생성하지 않아도 됨
	- 정렬해야할 레코드가 많지 않으면 메모리에서 처리 됨 (충분 빠름)
- 단점
	- 정렬 작업이 쿼리 실행 시 실행, 레코드 건수가 많아질수록 쿼리의 응답 속도가 느림

## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.2.3 ORDER BY 처리(Using filesort)