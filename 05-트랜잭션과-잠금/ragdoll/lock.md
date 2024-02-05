- MySQL의 잠금은 `MySQL 엔진 레벨의 잠금` / `스토리지 엔진 레벨의 잠금`
  - MySQL 엔진 레벨 잠금은 다른 스토리지 엔진 레벨의 잠금에 영향을 준다.
- MySQL 엔진 잠금
  - 글로벌 락
  - 테이블 락
  - 메타데이터 락
  - 네임드 락
- Storage Engine 잠금 (InnoDB)
  - Record Lock
  - Gap Lock
  - Next key Lock
  - Auto increment Lock

## MySQL 엔진 잠금

### Global Lock

- 해당 락을 잡으면 다른 세션에서는 SELECT 외에 다른 액션은 수행이 불가하다.
- 설정에 따라 mysqldump를 사용할 때 걸리기도 하므로, 실행 전 확인을 권장함

```sql
> FLUSH TABLES WITH READ LOCK
```

### Table Lock

- 테이블 단위로 잠금이 수행되는 것
- InnoDB는 DDL의 경우 영향을 받지만, DML은 대부분 가능

### Named Lock

- 임의의 문자열에 잠금을 설정하는 것
  - GET_LOCK()
- 여러 서버간에 동기화 메커니즘이 필요한 경우 활용할 수 있다.

### Metadata Lock

- 테이블 구조를 변경 시 획득하는 잠금
- 묵시적 락이며 명시적으로 획득, 해제는 불가하다.

---

## InnoDB 스토리지 엔진 잠금

> [!NOTE] InnoDB Storage Engine Lock
>
> - InnoDB는 레코드 기반의 락 기능을 제공
> - 레코드와 레코드 사이를 잠그는 Gap Lock 제공

### Record Lock

- 레코드 자체에 잠금을 설정하는 것
- 데이터 전체가 아니라 인덱스에만 잠금을 설정한다.

### Gap Lock

- 레코드와 레코드 사이를 잠그는 것
- INSERT 가 발생했을 때, 저장 될 위치를 선점할 때 사용
- Next key Lock의 일부

### Next key Lock

- Record Lock + Gap Lock
- Bin log에 기록된 쿼리가 레플리카, 소스 서버 모두 동일하게 적용됨을 보장하기 위해 사용 됨
  - ... 🤔 (?)

### Auto increment Lock

- AUTO_INCREMENT 값을 인덱스로 사용하는 경우, 여러 레코드가 INSERT 될 때 동시성 문제를 해결하기 위해 사용
- 테이블 수준의 잠금
- AUTO_INCREMENT 값을 가져올 때만 잠금이 발생하며, 데이터 INSERT 과정까지 지속되는 것은 아니다.

---

## 인덱스와 락의 관계

- InnoDB의 잠금은 인덱스를 잠그는 방식
  - 변경 될 레코드를 찾는 과정에서 검색된 모든 인덱스를 잠금

```sql
-- CREATE TABEL employees (
--    first_name VARCHAR(30) NOT NULL,
--    last_name VARCHAR(10) NOT NULL,
--      ...
--    INDEX `idx_firstname` ON `first_name`
-- ) ENGINE = InnoDB;

> UPDATE employees SET hire_date() WHERE first_name = 'ragdoll' AND last_name = 'kim'

-- first_name에만 인덱스가 걸려있고, last_name에는 인덱스가 없으므로
-- frist_name = 'ragdoll' 을 만족하는 모든 레코드가 잠긴다.
```
