![](https://snowdeer.github.io/assets/common-sense/001.png)
## NAT
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Ft7xLO%2FbtrfqCwSPvi%2FL9HhWJ8OtMQMiN8ey23JP0%2Fimg.png)
Network Address Translation(이하 NAT)는 공인 IP의 고갈 현상을 해결하기 위한 기술.

라우터, 공유기 등 중앙 장비를 기준으로 여러 기기를 연결하여 사설 IP를 가진 내부망을 생성하고, 중앙 장비에 인터넷을 연결한 뒤 패킷이 들어오면 시작점 또는 도착점만 바꿔 하나의 공인 IP로도 여러 기기가 통신할 수 있게 해주는 기술임.
### 문제점
여러 호스트가 서로 겹치지 않고 인터넷을 사용하는 것은 가능하나, 동시에 인터넷을 사용하는것은 불가능함.
만약 두 개 이상의 기기가 같은 포트로 패킷을 전송했을 경우에, 어디에 데이터를 전송해야 할 지 알 수 없기 때문
## NAPT
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcDiQPP%2Fbtrfn3v1kER%2FSUvkzdWH5OKnPUp9gtFGD1%2Fimg.png)
Network Address Port Translation (이하 NAPT)는 NAT 기술을 더 발전시킨 기술로, 포트가 같은 호스트가 두 개 이상이어도 한 번에 인터넷을 사용할 수 있게 해주는 기술.

패킷을 수신하면 해당 패킷의 포트 주소를 임의로 바꾼 뒤 전송하고, 해당 주소와 변환 전 포트, 변환 후 포트를 테이블에 저장함으로써 포트가 겹치는 문제가 생기지 않게 해줌.

(그리고 이런 기능으로 인해 변환되지 않은 포트로는 접근이 되지 않는다는, 보안에서의 장점이 있다고는 하지만 조금 이해하기 어려움)
### 정적 NAPT
만약 외부에서 접속을 허용하고 싶은 내부 장비가 있을 경우에도, NAPT에서는 테이블에 저장된 값만 변환할 수 있기 때문에 외부에서 접속할 수 없음.
이는 수동으로 변환 결과를 저장하는 **"정적 NAPT"** 를 사용하여 해결할 수 있음. 
(포트포워딩, DMZ 등이 정적 NAPT에 해당됨)
### 문제점
만약 FTP와 같이 데이터 부분에 IP와 포트 번호를 저장해야 하는 프로토콜을 사용할 경우, NATP는 IP 헤더의 IP와 포트만 변경하기 때문에 잘못된 주소 사용으로 인해 오류가 발생하게 됨.
이는 라우터에서 자체적으로 대응하는 방법밖에 없기 때문에, 특정 프로토콜을 지원하는 라우터를 구매해야 함.
### References
- 하루 3분 네트워크 교실 "네트워크 주소 변환", "NAPT"