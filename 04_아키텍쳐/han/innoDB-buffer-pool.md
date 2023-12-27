- [[innoDB]] 의 가장 핵심적인 부분
- 디스크의 데이터 파일, 인덱스 정보를 메모리에 캐시 해두는 공간
	- 데이터베이스 성능향상 목적
- 쓰기 작업을 지연시켜 일괄 작업으로 처리할 수 있게 해주는 버퍼 역할도 같이한다.
- [[clean-page]], [[dirty-page]] 를 가지고 있음.

> buffer pool 크기 설정
- 버퍼 풀을 크게 변경하는 작업은 시스템 영향도가 그리 크지 않지만, 버퍼 풀을 줄이는 작업은 서비스의 영향도가 매우 크다 (주의)
### 구조
- 3개의 리스트 자료구조
	- LRU(least recently used)
	- Flush
	- Free
![image](https://dev.mysql.com/doc/refman/8.0/en/images/innodb-buffer-pool-list.png)
- Old sublist -> LRU(least recently used)
- New sublist -> MRU(Most recently used)

- LRU 목적
	- 디스크로부터 한번 읽어보 페이지를 최대한 오랫동안 버퍼풀 메모리에 유지하도록 하여, 디스크 읽기를 최소화하는 것

---

## Reference
- https://dev.mysql.com/doc/refman/8.0/en/innodb-buffer-pool.html