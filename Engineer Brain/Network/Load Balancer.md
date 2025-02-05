![[Network - Load Balancer 1.png]]
### Define
- 여러 개의 서버를 통해 서비스를 운영할 때, 한 대의 서버에 부하가 집중되지 않도록 분산시켜주는 장치
- 보통 서버를 **"scale-out"** 하여 사용하는 경우에 접할 수 있음

### Algorithms
#### Round Robin
- 서버에 요청이 들어올 때마다 서버를 순서대로 배정하는 방식
- 순서대로 분배되기 때문에, 서버가 전부 동일한 성능이며 오래 연결하지 않는 경우 적합
#### Weighted Round Robin
- 서버마다 가중치를 매기고, 가중치가 높은 서버에 요청을 우선 배정하는 방식
- 서버의 성능이 서로 다를 경우에 적합 (성능별로 가중치를 매겨서 요청을 제한하면 되니까)
#### IP Hash
- 클라이언트의 IP 주소를 해싱하여 특정 서버에 매핑하는 방식
- IP 주소 값을 해싱하여 요청을 분배하기 때문에, 사용자들이 항상 원래 접속하던 서버에 접속됨
#### Least Connection
- 요청이 들어온 시점에서 가장 연결 수가 적은 서버에 요청을 배정하는 방식
- 서버에 분배된 트래픽들이 일정하지 않은 경우에 적합
#### Least Response Time
- 요청이 들어온 시점에서 가장 연결 수가 적으며 응답 속도가 빠른 서버에 요청을 배정하는 방식
- 현재 상황에서의 서버 상태를 보고 배정하기 때문에, 적절한 성능을 보장함

### Load Balancing
- 여러 서버에 사용자들의 요청을 분배시켜 특정 서버에 부하가 집중되지 않게 하는 작업
- L4 로드밸런서부터 포트 번호에 접근할 수 있기 때문에, 여러 포트로 서버를 운영할 경우 L4 로드밸런서 이상을 써야 함
#### L4 Load Balancing
<img src="https://post-phinf.pstatic.net/MjAxOTEyMTBfNCAg/MDAxNTc1OTU1MzY3OTM2.nG91HOEOh6Sc1AuUgbN3O4pcnEI-rh24UKSrrrjkrcsg.VcG18MidW4az7Oh0RQfRPLDBHNRyGayE1BsQxDImL3Ig.JPEG/L4-%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%8B%B1.jpg?type=w1200" style="width: 600px; height: auto">
- **"네트워크 계층(또는 트랜스포트 계층)"** 의 정보를 기반으로 요청을 분산함
- IP 주소, 포트번호 등에 따라 트래픽을 나누는 정도의 제한적인 분산만 가능함
- L7 로드밸런서에 비해 가격이 저렴함
- 패킷을 복호화하지 않고, 패킷 정보만 가지고 요청을 분산하기 때문에 속도가 빠르고 효율적이며, 안전함
	- 다만, 패킷을 복호화하지 않기 때문에, 상세한 라우팅은 불가능함
#### L7 Load Balancing
<img src="https://post-phinf.pstatic.net/MjAxOTEyMTBfMjA1/MDAxNTc1OTU1MzgxODY5.odnG4CRES0e5bH7sOKyWRP1c8uO_XC4VX9A3HPeI1JQg.lNL2eJYbMz6NX1e5YFzfHDMQHn4YrdOJR2VYHmq5e1Ig.JPEG/L7-%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%8B%B1.jpg?type=w1200" style="width: 600px; height: auto">
- **"애플리케이션 계층"** 에서 요청을 분산하기 때문에, HTTP 헤더나 쿠키 등의 정보에 따라 분산시킬 수 있음
- 비정상적인 트래픽을 필터링할 수 있어, 보안성이 우수함
- 비교적 상위 계층이기 때문에, 패킷을 통해 상세한 라우팅이 가능함
	- 다만 패킷의 복호화로 인해 더 높은 비용이 지불되게 됨

### References
- https://m.post.naver.com/viewer/postView.nhn?volumeNo=27046347&memberNo=2521903
- https://co-no.tistory.com/entry/네트워크-로드밸런싱