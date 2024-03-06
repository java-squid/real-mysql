- [[sql-parser]] 가 쿼리를 분석하고, 생성하는 데이터 구조
- 쿼리의 구조와 의미를 나타내는 트리형태

> 예시

```sql
SELECT * FROM customers WHERE country = '대한민국';
```

```txt
SELECT 
  / \ 
  * WHERE 
     / \ 
    = country 
        / \ 
        '대한민국'
```

---
## Reference
- https://dev.mysql.com/doc/refman/8.3/en/show-parse-tree.html