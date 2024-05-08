- [[08-인덱스/han/index|index]] 를 처음부터 끝까지 스캔하는 것을 의미

```sql
SELECT count(*) FROM employees
```
- 단순히 레코드 건수만 필요로하는 쿼리라면, 용량 작은 [[08-인덱스/han/index|index]] 선택
	- 왜?
	- 디스크 읽기 횟수를 줄일 수 있기 때문

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.2.1 풀 테이블 스캔과 풀 인덱스 스캔