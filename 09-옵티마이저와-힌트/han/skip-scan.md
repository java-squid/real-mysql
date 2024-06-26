- 인덱스의 제약사항을 제한적이지만 뛰어넘을 수 있는 최적화 기법
- 인덱스의 핵심은 값이 정렬되어 있음.
	- 즉 인덱스를 구성하는 칼럼의 순서가 매우 중요하다
	- 예를 들어 (A,B,C) 칼럼으로 구성된 인덱스가 있을 때, 어떤 쿼리에 `WHERE` 절에 B,C 에 대한 조건을 가지고 있으면 이 쿼리는 인덱스를 사용할 수 없음
	- 하지만 [[skip-scan]] 옵션을 사용하면 이 제약을 한정적으로 뛰어남게 됨

- 정리하자면,
	- 인덱스의 선행 칼럼이 조건절에 사용되지 않더라도 후행 칼럼의 조건만으로 인덱스를 이용한 쿼리 성능 개선이 가능하게 만드는 기능


> [[optimizer-hint]]

- `SKIP_SCAN`
	- 인덱스의 선행 칼럼에 대한 조건이 없어도, [[optimizer]] 가 해당 [[08-인덱스/han/index|index]] 를 사용할 수 있도록 함
- `NO_SKIP_SCAN`
	- [[skip-scan]] 을 사용하지 않도록 하는 옵션

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.3.1.18 스킵 스캔
	- 9.4.2.11 SKIP_SCAN & NO_SKIP_SCAN