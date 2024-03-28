- 정렬 키와 [[record]] 의 [[rowid]] 만 가져와서 정렬하는 방식
	- [[two-path]]
- 정렬 키와 [[record]] 전체를 가져와서 정렬하는 방식, [[record]] 의 칼럼들은 고정 사이즈로 메모리 에 저장 
	- [[single-path]]
- 정렬 키와 [[record]] 전체를 가져와서 정렬하는 방식, [[record]] 의 칼럼들은 가변 사이즈로 메모리에 저장
	- [[single-path]]

## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.2.3.2 정렬 알고리즘