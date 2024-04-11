- 인덱스 머지 교집합
- `Extra` 에 `Using intersect` 
- 쿼리가 여러개의 인덱스를 각각 검색해서, 그 결과의 교집합만 반환했다는 뜻
- 해당 옵션을 비활성화 할수도
	- `index_merge_intersection=off`

--- 
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.3.1.6 인덱스 머지 - 교집합