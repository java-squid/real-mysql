- [[explain]] 의 타입.
- [[eq_ref]] 와는 달리 조인의 순서 없이 사용됨.
- [[primary-key]] 나 [[unique-key]] 등의 제약 조건도 없음.
- 인덱스 종류와 관계엾이 동등(equal) 조건으로 검색할 때 사용됨.
- [[const]] 와는 다르게 반환되는 레코드가 반드시 1건이라는 보장이 없다.₩

> 예시

```sql

SELECT * FROM dept_emp WHERE dep_no = 'd005';
```

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.3.5.4 ref