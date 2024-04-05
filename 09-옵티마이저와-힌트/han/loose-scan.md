- [[semi-join]] 최적화 방법
- `Using index for group-by` 와 비슷
- `Extra` 에 `Using index; LooseScan`
- 서브 쿼리 테이블을 읽고, 그 다음으로 아우터 테이블을 드리븐으로 사용해서 조인을 수행
- `SET optimizer_switch='loosescan=off` 하면 비활성화 됨

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.3.1.1.2 루스 스캔