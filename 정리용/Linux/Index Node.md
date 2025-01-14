### Define
- 유닉스 계통의 File System 에서 사용하는 자료 구조
- 모든 파일 및 디렉토리에 대한 Index block을 생성하여 관리함
- 여러 메타데이터를 소유하고 있으며, **"Data Block Pointer"** 를 통해 실제 데이터를 가리킴
	- inode number, type, permission, owner, size, timestamp, block count, link number 등
- 이로 인해, 동일한 파일 시스템 내에서 파일을 옮길 경우 디렉토리 엔트리의 매핑만 변경하는 식으로 이루어짐
	- 실제로 Inode와 파일 데이터에는 아무런 영향도 미치지 않음

### Data Block Pointers
![[Inode1.png]]
- Direct Block Pointer **(node -> 데이터)**
- Single Indirect Pointer **(node -> 데이터 블록 -> 데이터)**
- Double Indirect Pointer **(node -> 데이터 블록 -> 데이터 블록 -> 데이터)**
- Triple Indirect Pointer **(node -> 데이터 블록 -> 데이터 블록 -> 데이터 블록 -> 데이터)**

### References
- https://media.geeksforgeeks.org/wp-content/uploads/20240111151731/inodes-660.png