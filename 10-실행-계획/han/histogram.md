- 칼럼의 데이터 분포도
	- 즉 각 범위 (버킷) 에 얼마나 많은 [[record]]가 있는지 나타낸다
- [[optimizer]] 가 실행계획을 생성하는 데 사용한다
- 칼럼 단위로 관리됨.
- 자동으로 수집되지 않고, `ANALYZE TABLE .... UPDTE HISTOGRAM` 명령을 수행해 수동으로 수집 및 관리

> 종류

- Singleton
	- 싱글톤 히스토그램
	- 칼럼값 개별로 레코드 건수를 관리하는 히스토그램
		- e.g. 성별 -> `M` or `F`
	- `Value-Based` 히스토그램 또는 도수 분포라도 불린다.
- Equi-height
	- 높이 균형 히스토그램
	- 칼럼값의 범위를 균등한 개수로 구분해서 관리하는 히스토그램
		- e.g. hire_date...
	- `Height-Balanced` 히스토그램이라고도 불린다

> 용도

- [[histogram]] 도입 전에도 [[mysql-server]] 는 테이블과 [[08-인덱스/han/index|index]] 에 대한 통계정보가 존재.
	- 전체 [[record]] 건수, [[08-인덱스/han/index|index]] 된 칼럼이 가지는 유니크한 값의 개수 정도
	- 그렇지만 이정도의 통계 정보로는 사용자별 여러 상황에 대처하지 못함
	- 이를 대응하기 위해 [[histogram]] 등장
	- 사용자별 통계정보를 수집하는 것임
- 사용자별 통계정보를 기반으로, [[optimizer]] 가 적절한 실행계획을 세울 수 있도록 도와준다

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.1.2 히스토그램
	- 10.1.2.1 히스토그램 정보 수집 및 삭제
	- 10.1.2.2 히스토그램의 용도