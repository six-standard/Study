### Define
- DB에서 상태를 변경시키는 작업의 단위
- ACID 원칙에 기반하여 동작함

### ACID
#### Atomicity
- 트랜잭션이 DB에 전부 반영되거나, 아얘 반영되지 말아야 함 (누락 불가)
#### Consistenty
- 작업 처리 결과가 항상 일관적이어야 함
- 예를 들어, 송금 트랜잭션 진행 시 타입이 갑자기 integer로 바뀌는 등의 작업 불가
#### Isolation
- 둘 이상의 트랜잭션이 동시에 동작중일 경우에 다른 트랜잭션의 연산에 끼어들지 말아야 함
#### Durability
- 트랜잭션이 성공적으로 진행됬을 때, 그 결과는 영구적으로 유지되어야 함.
### Isolation Level
- 트랜잭션의 독립적인 수준을 위해 트랜젝션을 서로 격리시키는 수준
- Locking을 통해 트랜잭션 진행 중에는 다른 트랜젝션의 접근을 막을 수도 있겠으나, 성능상 하자가 생김
  이를 효율적으로 해결하기 위해 방법이 트랜잭션 격리
#### READ UNCOMMITTED
![](https://velog.velcdn.com/images/shasha/post/27f8fb66-9f8c-4a16-a787-7715fb18ca38/image.png)
- 데이터가 커밋되지 않고 업데이트되기만 해도 다른 트랜잭션에서 읽을 수 있는 방식
- 정합성에 문제가 큰 방식이기 때문에 최근에는 안 쓰인다고 함
#### READ COMMITTED
![](https://velog.velcdn.com/images/shasha/post/554cb0be-e1ed-485f-bbc2-0d4b1c443d59/image.png)
- 데이터를 undo 공간에 백업해두고 사용하는 방식
- Undo 데이터는 일정 시간 이후 제거되며, 서로 다른 트랜잭션에서 커밋된 내용이 반영됨
	- 커밋이 진행되기 전과 후로 결과가 상이한, 일관성이 깨지는 상황 발생 (Non-Repeatable)
#### REPEATABLE READ
![](https://velog.velcdn.com/images/shasha/post/ef8e2c47-e3f3-4eb5-8033-1a61d8fabc9e/image.png)
- 데이터를 Undo 공간에 백업해두고 사용하는 방식
- Undo 데이터는 일정 시간 이후 제거되며, 서로 다른 트랜잭션에서 커밋된 내용이 반영되지 않음
	- Phantom Read라는 문제가 있다고 함 (이해는 안 가서, 나중에 알아봐야 할 듯)
#### SERIALIZABLE
- 어떤 트랜잭션이 작업중일 경우 다른 트랜잭션의 작업을 중단하는 방식
- 그냥 Lock 방식으로, 거의 대부분의 문제가 발생하지 않지만 성능이 매우 낮음

### Reference
- https://velog.io/@shasha/Database-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%A0%95%EB%A6%AC