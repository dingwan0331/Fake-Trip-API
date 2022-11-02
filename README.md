# Fake Trip

- [마이리얼트립](https://www.myrealtrip.com/) 클론 사이트
- 지원기능

  - 회원가입 & 로그인: 카카오소셜로그인을 제공합니다.
  - 숙소 리스트:
    - 지역별, 편의시설, 등급, 숙소타입, 수용인원, 가격별 필터링기능
    - 체크인 시간별 정렬기능을 제공합니다.
  - 숙소 상세정보:
    - 사용자가 선택한 날짜에 따른 예약가능한 방만 제공합니다.
    - 호텔, 룸 별 상세 사진들을 제공합니다.
  - 리뷰기능:
    - 사진을 포함한 리뷰기능을 지원합니다.
  - 예약기능:
    - 예약시 별도의 핸드폰번호 입력을 요구합니다.
    - 예약자 정보와 투숙객정보를 따로 관리합니다

# 📆 개발 기간

- 개발 기간 : 2022-07-04 ~ 2022-07-15 (12일)

## 🧑🏻‍💻 함께한 개발자

- BE(2명):
  [정진관](https://github.com/dingwan0331), [박민하](https://github.com/miracle-21)
- FE(4명): [김인태](https://github.com/dlsxody1), [장류광](https://github.com/dkzks44), 정현준, [조예지](https://github.com/Dumibell)
  - [FE GitHub 링크](https://github.com/wecode-bootcamp-korea/34-2nd-Fake-Trip-frontend)

## 🛠 협업 툴

![](https://velog.velcdn.com/images/miracle-21/post/0e0445ab-4831-4592-9db0-6c1eeae03c08/image.png)

# 사이트 시현 영상

[데모 영상](https://ifh.cc/v/oppC60.mp4)

# 기술스택

<table style="border:0;">
    <thead>
        <tr>
            <th>Language</th>
            <th>Framwork</th>
            <th>Database</th>
            <th>Test</th>
            <th>Deploy</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><img src="https://img.shields.io/badge/node.js-339933?style=for-the-badge&logo=node&logoColor=white"></td>
            <td><img src="https://img.shields.io/badge/express-000000?style=for-the-badge&logo=express&logoColor=white"></td>
            <td><img src="https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=black"></td>
            <td>Djago TestCase</td>
            <td>AWS EC2 & RDS</td>
        </tr>
    </tbody>
</table>

# Project ERD

![](https://velog.velcdn.com/images/miracle-21/post/79930301-e01b-433b-90c5-a8ffa096cb55/image.png)

# End-Point

<table style="border:0;">
    <thead>
        <tr>
            <th>기능</th>
            <th>Method</th>
            <th>Url</th>
            <th>Query</th>
        </tr>
    </thead>
    <tbody>
        <tr>
          <th>회원가입 & 로그인</th>
          <td>Post</td>
          <td>/users/signin</td>
        </tr>
        <tr>
          <th>핸드폰 번호 변경</th>
          <td>Patch</td>
          <td>/users</td>
        </tr>
        <tr>
          <th>상품 리스트</th>
          <td>Get</td>
          <td>/products</td>
          <td>start_date, end_date, min_price, max_price, offset, limit, amenity, guest, </td>
        </tr>
        <tr>
          <th>상품 상세페이지(숙소 정보)</th>
          <td>Get</td>
          <td>/products/:id</td>
          <td>start_date, end_date</td>
        </tr>
        <tr>
          <th>상품 상세페이지(룸 정보)</th>
          <td>Get</td>
          <td>/products/:id/rooms</td>
          <td>start_date, end_date, min_guest</td>
        </tr>
        <tr>
          <th>상품 상세페이지(리뷰 정보)</th>
          <td>Get</td>
          <td>/products/:id/reviews</td>
          <td>sort, newest, offset, limit,rating, has_image</td>
        </tr>
        <tr>
          <th>리뷰 작성기능</th>
          <td>Post</td>
          <td>/users/reviews</td>
          <td></td>
        </tr>
        <tr>
          <th>리뷰 삭제기능</th>
          <td>Delete</td>
          <td>/users/reviews</td>
          <td>review_id</td>
        </tr>
    </tbody>
</table>

# Directory Structure

```bash
.
├── project
├── app (users, products, orders)
│   ├── models.py
│   ├── views.py
│   ├── urls.py
│   └── tests.py
├── core
├── my_settings.py
└── requirements.txt
```

- project
  - Django에서 지원하는 기본 프로젝트 폴더입니다.
- app
  - 3가지의 app파일을 가지고있습니다.
  - users: 회원의 로그인과 리뷰를 관리합니다.
  - products: 상품 리스트와 상세정보관련 상품에 대한 리뷰를 관리합니다.
  - orders: 예약 기능을 관리합니다.
- core
  - 모둘화 시켜놓은 파일들을 관리합니다.
  - 추상 Model인 TimeStamp모듈
  - AWS S3 & KakaoSocial과 같이 외부와 통신하는 모듈도 포함되어있습니다.
- my_settings.py
  - 알고리즘, AWS 세팅, DB 세팅등의 노출하지 않을 파일들을 관리합니다.
- requirements.txt
  - pip로 설치된 라이브러리들의 이름과 버전이 기재되어있습니다.

# 🖥 담당업무

- ERD 모델링
- 웹 서버 구축(AWS: EC2 & RDS)
- 회원가입/로그인 API
  - KakaoAPI를 통한 소셜로그인 기능
  - JWT를 이용하여 토큰 발급
- 상품 상세페이지 API
  - 호텔, 룸, 리뷰 API
  - 룸별, 호텔별 예약불가 기능
- 리뷰 기능 API

  - S3 & Form Data를 이용한 이미지 업로드 기능

- 유저 핸드폰 번호 변경 API

  - 카카오에서 받지 못한 정보를 예약시에 받아오는 형식으로 풀어냈습니다.

- 예약 기능(ReservationView)
  - 예약자 정보와 투숙객 정보를 분리하여 관리
  - validators moulde의 클래스화
