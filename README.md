# 박시우 | Siwoo Park

서버와 외부 API를 연결하고, 모바일 앱과 PC 앱을 만들었습니다. 대표 프로젝트는 옷장 관리와 코디 추천 앱인 **Orbit**입니다.

* 연락처: [sue020219@gmail.com](mailto:sue020219@gmail.com)
* 학력: 컴퓨터소프트웨어학과 학사(전공심화) 졸업 · 학점 4.23/4.5
* 수상: 2024 LINC 3.0 캡스톤디자인 경진대회 대상 · Rubato, 팀 DeltaOmega

## 프로젝트

### [Orbit](https://github.com/deltaomega02/orbit)

옷을 등록하고 날씨, Google Calendar 일정, 스타일 선호에 맞는 코디를 추천받는 모바일 앱입니다. 전신 사진을 바탕으로 가상 착용 이미지도 생성합니다.
학사 졸업작품으로 3명이 함께 만들었습니다. 팀장으로 전체 아키텍처 설계와 서버 전반, Gemini 연동 프롬프트 및 이미지 생성 흐름을 맡았습니다. DB 저장·관리 로직과 클라이언트-서버 통신은 풀스택 팀원과 나누어 구현했습니다.

추천 결과가 이미지 생성을 기다리지 않도록 추천 결과를 먼저 저장해 반환하고 가상 착용은 별도 요청으로 분리했습니다. 이미 생성된 착용 이미지가 있으면 다시 만들지 않고 기존 이미지를 씁니다.
오늘 추천한 조합을 프롬프트에 넣어 두고, 모델 응답이 기존 조합과 같으면 재시도 신호를 반환하도록 처리했습니다.

구성: `React Native·Expo 앱 → Django REST Framework 서버 → MySQL`이며, 서버에서 Gemini API를 호출합니다.

### [Orbit Local](https://github.com/deltaomega02/orbit-local)

Orbit을 Kotlin과 Spring Boot로 다시 만든 개인용 PC 앱입니다. 브라우저 UI와 H2 파일 DB를 사용하며 Windows 배포본에는 실행 런타임을 포함했습니다.
기존 앱의 이메일 기반 간이 토큰을 서명과 만료가 있는 JWT로 바꾸고, 코디와 하위 아이템이 한 트랜잭션으로 묶여 저장되도록 구성했습니다. 저장 실패 시 롤백되는 동작도 테스트로 확인했습니다.

구현 과정에서 마주친 문제는 다음과 같이 풀었습니다.

* 코디 목록에서 컬렉션 fetch join과 페이지네이션을 함께 쓰자 Hibernate가 메모리에서 페이징을 처리한다는 경고를 남겼습니다. ID 목록을 먼저 페이징 조회한 뒤 해당 ID들로 fetch join하도록 쿼리를 둘로 나눴습니다. 이후 코디 수가 늘어도 쿼리 실행 횟수가 일정한지 Hibernate 통계로 검사했습니다.
* 가상 착용 기능이 앱에서만 얼굴을 바꾸는 문제가 있었습니다. 프롬프트 수정으로 잡히지 않아 로컬 프록시로 실제 요청을 확인했고, 설정 파일이 코드 기본값을 덮어 다른 모델을 호출하고 있던 것을 찾았습니다. 모델 설정을 바로잡은 뒤에는 결과 이미지 크기가 입력 이미지와 일치하는지를 회귀 확인 기준으로 삼았습니다.

### METIS 자동매매 ([AI 판단 버전](https://github.com/deltaomega02/metis-ai-trader) · [규칙 기반 버전](https://github.com/deltaomega02/metis-rule-trader))

Bybit USDT 무기한 선물을 대상으로 포지션 관리와 주문 집행을 자동화한 개인 프로젝트입니다. 초기 AI 판단 버전은 Gemini로 종목 분석과 진입 신호를 생성하고, 코드에서는 스레드 풀 병렬 처리와 주문 유효성 검증을 담당하도록 분리해 운영했습니다.

하지만 AI 방식은 과거 데이터로 판단 과정을 다시 재현해 검증하기 어렵다는 문제가 있었습니다. 이에 따라 장기 데이터로 검증할 수 있는 규칙 기반 구조로 전환했습니다. 슬리피지와 펀딩비를 반영한 5.9년 백테스트를 통해 돈치언 돌파와 추세 지표 조합을 검증했고, 자본 대비 리스크와 최대 손실 한도를 정량적으로 통제하도록 설계했습니다.

이후 GCP 환경에서 systemd 데몬으로 약 45일간 무중단 가동하며 거래소 포지션 대조, 백오프 재시도, SQLite 기반 원장 관리를 구현했습니다. 실거래 표본이 적어 기대값을 충분히 입증하지는 못했지만, 신뢰성 있는 실행 시스템을 직접 운영해 보는 계기가 되었습니다. Python, SQLite, Bybit V5 API, WebSocket, GCP Compute Engine을 사용했습니다.

### [Rubato](https://github.com/deltaomega02/rubato)

여행지와 기간, 취향 태그를 입력하면 일정을 짜고 네이버 지도에 동선을 그려 주는 Android 앱입니다. 전문학사 졸업작품으로 5명이 함께 개발했습니다.
팀장을 맡아 기획과 WBS 기반 일정 관리, 서버 구축, AI 로직 구현을 진행했습니다. 실시간 정보 처리 방식을 두고 의견이 갈렸을 때는 두 방식의 시제품에 같은 질문을 넣어 비교해 보고 팀원들과 방향을 결정했습니다.
Android(Java), PHP, MySQL과 OpenAI·Gemini API를 사용했습니다.

### [LINE Translator](https://github.com/deltaomega02/line-translator)

등록된 두 사용자의 LINE 대화를 한국어와 일본어로 번역하는 개인 스크립트입니다. 상대가 한국어로 쓴 문장은 어색한 곳만 짧게 교정하고 자연스러우면 👍로 답하며, 질문 명령이 들어오면 검색을 활용해 답변을 정리합니다.
GCP Cloud Functions의 Python 웹훅 함수에서 LINE 서명을 검증한 뒤 Gemini API를 호출하도록 만들었습니다.

## 사용 기술

* 언어: Java, Kotlin, Python, PHP, TypeScript
* 서버·앱: Spring Boot, Django REST Framework, Android, React Native
* 데이터·외부 연동: MySQL, SQLite, GCP Compute Engine, GCP Cloud Functions, Gemini API, OpenAI API, Bybit API
