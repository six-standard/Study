### Define
- 한국어로는 **"너비 우선 탐색"**
- 현재 정점과 가장 인접한 정점부터 탐색하는 방식
- queue를 통해 구현되는 방식

### Principle
![](https://velog.velcdn.com/images%2Flucky-korma%2Fpost%2Fe2ef7ac3-14e6-42e7-a768-224c5f773e29%2FR1280x0-3.gif)
- queue를 통해 동작함으로써, 현재 그래프 주변에 존재하는 모든 정점들을 탐색할 수 있게 된다
### Implementation
```js
function BFS(start, points, nodes) {
	let queue = [start];
	let graph = Array.from({length: points.length}, () => []);
	let visited = Array.from({length: points.length}, () => 0);

	nodes.forEach([from, to] => {
		graph[from-1] = to-1;
		graph[to-1] = from-1; 
		// node를 '1 2'와 같은 식으로 표현했다면, 실제 배열 형태에 맞춰 넣어줘야 함
	});
	
	while(queue.length) {
		let node = queue.shift();
		graph[node].forEach(item => {
			if(!visited[item]) {
				visited[item] = 1;
				queue.push(item);
			}
		});
	}
}
```

### References
- https://velog.io/@lucky-korma/DFS-BFS%EC%9D%98-%EC%84%A4%EB%AA%85-%EC%B0%A8%EC%9D%B4%EC%A0%90