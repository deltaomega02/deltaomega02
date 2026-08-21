# 박시우 (Siwoo Park)

서버 개발자를 지향합니다. 만든 것을 배포하고 **운영하면서 고장나는 걸 직접 겪는 쪽**에 관심이 많고, 그래서 동작하는 것보다 **틀렸을 때 바로 드러나는 구조**를 먼저 만드는 편입니다.

**서버·백엔드 신입 구직 중** (수도권) · sue020219@gmail.com

연성대학교 컴퓨터소프트웨어학과 학사(전공심화) 2026.02 졸업 · **학점 4.23 / 4.5** · 군필
2024 LINC 3.0 캡스톤디자인 경진대회 **대상** · 일본어 일상회화

---

## 지금 가장 많이 보고 있는 것

| 저장소 | 설명 | 기술 |
|---|---|---|
| **[metis](https://github.com/deltaomega02/metis)** | 암호화폐 거래 실행 시스템 — 1GB VM에서 1년 9개월째 운영 중. 멱등 주문 원장, 상태 정합성 조정(reconcile), systemd 자원 제한 | Python(asyncio), SQLite(WAL), GCP |
| **[orbit-local](https://github.com/deltaomega02/orbit-local)** | orbit 코디 도메인의 **Kotlin + Spring Boot 이식**. Django 구현에서 빠뜨렸던 트랜잭션 경계·테스트·N+1을 먼저 넣었다 | Kotlin, Spring Boot, JPA, JUnit 5 |

`metis`는 v1~v7을 지우지 않고 디렉토리로 남겨 뒀습니다. 같은 문제를 어떤 순서로 다르게 풀었는지가 그대로 보입니다.

## 졸업작품 (둘 다 팀장)

전문학사(3년제)와 학사(전공심화)에서 각각 한 번씩 했습니다.

| 저장소 | 설명 | 기술 |
|---|---|---|
| [orbit](https://github.com/deltaomega02/orbit) | AI 패션 코디 추천·가상 착용 — **학사 졸업작품** (3인 팀장 · 아키텍처와 AI 파이프라인 담당, DB·통신 흐름은 팀원과 공동) | Django REST, MySQL, React Native(TS), Gemini |
| [rubato](https://github.com/deltaomega02/rubato) | AI 여행 경로 추천 — **전문학사 졸업작품**, 교내 캡스톤디자인 경진대회 **대상** (5인 팀장) | Android(Java), PHP, MySQL, GPT-4o + Gemini |
| [mechu](https://github.com/deltaomega02/mechu) | AI 메뉴 추천 (2학년 팀 프로젝트, 3인 팀장) | Android(Java), SQLite |

## 암호화폐 자동매매 — 7세대 기록 (2024.11 ~ )

하나의 문제를 7세대에 걸쳐 다시 설계한 기록입니다. 각 세대는 직전 세대의 **운영 데이터 분석**에서 출발했습니다. 현행 운영은 METIS 계열 최신 분기이고, 나머지는 중지·보존입니다.

| 세대 | 저장소 | 핵심 |
|---|---|---|
| 1 | [valkyr](https://github.com/deltaomega02/valkyr) | 첫 시스템 — 시그널·주문·모니터링 기본 구조 |
| 2 | [argos](https://github.com/deltaomega02/argos) | AI Chain-of-Thought 추론 도입 |
| 3 | [omni-archive](https://github.com/deltaomega02/omni-archive) | OODA 루프, 회고 기반 학습 |
| 4 | [metis](https://github.com/deltaomega02/metis) ([f](https://github.com/deltaomega02/metis-f) · [f2](https://github.com/deltaomega02/metis-f2) · [v5](https://github.com/deltaomega02/metis-v5)) | 분석 파이프라인 구조화. **v5에서 데이터 검증 후 AI를 판단 경로에서 제거.** 최신 분기가 현행 운영 |
| 5 | [hermes](https://github.com/deltaomega02/hermes) ([백테스트 연구](https://github.com/deltaomega02/hermes-backtesting)) | 4년 데이터 × 342,000 파라미터 조합 그리드서치 |
| 6 | [kairos](https://github.com/deltaomega02/kairos) | 전략 단순화 실험 |
| 7 | [athena](https://github.com/deltaomega02/athena) | AI 포트폴리오 매니저 (중지) — 이후 METIS 계열로 회귀 |

AI를 넣었다가 데이터를 보고 뺀 것이 이 시리즈에서 가장 중요한 판단이었습니다. AI를 쓰는 게 목적이 아니라 문제를 푸는 게 목적이라고 생각합니다.

## 도구

| 저장소 | 설명 | 기술 |
|---|---|---|
| [wucalc](https://github.com/deltaomega02/wucalc) | 게임 데미지 계산기 — 손계산 기댓값과 대조하는 **단위 테스트 184개** | Next.js, TypeScript strict, Tesseract OCR |
| [line-translator-bot](https://github.com/deltaomega02/line-translator-bot) | LINE 한↔일 번역·한국어 튜터 봇 (매일 사용 중). 상주 봇 → 서버리스 웹훅 전환 | Python, GCP Cloud Functions |
| [narou-translator](https://github.com/deltaomega02/narou-translator) | 일본 웹소설 번역 Chrome 확장 (작품별 용어집) | JavaScript, Chrome Extension |

---

공개 저장소의 API 키와 계정 정보는 모두 placeholder로 대체되어 있습니다.
