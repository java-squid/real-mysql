![image](https://hoing.io/storage/2021/11/double_write_buffer_1.png)

- 1번 ->  일단 buffer 공간에 기록해두고,
- 2번 -> 개별로 기록하다가 실패하면?
	- 이때 [[double-writer-buffer]] 를 이용함.
	- 실패하지 않으면 이용하지 않음

> 목적

- 데이터 안전성을 위해 
	- 즉 데이터 무결성을 위해

--- 
## Reference
- [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 4.2.8 Double Write Buffer