- [[optimizer-hint]]
- MySQL 5.7 이전에는 `FROM` 절에 사용된 서브쿼리는 항상 내부 임시 테이블로 생성됨
	- 이렇게 생성된 내부 임시 테이블을 [[derived-table]] , 파생 테이블이라 하는데 이는 불필요한 자원 소모를 유발
	- 이를 방지하기 위해 서브 쿼리 - 외부 쿼리 병합하는 최적화를 도입
	- [[optimizer]] 가 병합할지 아니면 임시 테이블을 선택할지 결정
	- [[optimizer]] 가 최적의 방법을 선택하지 못할 수도 있으니, 이를 대비하여 위 힌트를 사용
- [[MERGE]] 옵션은 서브쿼리 - 외부 쿼리를 병합하는 옵션

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.4.2.8 MERGE & NO_MERGE