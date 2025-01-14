### Define
- 정렬된 배열 또는 리스트에 적합한 고속 탐색 방법
- 배열의 중앙 값과 찾는 값을 비교하여, 범위를 좁혀 가며 값을 탐색하는 방식

### Principle
<img src="https://blog.kakaocdn.net/dn/G7wHv/btqV0D9Zn52/IrArSq3Au3Qlkd2ja1166k/img.png" style="width: 400px; height: auto; filter:invert(1)">
- 

### Implementation
```js
// loop structure
const binarySearch = (target, array) => {
	let [left, right] = [0, array.length - 1];
	while (left <= right) {
		const middle = Math.floor((left + right) / 2);
		if (target === array[middle]) return array[middle];
		else if (target < array[middle]) right = middle - 1;
		else if (target > array[middle]) left = middle + 1;
	}
	return -1;
};

// recursive structure
const recursiveBinarySearch = (target, array) => {
	let [left, right] = [0, array.length - 1];

	const recursor = (left, right) => {
		const middle = Math.floor((left + right) / 2);
		if (target === array[middle]) return array[middle];
		else if (target < array[middle]) return recursor(left, middle - 1);
		else if (target > array[middle]) return recursor(middle + 1, right);
	};
	
	return recursor(left, right) || -1;
});
```

### References
- https://minhamina.tistory.com/127