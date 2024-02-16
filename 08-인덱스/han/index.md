- 책의 [색인](https://crear.kr/%EC%9B%B9%EC%97%90-%EB%8C%80%ED%95%9C-%EC%A7%80%EC%8B%9D-%EC%83%89%EC%9D%B8-index-%EC%9D%B8%EB%8D%B1%EC%8A%A4/)
- 컬럼 값과 해당 레코드가 저장된 주소를 key-value 형태로 만들어놓은 데이터를 의미

> 특징

- 항상 정렬된 상태를 유지한다

> 장단점

- 데이터가 저장될 때 마다, 정렬해야하므로 저장하는 과정은 복잡하고 느림 (단점)
- 그렇지만, 정렬되어 있으므로 원하는 값을 굉장히 빠르게 찾아올 수 있음 (장점)

> 결론

- 데이터 저장 (INSERT, UPDATE, DELETE) 성능을 희생하고, 그 대신 읽기 속도를 높이는 기능

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.2 인덱스란?