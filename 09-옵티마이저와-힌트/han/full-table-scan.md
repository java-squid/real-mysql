- [[index]] 를 사용하지 않고, 테이블의 데이터를 처음부터 끝까지 읽어서 요청된 작업을 처리하는 작업
- 다음 조건이 만족할 때 선택됨
	- 테이블의 레코드 건수가 너무 작은 경우, 인덱스를 통해 읽는 것보다 [[full-table-scan]] 하는 편이 빠른 경우
		- 일반적으로 테이블이 페이지 1개로 구성된 경우
	- `where` or `on` 절 [[index]] 를 이용할 수 있는 적절한 조건이 없는 경우
	- [[index-range-scan]] 을 사용할 수 있더라도, [[optimizer]] 가 판단하기에 일치 레코드 건수가 너무 많은 경우

> 어떻게 동작하는가?

- 처음 몇개의 데이터 페이지를 [[foreground-thread]] 가 페이지 읽기를 실행
- 특정 시점 부터는 [[background-thread]] 로 넘김
- 4 or 8개씩의 페이지를 읽으면서 그 수를 계속 증가
	- 최대 64개 데이터 페이지까지 읽어서, [[innoDB-buffer-pool]] 에 저장
- 즉 [[foreground-thread]] 는 [[innoDB-buffer-pool]] 에 있는 데이터만 가져다 쓰면 되므로, 생각보다는 빠르게 처리된다.
---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.2 기본 데이터 처리