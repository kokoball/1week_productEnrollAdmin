# 목표는 취업이조 (1주차 2번째 과제 복습)

## 🚀 정보

- [배포주소 바로가기](https://goalisemployment.s3.ap-northeast-2.amazonaws.com/index.html)
- [노션 바로가기](https://sleepy-oxygen-343.notion.site/41970b5fee2d45aebd7b01de061039eb)

## 🧐 프로젝트 빌드 및 실행 방법

1. 상단 `Code` 버튼을 눌러 레포지토리를 클론 받습니다.

```
$ git clone https://github.com/wanted-team2/1week_productEnrollAdmin.git
```

2. 패키지를 설치합니다.

```
$ yarn install
```

3. 서버를 실행합니다.

```
$ yarn start
```

## 😎 팀원

- [김지영(팀장)](https://github.com/Jeong-jeong)
- [고병표](https://github.com/kokoball)
- [유제호](https://github.com/ludacirs)
- [홍수연](https://github.com/suyeon-hong)

## 🌈 담당

- ### 김지영

  - `상품 옵션 테이블(OptionTable)` 구현
    - 옵션 세트 추가, 삭제
    - 옵션 이미지 추가
    - 옵션 세트 내 옵션 추가, 삭제
    - 옵션 세트 내 옵션 내 추가, 삭제
    - 옵션 세트 내 옵션을 모두 삭제하면 옵션 세트 또한 삭제
    - 할인율 처리
      - 할인율 소수점 버림 처리
      - 정상가, 판매가 같을 경우 `할인율 없음` 표시
    - 재고 처리
      - 옵션 세트 내 모든 옵션에 대한 총 재고 수량 저장
    - 비과세, 과세 처리
      - 과세 옵션 선택 시 해당 옵션의 저장된 판매가의 부과세(VAT) 10%로 저장
    - 옵션 세트 내 옵션들은 입력시마다 디바운스 후 저장됨
    - 상품 옵션 테이블 데이터 구조

    ```js
    {
      index: 0, // 각 옵션세트 인덱스
      imageInfo: {},
      optionInfo: [ // 옵션 세트 내 옵션 정보
      {
        index: 0,
        optionName: '',
        normalPrice: 0, // 정상가
        price: 0, // 할인가
        discount: 0,
        stock: 0,
        isVAT: true,
        VAT: 0, // 부과세
        },
      ],
      totalStock: 0, // 옵션 세트 내 모든 옵션의 stock 총합
      additoryOptions: [ // 옵션 세트 내 옵션 내 추가
      {
        index: 0,
        addOptionName: '',
        addOptionNormalPrice: 0,
        },
      ],
    }
    ```
  - `상품 정보고시 테이블(ItemInformationTable)` context 분리, 및 리팩토링

- ### 유제호

  - `상품 기본 정보 테이블(ProductionInformation)` 구현
  - 전반적인 전역 상태관리
  - 태그 검색시 디바운스 적용
  - aws S3 배포

- ### 고병표

  - `노출 및 판매 기간 테이블(SetPeriodTable)` 구현
    - RadioButton 기본값("제한 없음")설정
    - 랜더링 시 Calender 기본값 설정 (1번 Calender : 현재 시간, 2번 Calender : 한 달 뒤)
    - 2번 Calender의 설정 날짜가 1번 Calender 보다 빠를 경우 Check value "미 노출" 상태로 변경
    - 상품 총 재고가 0이 (check = false) 되는 경우, 자동으로 "미판매" 상태로 변경
  - `상품 정보고시 테이블(ItemInformationTable)` 구현
    - 랜더링 시 '정보 고시 1' Table 불러오게 기본값 설정
    - 옵션 세트 추가/삭제, 항목 추가/삭제
  - `상품 소개, 구매자 추천 테이블(ProductImageTable, RecommendImageTable)` 구현
    - 이미지 첨부 Tab 시, 우측에 이미지 파일명 X 버튼과 함께 노출
    - X 버튼 클릭시 파일명 삭제

- ### 홍수연
  - `상품 배송 설정, 상품 혜택 허용, 기타 설정 테이블` 구현
    - 사용자 배송일 혹은 방문수령 토글버튼 활성화 시, 선 주문 예약 배송 토글버튼 비활성화
    - 선 주문 예약 배송 토글 활성화 시, 사용자 배송일 혹은 방문수령 토글버튼 비활성화
    - 주문 시작 시간과 마감 시간 비교하여 마감시간이 시작 시간보다 이를 경우 경고창 제공
    - 마감시간보다 이른 배송 날짜 선택시 경고창 제공

<br>
<br>

## 📈 디렉토리 구조

```
.
├── README.md
├── babel.config.js
├── craco.config.js
├── jest.config.js
├── package.json
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── robots.txt
│   └── tags.json
├── src
│   ├── App.jsx
│   ├── assets
│   ├── components
│   ├── contexts
│   ├── hooks
│   ├── pages
│   ├── setupTests.js
│   ├── style
│   └── utils
│   ├── index.jsx
└── yarn.lock
```
