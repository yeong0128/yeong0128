<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=180&section=header&text=JiYeong%20Kim&fontSize=48&fontAlignY=36&desc=Backend%20%C2%B7%20AI%20Developer&descAlignY=58&descSize=18&animation=fadeIn" width="100%" />

</div>

# 안녕하세요, 백엔드 · AI 개발자 김지영입니다 👋

> **만들고, 배포하고, 측정으로 확인하는 개발자입니다.** 직접 만든 블로그 서비스를 배포·운영하며 첫 화면 처리량을 **약 370배** 높였고, 캡스톤 팀에서는 **LLM 평가 엔진과 DB**를 맡아 AI 응답이 서비스를 멈추지 않게 만들었습니다.

[![Notion](https://img.shields.io/badge/Portfolio-000000?style=flat-square&logo=notion&logoColor=white)](https://app.notion.com/p/JiYeong-Kim-c411b2070412823da61a0149be508a15)
[![Ylog](https://img.shields.io/badge/Ylog-운영_중-4F46E5?style=flat-square)](http://ylog.java21.net)

---

## 🙋 About Me

- **측정으로 확인하는 개발** — AI 도구가 짚어 준 원인대로 고쳤다가 오히려 느려진 뒤, 실행 계획(EXPLAIN)을 직접 보고 진짜 원인을 찾았습니다. 그 뒤로 AI의 답도 숫자로 확인하고 반영합니다.
- **규칙은 한 번 더 막는다** — 예약 겹침은 서버 코드뿐 아니라 DB 제약으로, LLM 응답은 프롬프트뿐 아니라 Pydantic 검증과 복구 파싱으로 한 겹 더 막습니다.
- **요구사항부터 정하고 만든다** — 무엇을 만들지 문서로 먼저 정하고 구현합니다. 사용자 피드백으로 규칙을 바꿀 때도 요구사항 문서를 먼저 고친 뒤 코드를 고칩니다.

---

## 📌 Projects

### 📝 [Ylog](http://ylog.java21.net) — 멀티유저 블로그 서비스

`개인 프로젝트` `2026.10 ~ 운영 중` `Java` `Spring Boot` `PostgreSQL` `Redis` `React` `Docker` `Nginx` `GitHub Actions`

- **첫 화면 처리량 약 370배 개선** — 인기 검색어·핫한 글 순위가 "최근 14일" 조건 때문에 인덱스를 못 타고 전체 스캔하던 것을 EXPLAIN으로 찾아 조건·인덱스를 고치고, 순위는 Redis에 캐싱 → 초당 **10.7건 → 3,971건**
- **무중단 배포** — 새 서버를 옆에 띄운 뒤 Nginx 경로만 바꾸는 블루그린 배포로 배포 중 끊김 **약 8초 → 0초**
- **보안 점검** — 로그인 5회 실패 시 10분 잠금, 가입 여부를 숨기는 동일 오류 메시지, 비밀값은 GitHub Secrets로 분리, Git 기록에 남은 개발용 비밀번호까지 찾아 제거
- 학교 서버의 https 종단 처리로 소셜 로그인 리다이렉트가 http로 만들어지던 문제를 전달 헤더 설정으로 해결

### 🎤 [AICO](https://github.com/SpeechLab04/AICOproject) — AI 발표 코칭 서비스

`Backend & LLM 담당` `4인 캡스톤` `2026.03 ~ 06` `Python` `FastAPI` `OpenAI API` `Whisper` `SQLite` `SQLAlchemy` `Alembic` · [데모](https://aic-oproject.vercel.app)

- **LLM 내용 평가 엔진** — 발표 대본을 구성 40% · 근거 40% · 표현 20%로 채점, JSON 출력 고정 + `temperature=0`으로 같은 발표엔 같은 점수, 총점은 GPT가 아닌 서버가 가중치로 계산
- **AI 응답 때문에 서버가 멈추던 문제 해결** — 응답 앞에 설명 문장이 섞여 파싱 500 에러 → 출력 형식 가드레일 + Pydantic 검증 + 깨진 응답 재추출로 형식 오류 다운 제거
- 빈 대본·짧은 대본은 GPT 호출 전에 차단해 근거 없는 고득점과 불필요한 API 비용을 함께 막음, 교수 성향 4종 페르소나별 **예상 질문 생성**
- 사용자 → 발표 세션 → 피드백 **1:N 스키마 설계**, JWT 인증, SQLite 제약으로 어긋난 Alembic 마이그레이션을 batch mode로 해결

### 🏫 [M-SPACE](https://github.com/AI-go-do/mspace-core) — 학과 스터디룸 예약 시스템

`백엔드 예약 코어` `4인` `진행 중` `Java` `Spring Boot` `PostgreSQL` `Flyway` `Testcontainers` `GitHub Actions`

- 종이 대장으로 하던 스터디룸 5개 예약을 온라인으로 옮기는 프로젝트, **학교 시범운영** 예정
- 같은 방 시간 겹침은 **PostgreSQL `EXCLUDE` 제약**, 대표자당 1건은 부분 유니크 인덱스, 2시간·30분 단위는 `CHECK` 제약으로 **DB가 직접 막도록** 설계
- Flyway로만 스키마를 바꾸는 규칙으로 팀원·서버 DB를 맞추고, Testcontainers로 실제 PostgreSQL 위에서 테스트
- 기능 브랜치 → PR 리뷰 → Squash merge, PR마다 GitHub Actions 빌드·테스트와 SonarQube 품질 게이트

---

## 🛠 Tech Stack

| 분야 | 기술 |
| --- | --- |
| **Backend** | ![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white) |
| **Database** | ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white) ![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white) |
| **AI** | ![OpenAI API](https://img.shields.io/badge/OpenAI_API-412991?style=flat-square&logo=openai&logoColor=white) ![Whisper](https://img.shields.io/badge/Whisper-412991?style=flat-square&logo=openai&logoColor=white) |
| **Infra** | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white) ![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white) ![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black) |
| **Frontend** | ![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB) |
| **Collab · Tools** | ![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white) ![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white) ![Claude Code](https://img.shields.io/badge/Claude_Code-D97757?style=flat-square&logo=claude&logoColor=white) |

---

## 🏅 Certifications

| 자격증 | 취득일 |
| --- | --- |
| 정보처리기사 | 2026.06 |
| ADsP (데이터분석 준전문가) | 2026.06 |
| 한국사능력검정시험 1급 | 2026.08 |

---

## 📊 GitHub Stats

<div align="center">

<img src="https://github-readme-stats-fast.vercel.app/api?username=yeong0128&show_icons=true&theme=tokyonight&hide_border=true&include_all_commits=true" height="165" />
<img src="https://streak-stats.demolab.com/?user=yeong0128&theme=tokyonight&hide_border=true" height="165" />

</div>

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=100&section=footer" width="100%" />

</div>
