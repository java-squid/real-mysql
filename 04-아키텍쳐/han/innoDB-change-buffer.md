- 변경해야할 인덱스 페이지가 버퍼 풀에 있다면, 바로 업데이트 수행
- 그렇지 않고, 디스크로부터 읽어와서 업데이트해야 한다면 이를 즉시 실행하지 않고 임시 공간에 저장해두고 바로 사용자에게 결과를 반환하는 형태로 성능향상함.
- 이때 사용하는 임시 메모리가 [[innoDB-change-buffer]] 
- unique index의 경우엔 [[innoDB-change-buffer]] 를 사용하지 못함 
	- 왜? 
	- 반드시 중복 결과를 체크해야하므로.
- [[innoDB-change-buffer]]에 임시 저장된 인덱스 레코드 조각은 [[background-thread]] 에 의해서 병합됨.
	- 이를 `merge thread` 라 한다.

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.2.10 체인지 버퍼