- `DESC`, `EXPLAIN` 
- 실행 계획을 확인하는 키워드

> 예시

- 테이블 포맷

```sql
EXPLAIN
SELECT *
FROM employees e
WHERE first_name = 'ABC';
```

- 트리 포맷

```sql
EXPLAIN FORMAT=TREE
SELECT *
FROM employees e
WHERE first_name = 'ABC';
```

- Json 포맷

```sql
EXPLAIN FORMAT=JSON
SELECT *
FROM employees e
WHERE first_name = 'ABC';
```

> 분석

![image](https://github.com/java-squid/real-mysql/assets/22140570/b96db4c3-4ef2-4fea-8d45-c6b8cf1cf082)

- id
	- 단위 `SELECT` 쿼리별 부여되는 식별자 값
	- 해당 컬럼이 테이블의 접근 순서를 의미하지 않는다.
- select_type
	- 쿼리가 어떤 타입의 쿼리인지 
		- [[SIMPLE]]
		- [[PRIMARY]]
		- [[UNION]]
		- [[DEPENDENT UNION]]
		- [[UNION RESULT]]
		- [[SUBQUERY]]
		- [[DEPENDENT SUBQUERY]]
		- [[DERIVED]]
		- [[DEPENDENT DERIVED]]
		- [[UNCACHEABLE SUBQUERY]]
		- [[UNCACHEABLE UNION]]
		- [[MATERIALIZED]]
- type
	- [[mysql-server]] 가 각 테이블의 레코드를 어떤 방식으로 읽었는지 알려줌
		- [[system]]
		- [[const]]
		- [[eq_ref]]
		- [[ref]]
		- [[full_text]]
		- [[ref_or_null]]
		- [[unique_subquery]]
		- [[index_subquery]]
		- [[range]]
		- [[index_merge]]
		- [[10-실행-계획/han/index|index]]
		- [[ALL]]
- possible_keys
	- [[optimizer]] 가 최적의 실행계획을 만들기 위해 후보로 선정했던 접근 방법에서 사용되는 인덱스 목록
	- 사용될법했던 [[08-인덱스/han/index|index]] 목록이다.
	- 무시해도 무방
- key
	- 최종 선택될 실행계획에서 사용하는 [[08-인덱스/han/index|index]]
	- 쿼리 튜닝 시, 해당 칼럼에 의도했던 [[08-인덱스/han/index|index]] 가 표시되는 지 확인하는 것이 **중요**
	- [[ALL]] 과 같은 `type` 이면 해당 칼럼은 `null` 로 표시된다.
- key_len
	- 쿼리를 처리하기 위해 다중 칼럼으로 구성된 [[08-인덱스/han/index|index]] 에서 몇 개의 칼럼 까지 사용했는지 알려주는 칼럼
	- `byte` 로 알려준다.
- ref
	- 참조 조건으로 어떤 값이 제공되었는지 보여둠
	- 상수값 -> `const`
- rows
	- 얼마나 많은 [[record]] 를 읽고 비교해야하는 지 예측한 값
	- 예측한 값이므로 정확하진 않음.
- filtered
	- 필터링되고 남은 [[record]] 의 비율
	- e.g. rows = 233, filtered = 16.03 일때, 인덱스 조건에 일치하는 [[record]] 가 233건이며 (대략), 16.03 % 만 인덱스를 사용하지 못하고, 조건에 일치하는 것
		- 즉 233 * 16.03 = 37건 정도가 인덱스를 사용하지 못하지만 일치했다는 의미
- extra
	- `const row not found` 
		- 해당 테이블에 레코드가 1건도 없을 때
	- `Deleting all rows` 
	- `Distinct` 
		- 조인하지 않아도 되는 항목은 모두 무시하고 필요한 것만 조인했다는 의미
	- `FirtMatch`
		- [[semi-join]] 최적화 방법 중 하나
	- `Full scan on NULL key`
	- `Impossible HAVING`
		- 쿼리에 사용된 `HAVING` 절의 조건을 만족하는 레코드가 없을 때
	- `Impossible WHERE`
		- 쿼리에 사용된 `WHERE` 절 조건이 항상 FALSE 가 될 수 밖에 없을 때
	- `LooseScan`
		- [[semi-join]] 최적화 방법 중 하나
	- `No matching min/max row`
		- `min`, `max` 조건에 매칭되는 row가 없을 때
	- `no matching row in const table`
		- 조인에 사용된 테이블에서 const 방법으로 접근할 때 일치하는 레코드가 없을 때
	- `no matching rows after partition pruning`
		- 파티션된 테이블에 대한 `UPDATE`, `DELETE` 명령 시에, 대상 레코드가 없을 때
	- `no tables used`
		- `FROM` 절이 없는 쿼리 문장
	- `not exists`
	- `plan isn't ready yet`
		- 해당 커넥션에서 아직 쿼리 실행 계획이 수립되지 않은 상태
	- `Range checked for each record`
		- [[record]] 마다 [[index-range-scan]] 을 체크할 때
	- `recursive`
		- 재귀 쿼리 작성시
	- `rematerialize`
		- 매번 임시 테이블이 새로 생성되는 경우
	- `select tables optimized away`
		- 쿼리가 인덱스를 오름차순 또는 내림차순으로 1건만 읽는 형태일 때
	- `start temporary, end temporary`
	- `unique row not found`
	- `using filesort`
		- `ORDER BY` 처리가 인덱스를 사용하지 못할 때
		- 많은 부하를 일으키므로, 가능하다면 쿼리 튜닝 혹은 인덱스를 생성하는걸 고려해야한다.
	- `using index`
		- [[covering-index]]
		- 데이터 파일을 전혀 읽지 않고, 인덱스만 읽어서 쿼리를 모두 처리할 수 있을 때
	- `using index condition`
		- [[index-condition-pushdown]] 최적화를 사용하는 경우
	- `using index for group-by`
		- `GROUP BY` 처리에 [[08-인덱스/han/index|index]] 를 사용하는 경우
	- `using inde for skip scan`
		- [[index-skip-scan]] 을 사용하는 경우
	- `using join buffer`
		- [[block-nested-loop]] 조인이나, [[hash-join]] 을 사용하는 경우
	- `using MRR`
		- multi range read
	- `using sorit_union, using union, using, intersect`
		- [[index-merge]] 접근 방법으로 실행되는 경우
	- `using temporary`
		- 쿼리 처리 시에, 중간 결과를 담아 두기 위한 임시테이블을 생성한 경우
		- 이 임시 테이블이 메모리 혹은 디스크 중 어디에 생성되었는지는 모른다.
	- `using where`
		- [[mysql-engine]] 에서 별도의 가공을 해서 필터링 작업을 처리한 경우
		- 가장 흔함
	- `zero limit`
		- `LIMIT 0` 조건이 쿼리에 들어간 경우
---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 10.2 실행 계획 확인
	- 10.2.1 실행 계획 출력 포맷
	- 10.3.1 id 칼럼
	- 10.3.2 select_type 칼럼
	- 10.3.6 possible_keys 칼럼
	- 10.3.7 key 칼럼
	- 10.3.8 key_len 칼럼
	- 10.3.9 ref 칼럼
	- 10.3.10 row 칼럼
	- 10.3.11 filtered 칼럼
	- 10.3.12 Extra 칼럼
- https://velog.io/@ddongh1122/MySQL-%EC%8B%A4%ED%96%89%EA%B3%84%ED%9A%8D-EXPLAIN