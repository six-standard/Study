### Define
- 메모리 절약 등 최적화를 위해, 인스턴스 필요 시 새로 만들지 않고, 기존 인스턴스를 불러오는 행동 패턴
- 전역 변수를 통해 고정적인 인스턴스를 생성하고, 필요할 때마다 불러오게 하는 단순한 방식임
- 데이터베이스 연결, 데이터 로깅 함수, (클라이언트 한정) API 인스턴스 등이 보통 싱글톤으로 생성됨

### Implementation Type
- Eager Initialization
- Static block initialization
- Lazy initialization
- Thread safe initialization
- Double-Checked Locking
- Bill Pugh Solution
- Enum
- 아직 자바를 안 써서 그냥 이름만 적어둠.
	- 죄다 자바 기반 설명이라, 내가 뭘 하질 못함

### Bad side
- 메모리 절약, 사용의 간편함 등 다양한 장점만큼 문제도 많음
- 모듈 의존성 증가
	- 여러 모듈이 특정 싱글톤 함수를 참조하게 될 경우, 수정시 애로사항이 생김
	- 한 모듈만을 위해 싱글톤 함수를 수정할 경우, 다른 모듈들에게도 수정이 필요해짐.
- SOLID 원칙 위배 (자바)
	- 혼자 여러 책임을 지며 단일 책임 원칙 위반 (SRP)
	- 혼자 너무 많은 일을 하거나, 데이터를 너무 많이 공유시키며 개방-폐쇄 원칙 위반 (OCP)
	- 인터페이스가 아닌, 실제 구현체를 의존하게 되며 의존 역전 원칙 위반 (DIP)
- 특정 방식에서의 싱글톤 보장 불가
	- Lazy initialization 방식을 사용할 경우, 멀티 스레드 환경에서의 싱글톤 보장이 불가함
	- A번 스레드가 인스턴스 생성 코드를 읽는 상황에서 B번 스레드가 if문을 읽을 경우, 인스턴스가 없는 꼴
	- 당연히 인스턴스는 두 번 초기화되게 됨. (그럼 싱글톤이 아니게 되는거임)
	- 물론 갓갓 싱글스레드 Javascript에서는 큰 문제가 없음
- 단위 테스트의 어려움
	- 이 부분은 진짜 이해를 못 하겠다. (대충 의존성이 너무 심해서 생기는 문제로 보이긴 하는데.. 모르겠음)

### Post Script
- 나도 백엔드 할 걸... 프론트도 이런 원칙같은거 많으면 좋겠다... 뭐라는지 하나도 모르겠네;;
- 레퍼런스중 두 번째 글의 "테스트하기 어렵다." 부분이 도통 이해가 안 간다. 다시 공부하는게 좋을듯

### References
- https://inpa.tistory.com/entry/GOF-%F0%9F%92%A0-%EC%8B%B1%EA%B8%80%ED%86%A4Singleton-%ED%8C%A8%ED%84%B4-%EA%BC%BC%EA%BC%BC%ED%95%98%EA%B2%8C-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90#%EC%8B%B1%EA%B8%80%ED%86%A4%EC%9D%98_%EB%AC%B8%EC%A0%9C%EC%A0%90
- https://velog.io/@backfox/%EC%8B%B1%EA%B8%80%ED%86%A4-%ED%8C%A8%ED%84%B4%EC%9D%84-%EA%B2%BD%EA%B3%84%ED%95%98%EB%8A%94-%EC%82%AC%EB%9E%8C%EB%93%A4%EC%9D%98-%EC%9D%B4%EC%95%BC%EA%B8%B0#3-%ED%85%8C%EC%8A%A4%ED%8A%B8%ED%95%98%EA%B8%B0-%EC%96%B4%EB%A0%B5%EB%8B%A4