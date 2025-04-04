![[Design Patterns - Optimistic Pattern 1.png]]
### Define
- 작업에 대한 응답을 받기 전, 해당 응답이 성공적일 것이라고 가정 **(낙관)** 하고 피드백을 제공하는 방법
- 프론트엔드에서는 Tanstack-Query를 사용한 Optimistic Update가 유명한 방식임

### Implementation
```js
// Without Tanstack-Query
const [data, setData] = useState([]);
const [clicked, setClicked] = useState(false);

const add = (input) => {
	if(clicked) return;
	
	// 함수가 실행되면 이전 데이터를 저장하고, 데이터를 입력된 값으로 변경
	const prev = [...data];
	setData(prev => [...prev, input]);
	setClicked(true);

	// 오류가 발생하면 데이터를 원래대로 교체
	fetch('https://example.com/post')
	  .then(res => { if(!res.ok) throw new Error("Not Success"); })
      .catch(() => setData(prev))
      .finally(() => setClicked(false))
}

// With Tanstack-Query
const client = new Queryclient();

const { mutate } = useMutation({
	mutationFn: () => { /* Any Large Api */ },
	onMutate: async (data) => {
		// 요청이 전송되면 이전 데이터를 저장하고, 데이터를 입력된 값으로 변경
		await client.cancelQueries({ queryKey: ["key"] });
		const prev = client.getQueryData(["key"]);
		client.setQueryData(["key"], (prev) => ({ ...prev, ...data }));
	
		return { prev };
	},
	// 오류가 발생하면 데이터를 원래대로 교체
	onError: (_, __, { prev }) => client.setQueryData(["key"], prev),
	// 요청이 성공하면 쿼리 만료
	onSettled: () => client.invalidateQueries({ queryKey: ["key"] })
}),
```

