#알고리즘 #그래프 #그래프탐색

![](https://upload.wikimedia.org/wikipedia/commons/5/5d/Breadth-First-Search-Algorithm.gif)

# Define
- 하나의 정점에서 시작하여 인접 노드부터 탐색하는 그래프 탐색 알고리즘
- 보통 최단 거리를 찾을 경우 사용함
	- 가장 인접한 노드부터 시작해서 깊이별로 탐색하기 때문에, 최단 거리로써 활용 가능
	- 애초에 큐에서 나오는 순서대로 가까운 노드임

# Implementation
```js
const BFS = (length, array, start) => {
  const result = [];
  const queue = [start];
  const visited = Array(length).fill(0);

  let head = 0;
  visited[start] = 1;
  
  while (head < queue.length) {
    const current = queue[head++];
    
    array[current].forEach((item) => {
      if (!visited[item]) {
        visited[item]++;
        result.push(item);
        queue.push(item);
      }
    });
  }
  
  return result;
};

const graph = [[2, 3], [0, 2], [0, 3, 4], [1], []];
console.log(BFS(5, graph, 0)); // [ 2, 3, 4, 1 ]
```

# Representative Problems
- https://www.acmicpc.net/problem/1260 (DFS와 BFS)
- https://www.acmicpc.net/problem/2178 (미로 탐색)
- https://www.acmicpc.net/problem/13913 (숨바꼭질 4)

# Reference
- https://gmlwjd9405.github.io/2018/08/15/algorithm-bfs.html
- https://won-percent.tistory.com/34