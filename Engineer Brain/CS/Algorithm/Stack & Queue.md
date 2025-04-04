#자료구조 #선형

![[Algorithm - Stack & Queue 1.png]]

# Define
- **Stack :** 선입선출 형태의 자료구조로, 먼저 들어온 값이 먼저 나가는 방식 **(LIFO)**
	- 식당에 쌓인 접시를 떠올리면 쉬움 (마지막에 올렸던 접시가 가장 먼저 빠짐)
- **Queue :** 선입후출 형태의 자료구조로, 먼저 들어온 값이 나중에 나가는 방식 **(FIFO)**
	- 대기열을 떠올리면 쉬움 (가장 먼저 들어갔던 사람이 가장 먼저 나감)

# Implementation
```js
const array = [];

array.push(1);
array.push(2);
array.push(3);
array.push(1);
array.push(2);
array.push(3);

console.log(array.pop(), array.pop(), array.pop()); // 3 2 1 (Stack)
console.log(array.shift(), array.shift(), array.shift()); // 1 2 3 (Queue)
```

# Representative Problems
- https://www.acmicpc.net/problem/10828 (스택)
- https://www.acmicpc.net/problem/10845 (큐)

# Reference
- https://velog.io/@sisofiy626/자료구조-2.-스택Stack과-큐Queue-덱Deque