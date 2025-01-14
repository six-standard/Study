### Define
- 파일 시스템을 특정 디렉토리에 연결하여 디렉토리에 접근하는 방식으로 저장 장치의 데이터를 접근할 수 있게 해주는 행위
- 물리적인 하드웨어를 특정 마운트 포인트에 할당하여 해당 파일 시스템에 접근할 수 있게 해주는 행위
- 보통 `/dev`, `/media`, `/mnt` 이 세 가지 디렉토리를 통해 진행되게 됨

### Directories
#### /dev
- 리눅스에 연결된 물리 하드웨어들이 파일화되어있는 디렉토리
#### /media
- mount된 하드웨어들이 할당되는 디렉토리
- 필요한 하드웨어만 동적으로 마운트하기 위해 제작된 디렉토리
#### /mnt
- mount된 장비들이 임시 할당되는 디렉토리
- media와는 다르게, 시스템 운영자들이 백업/복원을 진행하거나, 새 디스크로 옮길 때 사용되는 디렉토리
- media와 동일한 방식으로 동작하긴 함

### References
- https://inpa.tistory.com/entry/LINUX-📚-하드-링크hard-link-심볼릭-링크symbolic-link-아이노드inode#inode_란
- https://unix.stackexchange.com/questions/13975/mounting-a-device-role-of-dev-media-and-mnt-and-the-mount-command