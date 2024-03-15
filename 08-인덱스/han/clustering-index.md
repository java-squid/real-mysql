- [[innoDB]] 에서만 지원
- [[primary-key]] 에만 적용되는 내용
	- 즉 [[primary-key]] 값이 비슷한 레코드끼리 묶어서 저장하는 것이 [[clustering-index]]
- [[primary-key]] 값에 의해, [[record]] 저장 위치가 결정
	- 즉 [[primary-key]] 변경되면, 해당 [[record]] 의 물리적인 저장 위치도 변경되어야함.
	- 그러므로 [[primary-key]] 를신중하게 결정

![image](https://velog.velcdn.com/images/claraqn/post/93fa78d9-03cb-4b4f-a2d4-b669f23757ed/image.png)


> 만약에 [[primary-key]] 가 변경된다면?

```sql
UPDATE tb_test SET emp_no = 100002 WHERE emp_no = 100007
```

- [[primary-key]] 가 변경되는 일은 거의 없을 것

![image2](https://velog.velcdn.com/images%2Fjsj3282%2Fpost%2F377b6639-92ad-401d-ac6d-29e9a0bca498%2Fimage.png)

- 3번 페이지에서 2번페이지로 이동
	- **실제 저장 위치가 변경**되었음

> [[primary-key]] 가 없는 [[innoDB]] 테이블은 어떻게 클러스터링 테이블로 구성?

- 우선 순위에 따라, [[primary-key]] 를 대체할 칼럼을 선정
	1. [[primary-key]] 가 있으면 기본적으로 선정됨
	2. `NOT NULL` 옵션의 [[unique-index]] 중에서 첫번째 인덱스
	3. 자동으로 유니크한 값을 가지도록 증가되는 칼럼을 내부적으로 추가한 뒤 선택

> 결론

- [[innoDB]] 테이블에서 [[clustering-index]] 는 테이블 단 하나만 가질 수 있는 혜택.
- 반드시 명시적으로 [[primary-key]] 를 생성해야함.

> 클러스터링 테이블의 모든 [[secondary-index]] 는 해당 [[record]] 가 저장된 주소가 아니라, [[primary-key]] 값을 저장하도록 구현되어 있음.

- 왜?
	- 실제 레코드가 저장된 값을 가지고 있다면,
	- 클러스터링 키 값(`emp_no` ) 이 변경될 떄 마다, 레코드 주소(`page no`) 가 변경되고 
	- 해당 테이블 모든 인덱스의 레코드 값을 변경해야하므로 (오버헤드)

##  장단점

> 장점

1. 성능 매우 빠름 
2. 테이블의 모든 [[secondary-index]] 가 [[primary-key]] 를 가지고 있으므로, 인덱스 만으로 처리될 수 있는 경우가 많음

> 단점

1. 테이블의 모든 [[secondary-index]] 가 [[primary-key]] 를 갖기 때문에, [[primary-key]] 값의 크기가 클 경우, 인덱스의 크기가 증가함
	- [[primary-key]] 의 크기가 커지면, 인덱스 크기 자동 증가됨..
2. [[secondary-index]] 를 통해 검색하려면 다시 [[primary-key]] 로 다시 검색해야 하기 때문에 느림
3. INSERT, UPDATE 성능 좋지 않음

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.8 클러스터링 인덱스
	- 8.8.1 클러스터링 인덱스
	- 8.8.2 세컨더리 인덱스에 미치는 영향
	- 8.8.3 클러스터링 인덱스의 장점과 단점
- https://velog.io/@claraqn/%ED%81%B4%EB%9F%AC%EC%8A%A4%ED%84%B0-%ED%85%8C%EC%9D%B4%EB%B8%94
- https://velog.io/@jsj3282/18.-%ED%81%B4%EB%9F%AC%EC%8A%A4%ED%84%B0%EB%A7%81-%EC%9D%B8%EB%8D%B1%EC%8A%A4