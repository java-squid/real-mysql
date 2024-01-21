- [[innoDB-storage-engine-lock]] 에서 존재하는 [[lock]]
- [[record]] 와 [[record]] 사이의 간격을 잠그는 락

![image](https://miro.medium.com/v2/resize:fit:1008/format:webp/1*JOJ-SyOL4U4-b3EZvflLEg.png)

```sql
CREATE TABLE tb_gaplock (  
id INT NOT NULL,  
name VARCHAR(50) DEFAULT NULL,  
PRIMARY KEY (id)  
);

INSERT INTO tb_gaplock  
VALUES (1, ‘Matt’), (3, ‘Esther’), (6, ‘Peter’);
```
- 위 SQL 실행 시, 2,4,5 row에 대해 [[gap-lock]] 을 획득한다.

### 왜 gap-lock을 사용할까?

- [[record]] 와 [[record]] 사이에 새로운 [[record]] 가 생성되는 것을 제어함.

> TODO


---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 5.3 InnoDB 스토리지 엔진 잠금
	- 5.3.1 InnoDB 스토리지 엔진 잠금
	- 5.3.1.2 갭 락
- https://medium.com/daangn/mysql-gap-lock-%EB%8B%A4%EC%8B%9C%EB%B3%B4%EA%B8%B0-7f47ea3f68bc