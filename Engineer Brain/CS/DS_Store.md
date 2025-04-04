# Define
- MacOS에서 Finder를 통해 파일을 확인할 때 추가되는 설정 파일
- 현재 경로에 포함된 파일들, 유저가 저장한 설정 등이 보통 저장되어있음
- 지워도 큰 문제가 생기진 않으나, 지우고 다시 열어보면 다시 생겨있어서 불편함

# Disable DS_Store
- `defaults write com.apple.desktopservices DSDontWriteNetworkStores true` 실행
- 그 이후부터는 DS_Store 파일이 다시 생기지 않는다고 함

# Remove DS_Store
- `find . -name '.DS_Store' -type f -delete` 실행
- 자동으로 현재 경로와 하위 경로에 존재하는 모든 DS_Store 파일들을 제거해줌

### References
- https://dlee0129.tistory.com/250
- https://velog.io/@junr_65535/.DSstore가-뭐여-난-이런거-쓴적-없는디
- https://chanhhh.tistory.com/209
