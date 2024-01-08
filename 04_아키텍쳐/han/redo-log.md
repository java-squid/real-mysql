- 데이터베이스의 변화의 모든 히스토리의 로그
- [ACID](https://ko.wikipedia.org/wiki/ACID) 중, durable, 영속성과 가장 밀접하게 연관
- 서버가 비정상적으로 종료되었을 때, 데이터를 잃지 않게 해주는 안전장치

> MySQL 서버가 비정상 종료되는 경우 InnoDB 스토리지 엔진의 데이터 파일이 가질 수 있는 경우의 수?

1. 커밋되었지만, 데이터 파일에 기록되지 않은 데이터
2. 롤백되었지만, 데이터 파일에 이미 기록된 데이터

- 1번의 경우, [[redo-log]] 기반으로 데이터 파일에 반영하기만 하면 됨
- 2번의 경우, [[redo-log]] 로는 해결할 수 없고, [[undo-log]] 를 기반으로 데이터 파일에 반영해야한다.

---
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.2.11 리두 로그 및 로그 버퍼
- https://en.wikipedia.org/wiki/Redo_log