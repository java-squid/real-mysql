- 트랜잭션이 수행될 때, 다른 트랜잭션에서 수행된 데이터 변경에 대한 가시성을 설정하는 것
- 격리 수준이 높을수록 정합성은 높아지며, 반대로 처리 성능은 하락
- 격리 수준에 따라 다음의 문제가 발생할 수 있음
  - DIRTY READ
  - NON-REPEATABLE READ
  - PHANTOM READ

## READ UNCOMITTED

- 다른 트랜잭션의 COMMIT 여부에 상관 없이 변경사항에 대한 가시성이 확보되는 것
- Dirty read 발생
  - 트랜잭션이 완료되지 않았는데 변경 이력을 볼 수 있는 것

## READ COMMITTED

- 다른 트랜잭션에서 COMMIT이 완료된 데이터의 변경사항만 가시성이 확보되는 것
- 언두로그의 데이터를 읽는다.
- Non-Repeatable read 발생
  - 트랜잭션이 완료되지 않았을때는 언두로그로 변경 이전의 데이터를 읽다가Commit 완료 후에는 변경된 데이터가 읽히는 것
- 즉, 같은 트랜잭션 안에서 다른 값이 읽히는 문제는 여전히 존재함

## REPEATABLE READ

- 다른 트랜잭션이 COMMIT 되었더라도, 트랜잭션 시작 시점의 스냅샷을 계속 보여주는 것
  - 언두로그의 값을 보여준다.
- READ COMMITED 언두로그 읽기 방식과의 차이는?
  - InnoDB는 트랜잭션마다 번호를 부여하는데, 현재 실행중인 트랜잭션과 연관된 트랜잭션 번호 이후에 생성된 언두로그는 지우지 않는다.
  - READ COMMITED는 최신의 트랜잭션 번호를 가진 언두로그를 읽는 반면, REPEATABLE READ는 트랜잭션 시작 시 부여받은 번호보다 앞 번호의 언두로그만을 읽는다.
- Phantom read가 발생한다.
  - 다른 트랜잭션에서 변경이 아닌 새로운 레코드를 INSERT 했을 때, 처음 조회 시 결과에 없던 레코드가 읽힐 수 있다.
    1. (Tx 1) SELECT \* FROM member WHERE id > 100
       - 1개의 레코드(ID: 101) 반환
    2. (Tx 2) INSERT INTO member (id) VALUES (102)
    3. (Tx 1) SELECT \* FROM member WHERE id > 100
       - 2개의 레코드(ID: 101, ID: 102) 반환

## SERIALIZABLE

- 가장 엄격한 격리 수준
- 한 트랜잭션에서 읽고 쓰는 레코드에 대해 다른 트랜잭션에서는 접근이 불가함
