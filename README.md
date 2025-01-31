# ✈️ TravelMail

## 🔓 프로젝트 설명

코로나 이후 드디어 일본여행이 가능해지면서, 일본행 비행기표 가격과 환율 정보를 매일 전달받고 싶은 마음에 시작한 작은 프로젝트입니다.

항공권 최저가 확인이 가능한 사이트에서 지정된 날짜의 지정된 여행지의 왕복&직항 비행기표 정보를 찾아 환율과 함께 **매일 12시에** 메일로 보내줍니다.

## 📊 수행하는 작업

1. 비행기표 데이터 수집 및 처리, 가공
2. 환율 정보 API 받아오기 및 처리, 가공
3. 최근 30영업일 간의 환율 차트 생성 및 PNG 저장
4. 비행기표 정보와 환율 정보를 담은 메일 발송기능
5. 오라클 클라우드 서버에서 주기적으로 환율 정보 수집 및 메일 발송 (매일 12시 점심)
6. 노션 데이터베이스에 모든 프로젝트 데이터 저장

## ✏️ 사용된 기술종류와 기술 설명

- **Selenium** : 동적인 크롤링이 가능한 셀레니움을 이용해 사이트에 접속, 최저가 페이지를 캡쳐하고, 사이트의 HTML코드를 가져옵니다.
- **BS4(BeautifulSoup)** : Selenium으로 가져온 HTML에서 원하는 값을 추출하고 다룰 수 있도록 해줍니다.
- **smtplib** : 파이썬 환경에서 이메일을 보낼 수 있게 해주는 패키지입니다. 이미지 첨부, 메일 템플릿 수정이 가능합니다.
- **requests** : 서버로 request를 보낼 수 있습니다. 한국수출입은행 API 활용을 위해 사용하였습니다.
- **한국수출입은행 API** : 환율 정보를 제공해주는 서비스입니다. 원-엔 환율 데이터를 받아옵니다.
- **ORACLE CLOUD SERVER** : 매일 주기적으로 프로그램을 돌려 정보수집 및 메일 발송을 하기위해 따로 서버를 활용하고 있습니다.
- **pandas** : 크롤링한 데이터 및 csv 파일을 DataFrame의 형태로 수정, 가공을 위해 필요한 패키지입니다.
- **matplotlib** : 데이터를 시각화해주는 패키지입니다. 환율 데이터를 그래프화해줍니다.
- **Notion Database** : 노션페이지를 데이터베이스로 활용하고 있습니다.

## 📩 이메일 예시 :

![mail_example](https://user-images.githubusercontent.com/59094592/195336022-a1551b13-af8b-4d64-b910-1ac2c6d60e7d.png)

## 📎 첨부파일 :

### 📸 셀레니움 캡쳐 결과

![price](https://user-images.githubusercontent.com/59094592/193433847-92c4863d-9292-44b7-92fd-2eb255b0c91d.png)

### 💴 환율 차트 생성 결과

![recent_jpy_currency](https://user-images.githubusercontent.com/59094592/196305564-89c58440-579d-4cfd-a408-dfe9fb278c05.png)

## 🛠 To Dos

- [x] 유저마다 원하는 **날짜**에 맞게 개인화된 항공권 검색 기능
- [x] 유저마다 원하는 **여행지**에 맞게 개인화된 항공권 검색 기능
- [x] 유저마다 원하는 **통화**에 맞는 개인화된 환율 정보 제공 기능
- [ ] ~~requests와 selenium 성능 비교~~ -> requests로 크롤링 힘듦
- [ ] ~~requests 성능이 좋다면, 이미지 캡쳐의 대안 찾기~~
- [x] 유저 데이터 DB에 저장하기 **(2022.10.28 기능 추가 완료)**
  - [x] DB 어떤 것 사용할지 정하기 : Notion DB
  - [x] DB 스키마 짜기
- [ ] 웹에서 신청 받아 DB에 추가
  - [ ] 유저의 신청 정보가 겹치면 묶어서 데이터 수집 1회만 수행한 후 메일 다건 동시에 발송
  - [ ] Flask? Fast API? 어떤 프레임워크 사용할 것인지 정하기
  - [ ] 웹과 크롤링이 섞이게 되면 프로젝트 구조를 어떻게 만들어야할지 알아보기
