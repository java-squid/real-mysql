- 정렬을 수행하기 위해 별도로 할당받은 메모리 공간
- 정렬해야하는 [[record]] 크기에 따라 가변적으로 변경되지만, 최대 사용 가능한 한계는 설정할 수 있음 (`sort_buffer_size` )
- 정렬해야할 레코드가 적다면 문제 없음
- 만약 정렬해야할 레코드가 엄청 많다면?
	- 해당 레코들을 여러 조각으로 나눠서 처리.
	- 이 과정에서 임시 저장을 위해 디스크 사용
	- 메모리에서 정렬 수행 -> 그 결과를 임시로 디스크에 저장 -> 레코드 가져와서 정렬 실행 ...
	- 정렬된 레코드를 병합하면서 또 정렬 수행 (Muliti-merge)
	- 즉 디스크 쓰기, 읽기를 유발

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.2.3.1 소트 버퍼