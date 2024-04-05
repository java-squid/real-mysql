- 해시 조인은 첫번째 레코드를 찾는데 까지 시간이 많이 걸리지만, 최종 레코드를 찾는 데까지 시간이 많이 걸지지 않음
	- [[nested-loop-join]] 은 상대적으로 첫번째 레코드를 찾는 데 시간이 많이 걸리지 않디만, 최종 레코드를 찾는데 많은 시간이 걸림
- 즉 [[hash-join]] 최고 `throughput`  전략에 적합
- [[nested-loop-join]] 최고 응답 속도(Best response-time) 전략에 적합
	- 보통 웹서비스에서는 응답속도가 중요하기 때문에...
	- 분석과 같은 서비스에서는 응답 속도보다는 `throughput` 이 중요

- 빌드 단계(Build-phase)
- 프로브 단계(Probe-phase)

---
## Reference
 -  [Real MySQL 8.0 (1권)](https://product.kyobobook.co.kr/detail/S000001766482)
	- 9.3.1.19 해시조인