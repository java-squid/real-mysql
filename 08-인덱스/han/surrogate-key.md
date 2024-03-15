- [[primary-key]] 를 대체하기 위해 인위적으로 추가된 식별자
- `AUTO-INCREMENT` 칼럼을 보통 이용함
	- 그래서 자동 증가되고
	- 데이터 변경 최소화됨.
- 그렇지만 해당 키를 사용하면,
	- 비즈니스 의미가 부족하고 (인공 숫자들이므로)
	- 추가적인 공간도 사용해야함 (해당 숫자들 저장을 위해)

> 예시

```sql
CREATE TABLE users ( 
 id INT PRIMARY KEY AUTO_INCREMENT, 
 name VARCHAR(255), 
 email VARCHAR(255) 
 );
```

- `id` 가 [[surrogate-key]]

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.8.4.4 AUTO-INCREMENT 칼럼을 인조식별자로 사용할 경우

