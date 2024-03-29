- [[innoDB]] 에서 사용자가 자주 요청하는 데이터에 대해 자동으로 생성하는 인덱스
- [[innoDB]] 에 하나만 존재하는 인덱스이다.


> 왜 도입?
- b-tree 인덱스 발생하는 검색 시간을 줄여주기 위해 도입된 기능
	- 검색 시간?
	- b-tree는 특정 값을 찾기 위해, 루트 -> 브랜치 -> 리프 노드까지 가야 최종 레코드에 도달할 수 있음.
	- 이런 작업이 몇천 개의 스레드로 실행하면, 쿼리 성능이 떨어진다.
	- 위 부분을 보완하려 나온 인덱스

> 구성
- key
	- b-tree index의 고유 번호(id)
- value
	- b-tree index의 실제 키 값(실제 데이터 페이지 주소)

> 도움이 되는 경우

- 디스크 읽기가 많지 않은 경우
- 동등 조건 검색 (IN 연산자) 가 많은 경우
- 쿼리가 데이터 중 일부 데이터에만 집중되는 경우

> 조심해야할 점

- [[adaptive-hash-index]] 사용하면 메모리 공간 사용하고,
- 활성화 되었을 경우, [[innoDB]] 가 인덱스 사용 전에, [[adaptive-hash-index]] 를 항상 확인해봐야함
 ---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.2.12 어댑티브 해시 인덱스