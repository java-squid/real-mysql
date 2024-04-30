## 쿼리 힌트

- 개발자가 옵티마이저 실행 계획 수립에 관여할 수 있는 방법

### 인덱스 힌트

- STRAIGHT_JOIN
  - SELECT, UPDATE, DELETE 쿼리에서 여러 테이블 조인 시 조인 순서를 고정시키는 기능
    - 보통 드라이빙 테이블로 데이터가 가장 테이블을 채택하나, STRAIGHT_JOIN을 사용하면 변경이 가능
  - FROM 절에 명시된 순서대로 조인 수행
- USE INDEX
  - 특정 테이블의 인덱스를 사용하도록 함
  - 용도에 따른 분류
    - USE INDEX FOR JOIN
      - JOIN 컬럼, 검색 용도
    - USE INDEX FOR ORDER BY
      - ORDER BY 용도로만 사용하게 함
    - USE INDEX FOR GROUP BY
      - GROUP BY 용도로만 사용하게 함
- FORCE INDEX : USE INDEX보다 강제적
- IGNORE INDEX : 인덱스를 사용하지 못하게 함

### 옵티마이저 힌트

- INDEX_MERGE
  - 하나의 테이블에 대해 여러 인덱스를 사용하는 것
  - 여러 인덱스를 통해 레코드를 검색하고 교집합을 반환
- NO_INDEX_MERGE
