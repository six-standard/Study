이미지에는 다양한 포맷이 존재했음.
그러나 최근 들어서 거의 일부 포맷으로 굳혀지고 있는 것 같은데, 이렇게 굳혀진 포맷들에 대해 정리해보기로 함.

### JPEG (JPG)
Joint Photograph Expert Group, 손실 압축 형태의 래스터 이미지 파일 포맷으로, 보통 스마트폰으로 사진을 찍으면 나오는 파일이 이 파일임.
#### Compression
1. **RGB 형태의 색상들을 YCrCb 방식으로 변경**
   픽셀의 밝기를 표현하는 Y, 색상의 색차를 표현하는 Cr Cb 형태로 이미지를 분리함.
2. **이미지 다운샘플링**
   보통 4:2:0 다운샘플링을 사용하며, 2\*2의 영역을 선택하여 평균 CrCb 값을 구한 뒤, 이를 영역에 덧씌워 색차의 갯수를 줄임.
   이 과정에서 Y값은 유지하는데, 인간의 눈은 밝기(Y) 에 민감하고, 색차(Cr, Cb) 에는 덜 민감하기 때문.
3. **이산코사인변환(DCT)**
   ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdQvDS3%2FbtqG624kUlj%2FURToKjCKMRmWpwVCH6gZX0%2Fimg.png)
   이미지를 8\*8의 작은 블록들으로 나누고, 이산 코사인 변환을 통해 픽셀 값을 주파수 정보로 변환함.
   이 과정에서 저주파(큰 변화와 구조), 고주파(작은 변화와 디테일) 이 분리됨. (DC, AC라고도 함)
4. **양자화**
   ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F9T32C%2FbtqG3kSm8sA%2F6augQc2Mj5BgQO69yXuvjK%2Fimg.png)
   변환된 주파수 정보들을 양자화 테이블을 통해 근사화함. (이 과정에서 정밀도가 감소하고, 정보가 손실됨)
5. **지그재그 스캔**
   ![](https://upload.wikimedia.org/wikipedia/commons/e/e1/Zigzag_scanning.jpg)
   이미지를 지그재그 형태로 스캔하여 더욱 효율적으로 압축할 수 있도록 데이터를 재배열하는 과정.
6. **엔트로피 코딩**
   허프만 코딩, 산술 코딩 등을 사용하여 재배열된 데이터를 압축하고, JPG 이미지 형태로 변환.
#### Why JPG
JPEG 말고 JPG라는 확장자도 존재하는데, 이름처럼 둘이 똑같은 포맷임.
원래 JPEG 포맷 자체가 초기 MS-DOS가 사용되던 시절에 나왔는데, 하필 MS-DOS가 파일 확장자를 3자리까지만 사용 가능해서 JPEG 대신 JPG 포맷을 사용했다고 함.

물론 현재는 윈도우 환경을 사용하며, 윈도우에서는 확장자 자리수 제한이 사라졌기 때문에 JPEG를 사용할 수 있게 되었음. (다만 JPG도 여전히 쓸 수 있는데. 결국 내부 내용물이 서로 동일해서 큰 문제는 없는 듯)
#### PNG
Portable Network Graphics, GIF 포맷을 대체하기 위해 나온 무손실 압축 형태의 래스터 이미지 포맷, 보통 그림을 다운로드받을 때 주로 보임.

- 투명 레이어, 트루컬러 (24비트) 등을 제공하고 있으며, GIF와 비교하여 라이선스가 없기 때문에 사용 자체도 자유로운 편.
- 빈도 수가 높고 연속된 데이터를 짧은 코드로 변환하는 DEFLATE 알고리즘을 통해 무손실 압축을 지원함.
  (다만 절대적인 이미지의 크기가 줄어드는건 아니라서, 큰 이미지일 경우 압축률이 JPEG보다 딸리는 편)
- 다만 래스터 형태인 만큼, 확대할 경우 계단 현상이 두드러지게 일어나는 편.
### SVG
Scalable Vector Graphics, 대표적인 백터 이미지 포멧, 보통 서비스의 단순한 아이콘 등에 주로 보임.

- 기본적으로 벡터 그래픽이기 때문에, 확대해도 이미지가 깨지지 않음
- 다만 수학적인 연산을 통해 그래픽으로 구현되는 만큼, 크고 복잡한 이미지일 경우 성능상 문제가 생기게 됨.
- XML 기반으로 동작해서, 파일 자체는 가벼운 편 (웹 브라우저에서도 태그 삽입으로 사용 가능)
### WebP
Web Picture Format, 구글이 개발한 벡터 이미지 포맷, 이름대로 웹에서의 배포에 쓰임.

### BMP
![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fckz7Df%2Fbtqu6L0NgDn%2FUVdYLIUqU12z7lkK4sB2f0%2Fimg.png)
BitMaP, 후처리 작업이 전혀 없는 무손실 무압축 고해상도 이미지 포맷으로, 단순히 이미지의 각 픽셀들을 비트로 일일히 입력해둔 이미지 파일 방식.
진짜 순수히 모든 픽셀을 표현한 방식이라, 분석도 쉽고 수정도 쉽다고 함.
다만 압축도 없고, 손실도 없어서 용량을 매우 많이 차지함.

### References
- https://velog.io/@es_seong/Image-Compression-JPEG-JPEG-2000
- https://suyeon96.tistory.com/15
- ChatGPT 응답 다수