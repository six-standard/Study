# 한국어
## ㄱ
## ㄴ
## ㄷ
### 동시성
- 동시에 처리되는 것처럼 **보이게** 하는 것
- Javascript와 같은 싱글 스레드 언어에서 여러 작업을 동시에 처리해야 할 때 사용하는 개념
- 한 코어 내부에서 여러 작업을 번갈아가며 처리함

### 디자인 패턴


### 다형성
- 한 클래스가 여러 얼굴을 가지는 것 (참고로 얼굴은 여러 개일 수 없음)
- Java의 데이터타입에는 클래스를 지정하거나, 클래스의 인터페이스를 지정할수도 있음
- Java는 Aable, Bable이라는 인터페이스를 사용하는 AB 클래스를 인스턴스로 만들 때 타입 지정 가능
- 이 때 Aable을 지정하면 Bable의 메서드들은 감춰지게 됨 (Aable의 메서드만 사용 가능)
- 반대 경우에서도 Bable의 메서드만 사용 가능하게 됨.
- 자세한건 [이 블로그 글](https://velog.io/@dangdang/Java-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4Interface%EC%99%80-%EB%8B%A4%ED%98%95%EC%84%B1Polymorphism#%EB%8B%A4%ED%98%95%EC%84%B1polymorphism)의 **다형성** 항목 참고

## ㄹ
## ㅁ
## ㅂ
### 병렬성
- 여러 작업을 **실제로** 동시에 처리하는 것
- Java와 같은 멀티 스레드 언어들이 여러 작업을 동시에 처리해야 할 때 사용하는 개념
- 물리적으로 여러 코어들이 모여서 병렬적으로 작업을 처리함
## ㅅ
## ㅇ
## ㅈ
## ㅊ
## ㅋ
## ㅌ
## ㅍ
## ㅎ
# English
## A
### Authentication
- 한국어로는 **"인증"**
- 클라이언트가 실제로 특정 유저인지 확인하는 과정
### Authorization
- 한국어로는 **"인가"**
- 특정 행위가 유저에게 허가된 작업인지 확인하는 작업
## B
## C
## D
### Deserialization
- 한국어로는 **"역직렬화"**, **"parsing(파싱)"**
- 특정 용도로 사용하기 위해 직렬화된 값을 원래 형식으로 변환하는 것
- Javascript로 따지자면, JSON.parse가 역직렬화이다 (JSON 문자열 => JS 객체)
### Data Injection (DI)
- 한국어로는 "의존성 주입"
- 하나의 객체에 다른 객체의 의존성을 제공하는 기술
- 특정 객체의 관리 주체가 특정 객체가 필요한 클래스가 아닌, 해당 클래스를 사용하는 외부 클래스
```js
const target = (object) => {
	console.log(object.target); // DI!
}

const object = { target: "DI!" }
target(object)
```
## E
## F
## G
### Glue Code
- 서로 다른 언어를 접착시켜 사용하기 위해 사용하는 코드
- 다른 언어로 된 코드를 Emscripten을 통해 웹 어셈블리 코드로 변환시키면 나오는 js 코드가 대표적인 Glue Code
### H
## I
## J
## K
## L
## M
## N
## O
## P
## Q
## R
## S
### Serialization
- 한국어로는 **"직렬화"**
- 메모리를 디스크에 저장하거나 네트워크 통신에 사용하기 위해 적절한 형식으로 변환하는 것
- Javascript로 따지자면, JSON.stringify가 직렬화이다 (JS 객체 => JSON 문자열)
## T
## U
## V
## W

## X
## Y
## Z


