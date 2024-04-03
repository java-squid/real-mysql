- [[index-merge]] 작업 중에 결과의 정렬이 필요한 경우, [[mysql-server]] 는 인덱스 머지 최적화에 [[sort-union]] 알고리즘을 사용
- `Extra` -> `Using sort_union`

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.3.1.8 인덱스 머지 - 정렬 후 합집합