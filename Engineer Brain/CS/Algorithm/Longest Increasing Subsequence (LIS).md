### Define
- 원소가 n개인 배열의 일부를 선택해 만든 부분 수열 중, 각 원소가 이전 원소보다 크며 길이가 가장 긴 부분 수열
- `{6, 2, 5, 1, 7, 4, 8, 3}`이라는 순열이 있을 때, LIS는 `{2, 5, 7, 8}`이 됨

### DP
```js
for (int k = 0; k < n; k++){
	length[k] = 1;
    for (int i = 0; i < k; i++){
        if(arr[i] < arr[k]){
            length[k] = max(length[k], length[i] + 1);
        }
    }
}
```

### Binary Search
<img src="https://i.imgur.com/tPAmqre.png" style="width: 400px; height: auto; filter:invert(1)">

```js
function solution([length], items) {
	let arr = [items[0]];

	const binarySearch = (target, array) => {
		let [left, right] = [0, array.length - 1];

	    while (left <= right) {
		    const middle = Math.floor((left + right) / 2);
		    if (target < array[middle]) right = middle - 1;
		    else if (target > array[middle]) left = middle + 1;
		}
	    return left;
	};

	for (let i = 1; i < length; i++) {
	    if (items[i] > arr[i - 1]) arr.push(items[i]);
	    else arr[binarySearch(items[i], arr)] = items[i];
	}
	return arr.length;
}
```