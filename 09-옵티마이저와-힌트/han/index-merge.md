- 하나의 테이블에 대해 2개 이상의 [[08-인덱스/han/index|index]] 를 이용해 쿼리를 처리하는 것
- 여러 인덱스를 통해, 검색된 [[record]] 로부터 교집합 또는 합집합만을 구해서 그 결과를 반환 하는 것
- 그 종류...
	- [[index-merge-intersection]]
	- [[index-merge-union]]
	- [[index-merge-sort-union]]

> [[optimizer]] 힌트 옵션

- `INDEX_MERGE`
- `NO_INDEX_MERGE`
	- [[index-merge]] 를 사용하고 싶지 않을 때

--- 
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.3.1.5 인덱스 머지
	- 9.4.2.9 INDEX_MERGE & NO_INDEX_MERGE