### Define
- 코드를 컴파일러가 변환할 때 만들어내는 추상화된 트리 구조의 값
- Javascript는 인터프리터 언어이면서도 컴파일러 언어인데, 컴파일러 사용 시 필요한 값
	- 터미널에 코드를 입력하거나, 단순한 파일을 실행할 경우에는 인터프리터로써 동작함
	- 하지만 jsx, typescript 등 일반적인 Javascript의 형태가 아닐 경우, 브라우저에서 불러올 수 있게 일반적인 Javascript로 코드를 변환해야 함

### Babylon (@babel/parser)
- AST 관련 글을 찾아보면 흔히 보이는 Babel의 Javascript Parser
- Javascript의 코드를 AST 형태의 구조로 변환해주는 기능을 제공함

### Prettier & Eslint
- Prettier, ESlint 등의 Code Formatter들은 AST를 통해 규칙에 맞지 않는 코드를 감지하고, 변환함
- 파싱을 통해 동작할 경우, 문자열에 작성된 코드나 잘못된 순서의 코드는 감지가 불가함

### References
- https://wikidocs.net/156283
- https://velog.io/@hbsps/%EC%B6%94%EC%83%81-%EA%B5%AC%EB%AC%B8-%ED%8A%B8%EB%A6%ACAST%EB%9E%80
- https://gyujincho.github.io/2018-06-19/AST-for-JS-devlopers