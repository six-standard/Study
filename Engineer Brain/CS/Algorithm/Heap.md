#자료구조 #비선형 #이진트리 

![](https://velog.velcdn.com/images/phobos90/post/2cc5209f-5569-43da-b897-8757b0a3d99d/image.png)

# Define
- 완전 이진 트리의 일종으로 우선순위 큐를 위하여 만들어진 자료구조
	- 여러 개의 값들 중에서 최댓값이나 최솟값을 빠르게 찾아내도록 만들어진 자료구조
- 일종의 **반정렬 상태(느슨한 정렬 상태)** 를 유지함
	- 큰 값이 상위 레벨에 있고 작은 값이 하위 레벨에 있다는 정도
	- 간단히 말하면 부모 노드의 키 값이 자식 노드의 키 값보다 항상 크다는(또는 작다는) 뜻
- 중복 값을 허용함 (알아서 입력 순서대로 정렬)

# Implementation
```js
class Heap { // 힙 베이스
  constructor() {
    this.heap = [];
  }

  swap(from, to) {
    [this.heap[from], this.heap[to]] = [this.heap[to], this.heap[from]]
  }

  parent(index) {
    return Math.floor((index - 1) / 2);
  }

  children(index) {
    return [index * 2 + 1, index * 2 + 2];
  }

  length() {
    return this.heap.length;
  }

  push(item) { 
    this.heap.push(item); 
    this.bubbleUp(); 
  } 
  
  poll() { 
    const value = this.heap[0]; 
    if (this.length()) { 
      if (this.length() === 1) this.heap.pop(); 
      else this.heap[0] = this.heap.pop(); 
      this.bubbleDown(); 
      return value; 
    } 
    else return 0; 
  }
}

class MinHeap extends Heap { // 최소 힙
  constructor(heap) {
	super(heap);
  }

  bubbleUp() {
    let index = this.length()-1;

	while(index > 0) {
		const parent = this.parent(index);
		if (this.heap[parent] <= this.heap[index]) break;
		this.swap(index, parent);
		index = parent;
	}
  }

  bubbleDown() {
    let index = 0;

	while(true) {
	  let small = index;
	  const [left, right] = this.children(index);

      if (left < this.length() && this.heap[left] < this.heap[small]) small = left;
      if (right < this.length() && this.heap[right] < this.heap[small]) small = right;

      if(small === index) break;
      this.swap(index, small);
      index = small;
	}
  }
}

class MaxHeap extends Heap { // 최대 힙
  constructor(heap) {
	super(heap);
  }

  bubbleUp() {
    let index = this.length()-1;

	while(index > 0) {
		const parent = this.parent(index);
		if (this.heap[parent] >= this.heap[index]) break;
		this.swap(index, parent);
		index = parent;
	}
  }


  bubbleDown() {
    let index = 0;

	while(true) {
	  let big = index;
	  const [left, right] = this.children(index);

      if (left < this.length() && this.heap[left] > this.heap[big]) big = left;
      if (right < this.length() && this.heap[right] > this.heap[big]) big = right;

      if(small === index) break;
      this.swap(index, small);
      index = small;
	}
  }
}

const min = new MinHeap();

min.push(30);
min.push(20);
min.push(50);

console.log(min.poll(), min.poll(), min.poll()) // 20 30 50
```

# Representative Problems
- https://www.acmicpc.net/problem/11279 (최대 힙)
- https://www.acmicpc.net/problem/1927 (최소 힙)
- https://www.acmicpc.net/problem/11286 (절댓값 힙)

# Reference
- https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html