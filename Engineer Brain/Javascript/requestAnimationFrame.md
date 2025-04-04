### Define
- Javascript 애니메이션 코드를 1프레임마다 실행시켜주는 함수.
- Event Loop 내부의 Queue 중 Animation Frame Queue에서 동작함.
	- Task Queue 내부에서 동작할 경우, Queue 내부의 다른 Task로 인해 애니메이션이 밀릴 수 있음.
		- 타이밍이 밀려 애니메이션이 연달아 실행될 시 프레임이 깎여나가게 됨.
	- 또한, 애니메이션은 화면 재생률에 따라 재생되야 하는데, setTimeout을 사용하면 이 점을 고려할 수 없음.

### How it Works
- 함수 실행시 Event Loop 내 별도 공간에 존재하는 Animation Queue에 콜백 함수 삽입.
- Animation Queue에 함수 진입 시, 해당 함수가 페이지의 Repaint 실행 주기에 맞춰 실행.
	- 반복 실행이 아님. 함수 내에서 콜백 형태로 재실행해야 함.
	- 화면의 재생률(60hz, 120hz 등)에 따라서 실행 주기가 맞춰짐.

### Issues
1. Animation Queue 자체가 렌더링 작업 중 styling 직전에 위치하기 때문에, requestAnimationFrame를 통해 중복 코드를 집어넣어 애니메이션을 구현하려 한다면 실제로는 마지막 코드만 스타일로써 적용되게 됨
```js
const block = document.querySelector('div.block');
requestAnimationFrame(() => {
	// block.style.transform = 'translateX(1000px)';
	// block.style.transition = 'all 1s';
	// block.style.transform = 'translateX(100px)'; 
	// 실제로는 렌더링 시 위 한줄만 적용됨
![[스크린샷 2025-01-15 오전 12.38.12.png]]
	// 아래 코드로 해결할 수 있음
	block.style.transform = 'translateX(1000px)';
	block.style.transition = 'all 1s';
	
	getComputedStyle(block).transform 
	// 요소의 속성을 가져오는 코드. 렌더링을 강제하는 속성이 있음
	// 다만 성능상 문제가 있다고 함
	block.style.transform = 'translateX(100px)';
	
	requestAnimationFrame(() => {
		requestAnimationFrame(() => {
			block.style.transform = 'translateX(100px)'; 
		})
	})
	// 이건 왜 이렇게 해야 하는지 아직 모르겠음
	// GPT한테 물어보는게 좋을 듯
})
```

### References
- https://jaeano.tistory.com/entry/Javascript-애니메이션-requestAnimationFrame
- https://developer.mozilla.org/ko/docs/Web/API/Window/requestAnimationFrame
- https://www.youtube.com/watch?v=cCOL7MC4Pl0 (Youtube)