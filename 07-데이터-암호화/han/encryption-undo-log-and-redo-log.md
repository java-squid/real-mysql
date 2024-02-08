- 테이블 암호화를 적용하더라도, [[undo-log]], [[redo-log]] 는 평문으로 저장
- 왜?
	- 디스크에 저장되는 데이터만 암호화 되고, [[mysql-server]] 의 메모리에 존재하는 데이터는 복호화된 평문으로 관리되기 때문
- 단 mysql 8.0.16부터는 해당 기능을 지원하긴 함

---
## Reference
 - - [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 7.4 언두로그 및 리두 로그 암호화