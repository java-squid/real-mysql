- [B-tree](https://ko.wikipedia.org/wiki/B_%ED%8A%B8%EB%A6%AC) 를 기반으로 만들어진 [[index]]
	- B(Balanced)
- 가장 일반적으로 사용되는 [[index]] 이다.
- 칼럼 값을 변형하지 않고, 원래의 값을 이용해 인덱싱하는 알고리즘

> B-tree 인덱스 구조
![image](https://junhyunny.github.io/images/db-index-data-structure-3.JPG)

- 트리 구조
- Root node -- Branch node -- leaf node
- left node에는 실제 데이터 레코드를 찾아가기 위한 **주솟값** 이 저장되어 있음
- 데이터 파일의 레코드는 **정렬되어 있지 않고** 임의의 순서로 저장되어 있음

> B-tree의 리프 노드와 테이블 데이터 레코드 [[myisam]]

![image](https://oopy.lazyrockets.com/api/v2/notion/image?src=https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F59a91184-df16-421c-9f40-7f4e45b9c229%2FUntitled.png&blockId=e27cd55f-671c-43ce-bcfe-b0f20e6454fe)
- 레코드 주소는 INSERT 된 순번이거나 데이터 파일 내 위치(Offset)
- 인덱스의 value 값은, 물리적인 주소를 가짐

>  B-Tree의 리프 노드와 테이블 데이터 레코드(InnoDB)

![image](https://oopy.lazyrockets.com/api/v2/notion/image?src=https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Feb58a0f8-87b8-49ed-b582-565f421524c2%2FUntitled.png&blockId=f361b3ec-d16d-40dd-b4eb-944c0ef98833)

- [[primary-key]] 가 [[rowid]]의 역할을 함
- 인덱스의 value값은 논리적인 주소를 가짐.
- 모든 [[secondary-key]] 검색에서 실제 데이터 레코드를 일기 위해서는 반드시 [[primary-key]] 를 거쳐가야함을 의미

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.2 인덱스란?
	- 8.3 B-Tree 인덱스
	- 8.3.1 구조 및 특성
- https://junhyunny.github.io/information/data-structure/db-index-data-structure/
- https://www.refinar.life/real-mysql/2