#알고리즘 #최단경로 

![](https://i.imgur.com/EKu1v4e.png)

# Define
- 최단 거리를 구하기 위해 사용하는 알고리즘들 중 하나
- 현재 노드까지의 최단 거리를 재활용하여 다음 노드의 최단 거리를 구함
	- 여기서 효율적인 알고리즘을 위해 짧은 순서대로 탐색할 목적으로, [[Heap|최소 힙]]을 사용하게 됨

# Implementation
```js
// MinHeap 클래스의 구현 과정은 생략

const Dijkstra = (graph, start) => {
  const queue = new MinHeap();
  const answer = new Array(graph.length).fill(Infinity);
  queue.push([start, 0]);
  answer[start] = 0;

  while (queue.length()) {
    const [from, fw] = queue.poll();
    for (let [to, tw] of graph[from]) {
      if (answer[to] > fw + tw) {
		answer[to] = fw + tw;
		queue.push([to, fw + tw]);
	  }
	}
  }
  
  return answer.slice(1).join(" ");
};

const graph = [
[], 
[[2, 2], [3, 3]], 
[[3, 4], [4, 5]], 
[[4, 6]], 
[[1, 1]], 
[]
];

console.log(Dijkstra(graph, 1)); // 0 2 3 7 Infinity
```

# Representative Problems
- https://www.acmicpc.net/problem/1753 (최단 경로)
- https://www.acmicpc.net/problem/1916 (최소 비용 구하기)

# Reference
- https://velog.io/@jmjgirl/Algorithm-다익스트라-Dijkstra-알고리즘