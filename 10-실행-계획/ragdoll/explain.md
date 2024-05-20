# Explain

- 옵티마이저가 쿼리를 어떻게 처리 할지 실행계획을 확인하는 방법

## 인덱스 다이브

- 옵티마이저는 레코드 건수를 파악하여 실행 계획을 수립하는데, 인덱스 B-Tree를 샘플링 하는 과정

## 코스트 모델

- 실행 계획을 수립하기 위한 비용 계산에 필요한 작업 비용(cost)

---

## 실행 계획 분석

- `EXPLAIN` 을 포함한 쿼리를 실행하면 실행 계획을 테이블 형식으로 노출
- 사용된 테이블 개수만큼 row 조회 됨
- 먼저 접근한 테이블이 위쪽, 나중에 접근한 테이블이 아래쪽에 위치

### id 컬럼

- SELECT문 개수만큼 생성 됨 (SELECT문에서 접근한 테이블마다 서로 다른 id 값을 부여함)
- 하나의 SELECT에서 JOIN이 수행되는 경우, 동일한 id 값을 가짐
- 서로 다른 SELECT문의 경우 id의 대소 관계가 테이블 접근순서를 나타내지는 않음
  - 접근 순서를 식별하고 싶다면 `FORMAT=TREE` 로 조회한 후 들여쓰기를 확인하면 힌트를 얻을 수 있음
    - 가장 먼저 접근 된 테이블 일수록 들여쓰기 깊음

### select_type 컬럼

- SELECT 쿼리가 어떤 타입의 쿼리인지 표시
- SIMPLE
  - UNION, 서브쿼리가 아닌 단순한 SELECT 쿼리 (일반적으로 가장 바깥 SELECT 쿼리)
- PRIMARY
  - UNION, 서브쿼리를 가지는 쿼리 중 가장 바깥 SELECT 쿼리
- UNION
  - UNION을 갖는 쿼리 중 가장 바깥 쿼리가 아닌 SELECT 쿼리
- DERIVED
  1.  UNION의 결과가 임시 테이블을 생성하는 경우, 첫 번째 쿼리가 DERIVED로 설정 된다.
      - 나머지 테이블은 UNION 값을 가진다.
  2.  서브쿼리를 사용하는 경우, FROM절의 서브쿼리
- DEPENDENT UNION
  - UNION으로 테이블이 결합될 때, 외부 쿼리에 의해 결과가 영향을 받는 경우 표시
- DEPENDENT SUBQUERY
  - 서브쿼리가 바깥 쪽 쿼리의 컬럼을 사용하는 경우
  - 외부 쿼리가 먼저 실행되어야 하므로 처리 속도에 영향을 받을 수 있음

```sql
-- DEPENDENT UNION example
> EXPLAIN
  SELECT *
  FROM employees e1 WHERE e1.emp_no IN (
	  SELECT e2 emp_no FROM employees e2 WHERE e2.first_name = 'Matt'
	  UNION
	  SELECT e3.emp_no FROM employees e3 WHERE e3.last_name = 'Matt'
  );
```

- UNION RESULT
  - UNION의 결과를 담아두는 임시 테이블에 부여 함
  - 명시적인 SELECT 테이블은 아니기 때문에 id 값은 생성되지 않는다.
- SUBQUERY
  - FROM 절 외에 다른 곳에서 사용된 서브쿼리
- DEPENDENT DERIVED
  - 레터럴 조인을 사용한 테이블에 부여되는 값
  - LETERAL JOIN
    - MySQL 8.0부터 FROM절의 서브쿼리에서 바깥 쿼리의 컬럼을 사용할 수 있게 되었음
    - 이 경우, LETERAL JOIN을 사용해야 함
      - `[LEFT/RIGHT/INNER] JOIN LETERAL` 키워드 사용
- UNCACHEABLE SUBQUERY
  - SUBQUERY는 그 결과를 캐시해서 사용하는데, 한번 캐시 해두고 그 결과를 공통으로 사용
  - 만약 공통으로 사용할 수 없는 경우 값 단위로 서브쿼리 결과를 캐시하는데, 이 것을 UNCACHEABLE SUBQUERY라 함
  - 캐시를 사용할 수 없는 경우는 다음과 같다.
    - 서브쿼리에 사용자 변수 사용
    - NOT_DETERMINISTIC 속성의 스토어드 루틴 사용
      - (?)
    - UUID(), RAND()와 같이 호출 시마다 달라지는 함수 사용
- UNCACHEABLE UNION
- MATERIALIZED
  - 서브쿼리가 IN 절에 사용된 경우, 서브 쿼리의 결과를 임시테이블로 만드는 방식으로 최적화한다.

##### 서브 쿼리의 종류

- Nested Query
  - SELECT 절에 사용된 쿼리
- Subquery
  - WHERE 절에 사용된 쿼리
- Derived Table
  - FROM 절에 사용된 쿼리
  - Inline View 또는 Sub Select라고도 함

### table 컬럼

- SELECT 문을 만들면서 접근한 테이블명
- 별칭이 사용된 경우 별칭을 표시
- 별도 테이블을 사용하지 않는 경우 `NULL`
- 임시 테이블인 경우 `<>` 안의 숫자는 임시 테이블 로우의 id 컬럼 값

### partitions 컬럼

- 파티션된 테이블을 조회하는 경우 어떤 파티션을 조회 했는지 표시

### type 컬럼

- 테이블 레코드를 어떤 방식으로 읽었는지 표시하는 컬럼
  - ex) 인덱스, 풀스캔, ...
- system
  - 레코드가 0개 또는 1개인 테이블에 접근할 때
  - MyISAM, MEMORY 테이블에서만 사용되는 값
- const
  - WHERE절에서 PK 또는 UNIQUE 인덱스를 이용하고, 단 1건의 레코드 반환만을 보장할 때
- eq_ref
  - 여러 테이블이 조인되는 쿼리에서만 표시되는 값
  - 드라이빙 테이블의 컬럼 값이 조인 테이블의 PK, UNIQUE INDEX 컬럼과 검색 조건으로 사용되는 경우
  - 드리븐 테이블의 PK, UK 컬럼으로 검색하는 경우이고, 드리븐 테이블에서 각 1건의 데이터만 조회되는 것을 보장하는 경우
- ref
  - 조인 순서, 인덱스 여부와 관계 없이 동등 조건으로 검색되는 경우
- fulltext
  - 전문 검색 인덱스를 사용해서 레코드를 읽는 경우
- ref_or_null
  - ref 방식에 NULL비교 추가
- unique_subquery
  - 서브쿼리에서 중복되지 않는 유니크한 결과만 반환할 때
- index_subquery
  - 중복된 결과를 반환할 수 있으나, 인덱스를 이용해 중복 결과를 제거할 수 있을 때
- range
  - 인덱스 레인지 스캔
- index_merge
  - 2개 이상의 인덱스를 사용해 각각의 검색 결과를 만들고, 이를 합쳐서 처리하는 법
- index
  - 인덱스 풀스캔
  - 사용되는 조건
    1.  - range, const, ref 방법이 불가한 경우
        - 인덱스에 포함된 컬럼만으로 처리 가능
    2.  - range, const, ref 방법이 불가한 경우
        - 인덱스를 이용해 정렬, 그루핑 작업 가능
- ALL
  - 테이블 풀 스캔

### possible_keys 컬럼

- 실행 계획을 세우는 과정에서 사용을 고려했던 모든 인덱스 목록

### key 컬럼

- 실행 계획에서 고려되었던 후보군 중 실제로 재택되어 사용된 인덱스

### key_len 컬럼

- 인덱스의 각 레코드에서 사용된 바이트 크기 정보
- 복합 인덱스의 경우 구성 중 몇 개의 컬럼을 사용했는지 알 수 있다.

### ref 컬럼

- ref 방식(type 값이 ref)으로 접근했다면 비교 조건으로 어떤 값이 제공됐는지 보여준다.
  - 상수면 const
  - 컬럼이면 `테이블.컬럼명` 표시
  - 값을 변형한 경우(MySQL 서버에 의해 자동 변환 or 사용자 지정 변환) func 표시

### rows 컬럼

- 실행 계획의 효율성 판단을 위해 예측했던 레코드 건수
- 쿼리를 위해 몇 건의 레코드를 읽고 확인해야 하는지를 예측한 수치

### filtered

- rows에 나타난 레코드 수 중, 필터링 되어 살아남은 레코드 비율(%)

## Extra 컬럼

- 내부 처리 알고리즘에 대한 부연설명

### const row not found

- const 접근 방법으로 처리를 시도 했지만 row가 1건도 없는 경우

### Deleting all rows

- WHERE 조건 없는 DELETE 구문 실행계획 확인 시 노출
- 8.x부터 표시 X

### Distinct

- SELECT 구문에서 DISTINCT 사용 시 꼭 필요한 row만 효율적으로 읽었을 때 표시

### FirstMatch

- 기준 테이블에서 첫 번째로 일치하는 한건만을 검색 했음을 표시

### Full scan on NULL key

- `column IN (SELECT ... FROM ...)` 형태의 쿼리에서 발생
  - column이 NULL인 경우 서브 쿼리 테이블 풀 스캔 발생할 수 있음
  - column이 NULL이 될 수 없는 케이스라면 명시적으로 `column IS NOT NULL` 을 WHERE 조건에 추가하면 됨

### Impossible HAVING

- HAVING 조건이 만족될 수 없는 경우 나타남

### Impossible WHERE

- WHERE 조건이 FALSE가 될 수 밖에 없는 경우

### LooseScan

- 루스 스캔이 발생한 경우

### No matching min/max row

- min(), max()가 사용된 쿼리에 레코드가 한건도 조회되지 않을 경우 발생

### no matching row in const table

- const 방식으로 접근하였지만 일치하는 row가 없는 경우

### No matching rows after partition pruning

- 파티션된 테이블을 대상으로 UPDATE, DELETE 실행 시 대상 레코드가 한건도 없을 경우 표시
  - 단순히 레코드가 없는 것이 아니라 파티션이 존재하지 않음을 표시

### No tables used

- FROM 절이 없거나 `FROM DUAL` 로 쿼리한 경우

### Not exists

- Outer join 조건을 활용하여 안티 조인 하는 경우 노출

### Plan isn't ready yet

- `EXPLAIN FOR CONNECTION` 명령어를 통해 옵티마이저가 올바른 실행 계획을 세웠는지 확인할 수 있음
  - ex) `EXPLAIN FOR CONNECTION 8`
- 커넥션에서 실행 계획을 수립하지 못한 경우 `Plan isn't ready yet` 표시

### Range checked for each record(index map: N)

- 레코드마다 인덱스 레인지 스캔을 수행
- 다음과 같은 쿼리에서 발생할 수 있음

```sql
EXPLAIN
SELECT *
FROM employees e1, employees e2
WHERE e2.emp_no >= e1.emp_no
```

### Recursive

- 8.0부터 재귀 쿼리 사용 가능
  - CTE (Common Table Expression) 사용 시 표시 됨

### Rematerialize

- LATERAL JOIN 실행 시 선행 테이블의 레코드별로 서브쿼리를 실행하여 임시 테이블에 결과를 저장하는 것

### Select tables optimized away

- 인덱스가 존재하는 컬럼에 MIN(), MAX()가 사용될 때
- 오름차순, 내림차순으로 1건만 조회되는 경우

### Start temporary, End temporary

- Duplicate Weed-out 최적화가 적용된 것
  - 서브 쿼리 최적화를 위해 임시 테이블을 사용
- 실행 계획을 조회 하면 처음 읽어들인 테이블 로우에 Start temporary, 마지막으로 읽은 테이블 로우에 End temporary 표시

### unique row not found

- 두개의 테이블이 유니크 컬럼으로 아우터 조인 될 때, 일치하는 레코드가 존재하지 않는 경우

### Using filesort

- ORDER BY가 수행 될 때, 인덱스를 사용하지 못하는 경우 표시
- 테이블을 소트 메모리 버퍼에 복사하여 정렬 수행

### Using index (커버링 인덱스)

- 인덱스만 읽어서 모두 처리할 수 있을 때

### Using index condition

- 인덱스 컨디션 푸시 다운이 적용된 경우

### Using index for group-by

- GROUP BY 수행 시 인덱스를 활용한 경우

### Using index for skip scan

- 인덱스 스킵 스캔이 사용된 경우

### Using join buffer(Block Nested Loop), Using join buffer(Batched Key Access), Using join buffer(hash join)

- 두 테이블 조인 시 드리븐 테이블의 조인 컬럼에 인덱스 설정이 되어 있지 않은 경우

### Using sort_union, Using union, Using intersect

- index_merge가 수행된 경우, 어떤 방식으로 두 결과를 병합했는지를 표시

### Using temporary

- 쿼리를 처리하는 동안 중간 결과를 임시 테이블에 저장하고 사용한 경우
- 임시테이블은 메모리 또는 디스크에 만들어진다.

### Using where

- 스토리지 엔진을 통해 데이터를 읽어온 후 MySQL 엔진 레벨에서 추가 필터링, 가공을 한 경우 표시

### Zero limit

- 데이터 값이 아닌 결과 값의 메타데이터만 읽고 싶을 때 쿼리에 `LIMIT 0` 을 포함시킬 수 있는데, 이 방식으로 쿼리를 수행한 경우 표시된다.
