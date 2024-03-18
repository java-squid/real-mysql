- [[sort-buffer]] 에 정렬 기준 칼럼 포함, `SELECT` 대상이 되는 칼럼 전부를 담아서 정렬을 수행하는 정렬 방식
- [[two-path]] 에 비해 많은 메모리 공간이 필요
	- e.g. [[two-path]] 에서 128KB의 [[sort-buffer]] 를 사용한다면 7000건 반면 [[single-path]] 에서는 3500건 정도만 정렬할 수 있ㅇ므
- 

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.2.3.2.1 싱글 패스 정렬 방식