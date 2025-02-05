### Define
- origin이 서로 다른 공유자끼리 리소스를 공유하려 할 때 발생하는 개념
- 한국어로 보통 **"교차 출처"** 라고 하는 듯

### Origin
- protocol, host, port를 합쳐 만들어진 문자열 `(https:// + google.com + :443)`
- 리소스 공유 시에, 위 셋 중 하나라도 다른 공유자가 있다면 cross-origin이 됨
- 보통 헤더에 기본적으로 포함되는 값임 (이를 검증하기 위한 헤더들(`sec-fetch-mode`등)도 포함됨 )
- window.open() 등으로 새롭게 열린 페이지는 **"상속 출처(inherited-origin)"** 가 적용됨
	- 해당 페이지를 연 페이지의 origin을 상속한다는 규칙

### Same-Origin Policy
- **"브라우저"** 에서만 동작하는 정책으로, origin이 다른 외부의 리소스를 차단하는 정책
	- 사실상 CSRF, XSS 등을 통한 쿠키 탈취를 방지하기 위해 적용되는 정책임
- 최근 들어서 대부분 FE와 BE가 이원화되는 만큼, 여러 방법들을 통해 완화하여 사용함

### Cross-Origin Resource Sharing
- 서로 다른 origin끼리 리소스를 공유할 수 있게 해주는 매커니즘
- Preflight 요청을 통해 요청의 유효성을 확인할 때 사용됨 (이 때 유효하지 않다면 CORS 오류가 뜸..)
- 서버에서 `Access-Control-Allow-Origin`, `Access-Control-Allow-Methods`, `Access-Control-Allow-Headers`등의 헤더를 설정하여 사용할 수 있음
	- `Access-Control-Allow-Origin` : 공유를 허용하는 origin을 설정함
	- `Access-Control-Allow-Methods`: 사용 가능한 method(get, post 등)를 설정함
	- `Access-Control-Expose-Headers`: 사용 가능한 커스텀 헤더를 설정함 (X-로 시작하는 헤더들)
	- `Access-Control-Allow-Credentials`: 요청 credential이 include일 때의 응답 여부를 설정함
		- 해당 헤더가 true일 경우, `Access-Control-Allow-Origin`을 wildcard 로 설정할 수 없음

### CORS Requests
#### Simple Requests
- Preflight 요청 없이 바로 전송되는 요청
- 아래와 같은 조건에서만 Simple Request로 동작함
	- 메서드가 `GET`, `HEAD`, `POST`
	- 헤더 중 `Accept`, `Accept-Language`, `Content-Language`, `Content-Type`만 수동으로 정해짐
	- 헤더 중 `Content-Type`가 `application/x-www-form-urlencoded` 또는 `multipart/form-data`, `text/plain`
#### Preflight Requests
- 실제 요청을 보내기 전에, 현재 요청이 유효한지 확인차 보내는 요청
	- 만약 매우 무거운 요청을 보냈는데, 해당 요청이 유효하지 않다면 리소스를 낭비하게 됨
- OPTION 메서드를 통해 전송되며, 위 헤더와 관련된 헤더만 전송되게 됨
#### Credential Requests
- 일반적인 요청에 쿠키 등 인증 정보를 더해서 보내는 요청
- fetch의 credential 속성에 따르며, 응답 헤더의 `Access-Control-Allow-Credentials`가 true여야 함
	- credential엔 `omit`(완전 차단). `same-origin`(same-origin 외에 차단), `include`(차단 없음)이 들어갈 수 있음.
	- `include`일 경우에는 쿠키의 일부 속성이 설정되어 있어야 인증 정보를 포함할 수 있음

### References
- https://velog.io/@hoo00nn/CORSCross-Origin-Resource-Sharing-란
- https://velog.io/@wjdwl002/CORS의-기본-개념과-동작-방식부제-Preflight-요청이란
- https://dongwooklee96.github.io/post/2021/03/23/sopsame-origin-policy-란-무엇일까.html
- https://woohyun-king.tistory.com/216