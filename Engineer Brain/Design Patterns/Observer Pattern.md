![면접을 위한 CS 전공지식 노트: 1.1.4 옵저버 패턴](https://thebook.io/img/080326/035_1.jpg)
### Define
- 옵저버(관찰자) 들이 관찰하고 있는 대상의 상태가 변경할 때마다, 대상자는 각 관찰자에게 통지하고, 관찰자들은 알림을 받아 조치하는 행동 패턴
- 보통 일대다(1:N) 의존성을 가지게 되는데, 분산 이벤트 핸들링을 구현할 때 사용함.
- Pub/Sub(발행/구독) 모델로 알려진 경우도 있는 듯?
- 쉽게 이해하려면, Javascript DOM 이벤트 리스너 함수를 생각하면 됨
	- 특정 요소에 이벤트 시의 콜백을 걸 수 있고(관찰), 이벤트가 발상하면 해당 콜백이 실행되며 (통지), 실행된 콜백에 의해 변수의 값이 바뀌거나 로그가 출력됨 (조치)

### Structure
![gof-Observer-pattern](https://blog.kakaocdn.net/dn/GyGdW/btrUMI5U4jc/8Truwi7vIFk71Q2Kndt6g1/img.png)

- ISubject (관찰 대상을 정의하는 인터페이스)
- IObserver (관찰자를 정의하는 인터페이스)
- ConcreteSubject (정의된 관찰 대상, 관찰자 리스트를 보유하고 있음)
- Observer N (정의된 관찰자, 여러 개가 될 수 있으며 통지를 받으면 update를 통해 처리 가능)

### Flow![gof-Observer-pattern](https://blog.kakaocdn.net/dn/mnHcc/btrUMPqtH6w/alhACffbMkQ89T8rOKq6t1/img.png)
- 관찰 대상(ConcreteSubject) 의 상태가 바뀌고, 변경 사항을 옵저버에게 통보 (notifyObservers)
- 통보받은 관찰자(Observer) 들은 값을 업데이트하거나, 로그를 출력하는 등 적절히 대응(update)
- 관찰이 끝난 관찰자를 그룹에서 제거(removeObserver), 또는 관찰이 필요한 관찰자가 그룹에 추가 (registerObserver)

### References
- https://inpa.tistory.com/entry/GOF-%F0%9F%92%A0-%EC%98%B5%EC%A0%80%EB%B2%84Observer-%ED%8C%A8%ED%84%B4-%EC%A0%9C%EB%8C%80%EB%A1%9C-%EB%B0%B0%EC%9B%8C%EB%B3%B4%EC%9E%90