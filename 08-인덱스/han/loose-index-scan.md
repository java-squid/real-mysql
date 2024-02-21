- tight index scan
- 느슨하게 또는 듬성듬성하게 인덱스를 읽는 것
- [[index-range-scan]] 과 비슷하게 동작하지만, 중간에 필요하지 않는 인덱스 키 값은 무시(SKIP) 하고 다음으로 넘어가는 형태로 처리되는 것을 의미
- 일반적으로 `GROUP BY`  와 같은 집합함수,  `MAX()`  와 같은 집계 함수에 대해 최적화 할때 사용됨
---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.3.4.3 루스 인덱스 스캔