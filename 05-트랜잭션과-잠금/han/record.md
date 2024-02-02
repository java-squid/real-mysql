- [[table]] 에 저장된 하나의 개별 데이터 항목
- [[table]] 의 각 행(row)  와 동일한 의미
- 열(column) 은 해당 [[record]] 의 속성(attribute) 에 해당 하는 값을 저장

> 특징
- [[table]]의 가장 작은 데이터 단위
- 각 열에 해당하는 값의 집합
- [[table]] 내의 모든 [[record]] 는 동일한 구조를 가짐
- 각 [[record]] 는 고유한 식별자를 가질 수 있음

```sql
INSERT INTO customers (first_name, last_name, email) VALUES ('John', 'Doe', 'johndoe@example.com'); // record를 추가하는 SQL 명령어
```
---
## Reference
- https://www.w3schools.com/sql/sql_intro.asp