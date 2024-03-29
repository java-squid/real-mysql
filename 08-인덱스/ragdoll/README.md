## 디스크 읽기 방식

- 데이터베이스에서의 성능 튜닝은 디스크 I/O를 줄이는 것이 관건
- 디스크 I/O 과정에서는 디스크 헤더를 움직이는 동작이 필요한데, 이것에 의해 처리 속도가 저하된다.
- 즉, 헤더의 이동을 얼마나 최소화 하느냐가 성능에 크게 영향을 준다.

## 순차 I/O

- 디스크 헤더를 움직이지 않고 읽어들이는 방식

### 랜덤 I/O

- 디스크 헤더를 돌려서 데이터에 접근하는 방식
- 순차 I/O보다 시스템 콜이 빈번하다.

---

## 인덱스

- 데이터(컬럼), 주소 값을 key-value 형태로 저장한 것
- 컬럼 값을 주어진 순서대로 미리 정렬하여 보관해서 검색 성능을 향상시킨다.
- Sorted List에 비유될 수 있다.
  - 항상 정렬된 상태를 유지해야 하기 때문에 저장, 삭제, 시 재정렬이 필요하여 처리 리소스가 늘어난다.
  - 그러나 이미 정렬이 되어 있으므로 검색에는 매우 뛰어나다.
  - 즉, C, U, D의 성능을 희생하고 R의 성능을 극대화 한 것이다.

---

### Primary Index

- 하나의 레코드를 대표하는 값. 식별자라 한다.
- NULL과 중복을 허용하지 않는다.

### Secondary Index

- PK를 제외한 나머지 모든 인덱스
- ex. UNIQUE index

### B-Tree

- 인덱스를 저장하는 대표적인 자료구조
- 컬럼의 값을 변환하지 않고 그대로 저장한다는 특징이 있다.

### Hash index algorithm

- 컬럼 값으로 해싱한 뒤 인덱싱하는 알고리즘
- 매우 빠른 검색 속도를 보이지만, 해싱을 거치기 때문에 값의 일부만으로는 검색이 불가하다.

---

## B-Tree 인덱스

- Balanced Tree
- 루트노드, 브랜치노드(루트노드, 리프노드가 아닌 모든 노드), 리프노드로 구성
  - 리프노드에는 항상 실제 데이터 레코드의 주소 값이 저장되어있다.
- InnoDB 스토리지 엔진은 레코드를 클러스터링 해서 저장한다.
  - 클러스터링이란, 비슷한 것들끼리 최대한 모아서 저장하는 방법을 의미한다.
  - 즉, PK 순서로 정렬되어 순차적으로 저장한다.
- 컬럼, 주소(자식노드 주소 or 데이터 파일에 저장된 레코드 주소)로 구성
- 인덱스는 테이블 키 컬럼만 가지고 있으므로 나머지 데이터를 위해서는 데이터 파일까지 접근해야 한다.
- InnoDB 스토리지 엔진에서는 테이블 레코드를 읽기 위해 반드시 프라이머리 키 인덱스를 한번 더 검색해서 접근한다.
- 쓰기 비용이 크다.
  - 레코드가 추가되면 저장 될 자리(리프노드)를 찾는다.
    - 리프 노드가 꽉 차는 경우 분리되는 작업이 필요하다.
      - 상위 브랜치 노드까지 작업 범위가 미치게 된다.
      - 이로 인해 쓰기 비용이 상대적으로 크다.
- 수정 비용도 크다.
  - 인덱스는 항상 정렬된 상태를 유지해야 하기 때문에, 키가 수정되는 경우 재정렬이 발생한다.
  - B-Tree는 값을 직접 수정하지 않고, 변경될 값을 삭제한 뒤 새로운 값을 삽입하는 방식으로 동작한다.
- DELETE 비용은 상대적으로 작다.
  - 삭제 될 리프노드에 마킹을한다.
    - 그러나 마킹작업 또한 디스크 I/O를 수반한다.
  - 마킹 된 리프노드는 방치되거나 재활용한다.
- 인덱스 키 값을 변경하면 아래의 순서로 동작한다.
  1.  기존 인덱스 키 값을 삭제
  2.  새로운 위치에 키 값 추가
- InnoDB 스토리지 엔진에서 UPDATE, DELETE 시 갭락, 이후 인덱스를 먼저 잠그고 테이블 로우를 잠그는 방식으로 동작한다. 따라서 인덱스가 걸려있지 않은 경우 무수히 많은 테이블 레코드가 잠길 수 있다.
- B-Tree 인덱스의 각 노드는 페이지(블록) 단위이다.
- B-Tree인덱스의 자식 노드 수는 가변이다.
  - InnoDB 스토리지 엔진은 페이지 단위로 데이터를 검색, 처리, 저장한다.
  - 인덱스 키 값의 크기가 모두 다르므로, 한 페이지를 채울 수 있는 개수가 다르다.
- 인덱스 1건을 읽는 비용은 테이블에서 직접 레코드를 읽는 비용의 4 ~ 5배가 든다.
  - 따라서 테이블의 절반 이상을 읽어들이는 쿼리가 실행된다고 하면, 인덱스를 통하는 것보다 테이블을 통해 직접 읽어서 필터링 하는 작업이 더 효율적일 수도 있다.
  - 일반적으로 20% ~ 25%를 성능의 손익분기점으로본다.

### 인덱스 레인지 스캔

- 스캔 할 인덱스의 범위가 정해진 상태
  - 스캔 : 차례대로 쭉 읽는 방식을 의미함
- 인덱스 스캔 이후 찾은 데이터 파일의 주소 값으로 각각 레코드를 불러오는데, 이 과정에서 랜덤 I/O가 발생한다.
- 인덱스 레인지 스캔의 작동 순서를 정리하면 다음과 같다.
  1.  검색 조건으로 인덱스의 시작 지점을 찾는다.
  2.  시작 지점으로부터 쭉 데이터를 읽는다.
  3.  2에서 얻은 키와 주소 값으로 레코드가 저장된 페이지를 조회하고, 최종 레코드를 읽는다.

### 인덱스 풀 스캔

- 인덱스를 처음부터 끝까지 모두 읽는 방식
- 예를 들어 인덱스가 A, B, C 순서대로 걸려 있을 때 B, C만을 조건으로 검색하는 경우 모든 인덱스를 다 읽게 된다.

### 루스 인덱스 스캔

- 일부 인덱스를 스킵하며 듬성듬성 읽는 방식
  - 중간에 불필요한 키 값을 스킵한다.

### 인덱스 스킵 스캔

- MySQL 8.0부터 추가된 기능
- 인덱스 A, B, C가 순서대로 걸려 있는 경우, A를 생략하고 B, C만을 사용해도 루스 인덱스 스캔처럼 작동
- 내부적으로는 A를 WHERE 조건에 넣어서 쿼리를 재작성한 뒤 실행 함
  - 누락된 A의 유니크한 값이 적을 때만 효율적으로 작동이 가능 함
- 실행 계획을 조회 해보면 `Using index for skip scan` 를 확인할 수 있다.

### 복합 컬럼 인덱스

- 선행하는 인덱스 정렬에 이후 인덱스들이 의존하여 정렬 된다.

### 가용성과 효율성

##### 비교 조건의 종류와 효율성

```sql
# INDEX idx (column_1, column_2, column3, ..., column_n)

# 인덱스 사용 불가
> .. WHERE column_1 <> 2

# column_1, column_2까지 범위 결정 조건
> .. WHERE column_1 = 1 AND column_2 > 10

# column1, column_2, column_3 까지 범위 결정 조건
> .. WHERE column_1 IN (1, 2) AND column_2 = 2 AND column_3 <= 10


# column_1, column_2, column_3까지 범위 결정 조건, column_4는 체크 조건
> .. WHERE column_1 = 1 AND column_2 = 2 AND column_3 IN (10, 20, 30) AND column_4 <> 100

# column_1, column_2, column_3, column_4까지 범위 결정 조건으로 사용
> .. WHERE column_1 = 1 AND column_2 IN (2, 4) AND column_3 = 30 AND column_4 LIKE 'column_%'


# column_1, column_2, ... column_5 모두 범위 결정조건으로 사용
> .. WHERE column_1 = 1 AND column_2 = 2 AND column_3 = 3 AND column_4 = 'column_4' AND column_5 = 'column_5'
```

## 전문 검색 인덱스

- 특정 키워드가 포함된 문서를 검색하는데에 사용

### 어근 분석 알고리즘

- 불용어(Stop word), 처리
  - 가치 없는 단어 필터링
- 어근 분석 (Stemming)
  - 단어의 뿌리 (어원)을 찾는 작업

### n-gram 알고리즘

- 키워드 검색을 위한 인덱싱 알고리즘
- 몇 글자 단위로 잘라서 인덱싱

### 멀티 밸류 인덱스

- 원래 인덱스, 데이터는 1:1 관계
- 8.x부터 인덱스, 데이터 N:1 관계가 가능하다.

##### 검색 조건 함수

- 멀티 밸류 인덱스는 다음의 함수를 사용 할 때만 동작한다.
  - MEMBER OF()
  - JSON_CONTAINS()
  - JSON_OVERLAPS()

### 함수 기반 인덱스

- 함수에 의해 변형된 값의 인덱스를 생성하는 방법
- 방법
  - 가상 컬럼
  - 함수
- 동일하게 B-Tree를 사용한다.

##### 가상 컬럼 방식

- 컬럼을 생성하는 방식과 비슷
- 테이블 구조 변경

```sql
ALTER TABLE example
	ADD example_composite_column VARCHAR(30) AS (CONCAT(example_column_1, ' ', example_column_2)) VIRTUAL,
	ADD INDEX `idx_example_composite_column` (example_composite_column)
```

##### 함수 방식

- 테이블 구조 변경 X
- DDL과 WHERE 조건이 같아야 인덱스가 작동한다.

```sql
-- DDL
CREATE TABLE example (
	-- ...
	INDEX idx_example_composite_column ((CONCAT(example_column_1, ' ', example_column_2)))
);

-- USAGE
SELECT * FROM example
WHERE CONCAT(example_column_1, ' ', example_column_2) = 'example'
```

### 클러스터링 인덱스

- PK가 비슷한 데이터끼리 모아서 저장
- PK 값이 바뀌면 저장위치도 바뀌게 된다.
- 리프노드에 레코드의 주소 값(ROW-ID)이 저장되는 세컨더리 인덱스와 다르게 리프노드에 레코드의 모든 값 저장
  - InnoDB는 리프 노드에 프라이머리 인덱스를 저장하고 있다.

##### 세컨더리 인덱스에 미치는 영향

- 클러스터링 인덱스 구조에서는 PK 값이 변경되면 데이터의 물리적 주소가 변경된다.
- 만약 리프노드에 특정 레코드의 주소 값(ROW-ID)를 저장한다면, PK가 변경되면 세컨더리 인덱스도 변경되어야 할 것이다.
- 클러스터링 인덱스에 영향을 받지 않고 오버헤드를 방지하기 위해, 세컨더리 인덱스는 리프노드에 클러스터링 인덱스 값을 저장하고 있다.

### 유니크 인덱스

##### 인덱스 읽기

- 유니크하지 않은 일반 인덱스와 큰 차이가 없다.
  - 유니크하지 않은 인덱스는 중복을 허용하므로 조금 더 많은 레코드를 읽기는 할 것이다.

#### 인덱스 쓰기

- 데이터가 INSERT 될 때 마다 중복 값이 이미 있는지 체크해야 하므로 일반 인덱스보다 쓰기 성능이 느리다.
- 읽기 잠금, 쓰기 잠금을 모두 사용하므로 데드락도 자주 발생한다.
