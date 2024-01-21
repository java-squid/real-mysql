- 가상 [[table]]
- 실제 [[table]] 에 저장된 데이터를 기반으로 하지만, [[view]] 자체로 데이터를 저장하진 않는다
	- 즉 [[view]] 는 자체적, 독립적으로 존재할 수 없음

### 생성 방법
```sql
CREATE VIEW view_name 
AS SELECT column1, column2, ... 
FROM table_name 
WHERE condition;
```
### 사용 이유
- 복잡한 쿼리 단순화
	- 자주 사용하는 쿼리는 [[view]] 로 만들어 놓고, 사용하면 편리
- 데이터 보안 강화
	- 사용자에게 필요한 부분의 데이터만 보여준다
- 데이터 독립성 향상
- 데이터베이스 구조 캡슐화

---
## Reference
- https://www.w3schools.com/mysql/mysql_view.asp