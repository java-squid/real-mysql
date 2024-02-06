- 암호화 키가 관리되는 플러그인
- MySQL 8.0에서는 다양한 플러그인이 제공됨

> 2-Tier 아키텍쳐
- 키 관리 방식
![image](https://velog.velcdn.com/images/code-10/post/017e930d-0c5e-4737-a6bc-dfeac27c46e6/image.png)
- 마스터키(master key) , 테이블 스페이스 키(tablespace key) 2가지 키를 가짐
- HashCorp Valut, 외부 키 관리솔루션
	- 마스터 키를 가져올 때 사용
- [[master-key]] 는 외부에서 가져올 수 있기 때문에, 노출될 가능성이 있음.
	- 그러므로 주기적으로 관리해야함
- 테이블 스페이스키가 private key
- 테이블 스페이스키는 절대 외부로 노출되지 않는다

---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 7.1.1 2단계 키 관리
- https://velog.io/@code-10/%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%95%94%ED%98%B8%ED%99%94