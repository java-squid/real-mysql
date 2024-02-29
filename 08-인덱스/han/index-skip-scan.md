- MySQL 8.0 부터 지원
- `Using index for skip scan`
- 인덱스 (A,B) 컬럼일 때, 조건절에 B 가 들어갈 경우 옵티마이저가 내부적으로 임의의 A값을 조건에 추가해서 인덱스를 사용할 수 있도록 만들어 주는 것
- 그러므로 
	- WHERE 조건절에 조건이 없는 인덱스의 선행 칼럼의 유니크한 값의 갯수가 적어야하고,
	- 쿼리가 인덱스에 존재하는 칼럼만으로 처리 가능해야함 [[covering-index]]

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.3.4.4 인덱스 스킵 스캔