- Spatial index, 공간 인덱스
- 공간인덱스는 R-tree 인덱스 알고리즘을 이용해, 2차원의 데이터를 인덱싱하고 검색하는 목적의 인덱스
- 기본적으로 [[b-tree-index]] 와 흡사
	- [[b-tree-index]] 는 1차원의  [[scalar]]
	- [[r-tree-index]] 는 2차원의 공간 개념

> 용도

- 위도, 경도 좌표 저장에 주로 사용
- '현재 사용자 위치로부터 반경 5km 이내 음식점 검색' 과 같은 검색에 사용할 수 있음

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.4 R-tree 인덱스
	- 8.4.2 R-tree 인덱스 용도