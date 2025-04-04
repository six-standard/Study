#알고리즘 #그래프 #그래프탐색 

![](https://upload.wikimedia.org/wikipedia/commons/7/7f/Depth-First-Search.gif)

# Define
- 하나의 정점에서 **가장 깊은 노드까지 탐색한 후**, **다시 되돌아가며 탐색**하는 그래프 탐색 알고리즘
- 보통 완탐이나 

# Implementation
```js
const graph = [[1, 4], [0, 2], [1, 3], [2, 4], [0, 3]];

// 재귀형 DFS
const RecursiveDFS = (graph, start, visited = [], answer = []) => {
  visited[start] = true;
  answer.push(start + 1);

  for (const next of graph[start]) {
    if (!visited[next]) RecursiveDFS(graph, next, visited, answer);
  }
  
  return answer.join(" ");
};

console.log(RecursiveDFS(graph, 0)); // 1 2 3 4 5

// 반복형 DFS (성능이 비교적 더 좋음)
const IterativeDFS = (graph, start) => {
  const visited = new Array(graph.length).fill(false);
  const stack = [start];
  
  const answer = [];
  
  while (stack.length > 0) {
	const node = stack.pop();
	if (!visited[node]) {
	  visited[node] = true;
	  answer.push(node + 1);
    
      // Pop을 통해 FIFO 구조로 동작하기 때문에, 배열의 뒤부터 순회
	  for (let i = graph[node].length - 1; i >= 0; i--) {
		const neighbor = graph[node][i];
		if (!visited[neighbor]) stack.push(neighbor);
	  }
	}
  }
  return answer.join(" ");
};

console.log(IterativeDFS(graph, 0)); // 1 2 3 4 5
```

# Representative Problems
- https://www.acmicpc.net/problem/1260 (DFS와 BFS)
- https://www.acmicpc.net/problem/10451 (순열 사이클)
- https://www.acmicpc.net/problem/2667 (단지 번호 붙이기)

# Reference
- https://olrlobt.tistory.com/35