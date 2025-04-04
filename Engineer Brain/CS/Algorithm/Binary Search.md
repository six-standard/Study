#알고리즘

![](https://velog.velcdn.com/images/kwontae1313/post/4b6514c9-54b1-425f-afa1-2f167970f5f0/image.png)

# Define
- 정렬된 데이터에서 특정 값을 빠르게 찾아내는 알고리즘
	- Up & Down 방식으로 값을 찾아내기 때문에, 정렬되지 않으면 사용 불가
- **O(N log N)** 의 시간을 가지며, 배열의 길이가 길어질수록 성능이 좋아짐

# Implementation
```js
const Binary_Search = (array, target) => {
  let [left, right] = [0, array.length-1];

  while(left <= right) {
    let middle = Math.floor((left + right) / 2);
    if(array[middle] > target) {
      right = middle - 1;
    } else if (array[middle] < target) {
      left = middle + 1;
    } else { 
      return middle;
    } 
  }
  
  return -1;
}

  

console.log(Binary_Search([5, 8, 10, 15, 20, 25, 30, 40, 50, 54, 66, 69, 83, 86, 90], 66)); // 10
```

# Representative Problems
- https://www.acmicpc.net/problem/1920 (수 찾기)
- https://www.acmicpc.net/problem/10816 (숫자 카드 2)
- https://www.acmicpc.net/problem/1654 (랜선 자르기)

# Reference
- https://jungeunpyun.tistory.com/73
- https://www.acmicpc.net/blog/view/109 (이분탐색에 대한 자세한 설명)