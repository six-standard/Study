### Define
- 한국어로는 **"쪼갤 수 없는 배낭 문제"**
- DP를 통해 풀이하는 배낭 문제로, 보통 첫 줄에 각 요소의 중요도와 가중치가 주어진다.

### Principle
![[CS - 0,1 Knapsack 1.png]]
- **배열의 높이(바깥 배열)** 를 **요소의 길이(보통 한 자리 수의 형태)** 로 지정
- 배열의 **너비(내부 배열)** 를 가중치의 **최댓값(보통 2~3 자리 수의 형태)** 으로 지정
- 그 이후, 각 행마다 해당 요소의 중요도를 가중치에 맞게 배정
	- 5열부터 끝 열까지 이전 행과 비교하여 중요도를 배정하면 됨
	- **(이전 행, 현재 열)** 의 중요도 or 현재 입력할 중요도 + **(이전 행, 남은 가중치)** 의 중요도 중 큰 값을 배정

### Implementation
해당 코드는 대표적인 배낭 문제(평범한 배낭) 에 대한 구현이다.
```js
function solution(input) {
  let [[length, max], ...items] = input.split("\n").map((i) => i.split(" ").map(Number));
  [length, max] = [length + 1, max + 1];

  let dp = Array.from({ length }, () => Array.from({ length: max }, () => 0));

  for (let i = 1; i < length; i++) {
    for (let j = 1; j < max; j++) {
      if (j - items[i - 1][0] >= 0) {
        dp[i][j] = Math.max(dp[i - 1][j], items[i - 1][1] + dp[i - 1][j - items[i - 1][0]]);
      } else {
        dp[i][j] = dp[i - 1][j];
      }
    }
  }

  return dp[length - 1][max - 1];
}
```

### Representative Problems
- https://www.acmicpc.net/problem/12865 (평범한 배낭, 골드 5)
- https://www.acmicpc.net/problem/14728 (벼락치기, 골드 5)
- https://www.acmicpc.net/problem/17845 (수강 과목, 골드 5)

### References
- https://hoonni3002.tistory.com/122