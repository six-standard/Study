### Define
- 과거부터 리눅스에서 여러 파일을 검색할 때 사용하던 패턴 매칭 기법
- 과거부터 사용되던 기법이자, 활용성이 높은 기법이다 보니 다양한 곳에서 사용됨
	- VSC의 파일 검색 시스템에서도 특정 파일을 필터링하기 위해 사용됨
	- .gitignore의 파일 필터링에서도 사용됨

### Wildcards
- **?**
	- 문자와 상관없이 정확히 한 글자와 매칭되는 기호
	- 'abc.def', 'aaa.bbb', 'abc.abc'에서 **'?bc.???'** 는 'abc.def', 'abc.abc'를 찾아줌
- **\***
	- 길이와 상관 없는 어떤 문자열이든 매칭되는 기호
	- a로 시작하는 (첫 글자가 a인) 이름을 가진 파일을 찾으려면  **'a*'** 로 찾을 수 있음
- **\*\***
	- 모든 하위 디렉토리들과 매칭되는 기호
	- 'foo 폴더 아래의 모든 파일을 찾으려면  **'foo/\*\*/\*'** 로 찾을 수 있음
- **{}**
	- 동시에 여러 문자열을 검색할 수 있게 해주는 기호
	- js 또는 jsx 확장자를 가진 파일을 찾으려면 **'\*.{js,jsx}'** 로 찾을 수 있음
- **\[\]**
	- 특정 문자를 범위로써 매칭할 수 있게 해주는 기호
	- 대문자로 시작되는 이름을 가진 파일을 찾으려면 **'\[A-Z]\*'** 로 찾을 수 있음
- **()**
	- \* 기호나 ? 기호 바로 뒤에 붙여 선택지 제한을 제공해줄 수 있는 기호
	- 위에서 **{}** 기호로 js파일을 찾던 패턴을 **'\*.js?(x)'** 로 줄일 수 있음 (읽기엔 그닥..)

### References
- https://www.daleseo.com/glob-patterns/