- [[preprocessor]] 을 거쳐 나온 쿼리 문장을 가장 저렴한 비용으로 가장 빠르게 처리할 지를 결정하는 역할
- DBMS의 두뇌
- [[query-execution-process]] 에서 2번째(최적화 및 실행 계획 수립) 단계의 일을 처리하는 모듈

> 종류

- 비용 기반 최적화 (Cost-based optimizer)
	- CBO
	- 각 단위 작업의 비용 정보, 예측된 통계 정보를 이용해 실행 계획별 비용 산출
	- 최소 비용으로 소요되는 방식을 선택하게 됨
	- 현재 대부분의 DBMS가 선택하고 있는 방식

- 규칙 기반 최적화 (Rule-based optimizer)
	- [[optimizer]] 에 내장된 우선 순위에 따라 실행 계획을 수립하는 방식
	- 거의 모든 사용자에 대해 같은 실행 방법으로 실행되기 때문에 사용되지 않음


--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.1.6.3 옵티마이저
	- 9.1.2 옵티마이저 종류