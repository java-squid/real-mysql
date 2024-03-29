- 검색해야할 인덱스의 범위가 결정됐을 때 사용하는 방식
- 검색하려는 값의 수나, 검색 결과 레코드 건수와 관계없이 range-scan 이라고 표현
- 루트, 브랜치노드를 이용해 스캔 시작 위치를 검색하고, 그 지점부터 필요한 방향 (오름 혹은 내림차순) 으로 읽어나가는 과정
- 리프노드에서 검색 조건이 일치하는 건들에 대해, 데이터 파일에서 레코드를 읽어오는 과정이 필요.
	- 이 때 레코드 한 건 단위로 [[random-IO]] 가 발생.

> 정리해보면 인덱스 레인스 스캔 3단계를 거침

1. 인덱스 탐색(index seek), 인덱스에서 조건을 만족하는 값이 저장된 위치를 찾음
2. 인덱스 스캔(index scan), 1번에서 탐색된 위치부터 인덱스를 차례로 읽음 
3. 2번에서 읽은 인덱스 키, 레코드 주소를 통해, 레코드가 저장된 페이지를 가져오고 최종 레코드를 일겅옴
---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.3.4.1 인덱스 레인지 스캔