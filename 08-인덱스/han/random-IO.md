![image](https://parkmuhyeun.github.io/assets/img/blog/woowacourse/idx_1.png)

- 위 사진의 오른쪽가 랜덤 I/O
	- 디스크에 기록하기 위해 디스크 헤드를 **3**번 움직였다.
- 랜덤 I/O 란? 
	- 하드 디스크 드라이브의 원판을 돌려서 읽어야 할 데이터가 저장된 위치로, 디스크 헤더를 이동시킨 다음에 읽는 것
- 디스크의 성능은 디스크 헤더의 위치 이동 없이 얼마나 많은 데이터를 한번에 기록하느냐에 의해 결정됨.
	- 즉 3번이나 움직였으므로, 왼쪽 (순차 I/O) 에 비해 부하가 크다

---
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 8.1.2 랜덤I/O와 순차 I/O
- https://parkmuhyeun.github.io/woowacourse/2023-11-02-Index/