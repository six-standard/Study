![](https://velog.velcdn.com/images/dev-redo/post/88e69581-3f14-4479-8bd8-fc289c084e79/image.png)
### Define
- 재귀적으로 문제를 풀어가면서 현재 노드가 조건에 위배되는지 판단, 만약 위배하면 해당 노드를 제외하고 다음 단계로 나아가는 알고리즘
- DFS 기반의 알고리즘임 (재귀적으로 모든 노드를 탐색해야 하니까)
- **가지치기(pruning)** 라고도 함
- ~~위 트리는 그냥 "요기, 요기, 요기, 쫘라락, 요기 쫘라락" 라고 설명하면 쉽게 떠올릴 수 있을 듯...~~

### Implementation
```js
function solution(input) {
	const [n, m] = input.split(" ").map(Number);
	let visited = new Array(n).fill(0);
	let answer = "";
	
	function dfs(depth, array) {
		if (depth === m) {
			answer += array.join(" ") + "\n";
		} else {
			for (let i = 0; i < n; i++) {
				if (!visited[i]) {
					visited[i] = 1;
					dfs(depth + 1, [...array, i + 1]);
					visited[i] = 0;
				}
			}
		}
	}
  
	dfs(0, []);
	
	return answer.trim();
}
```

### Representative Problems
- https://www.acmicpc.net/problem/15649 (N과 M (1), 실버 3)
- https://www.acmicpc.net/problem/15650 (N과 M (2), 실버 3)
- https://www.acmicpc.net/problem/15651 (N과 M (3), 실버 3)
### References
- https://velog.io/@dev-redo/%EB%B0%B1%EC%A4%80-15649%EB%B2%88-N%EA%B3%BC-M1-NodeJS
- https://youngdroidstudy.tistory.com/entry/%EB%B0%B1%ED%8A%B8%EB%9E%98%ED%82%B9-%EB%B0%B1%ED%8A%B8%EB%9E%98%ED%82%B9%EC%9D%98-%EC%84%A4%EB%AA%85%EA%B3%BC-%EA%B0%84%EB%8B%A8%ED%95%9C-%EC%98%88%EC%A0%9C%ED%92%80%EC%9D%B4