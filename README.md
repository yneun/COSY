# 🧠 COSY - AI 규제 적합성 판단 어시스턴트

사용자 입력을 기반으로 국가별 규제 적합성을 판단하는 서비스로,
Spring Boot 기반 백엔드와 RAG 구조를 결합한 프로젝트입니다.

---

## 👤 My Role

* Spring Boot 기반 백엔드 API 설계 및 구현
* MySQL 데이터베이스 설계 및 연동
* 사용자 요청 처리 및 데이터 흐름 관리
* AI(RAG) 서버와의 API 연동 로직 구현

---

## 🚀 주요 기능

* 사용자 입력 기반 규제 적합성 판단 요청 처리
* MySQL을 활용한 데이터 저장 및 조회 기능 구현
* Spring Boot API를 통한 서비스 로직 처리
* FastAPI 기반 AI 서버와 연동하여 결과 반환

---

## 🧠 Architecture

User → Spring Boot API → MySQL
          ↘ FastAPI (RAG) → Vector DB → LLM

---

## ⚙️ Tech Stack

* **Backend**: Spring Boot
* **Database**: MySQL
* **AI**: FastAPI, LangChain, RAG
* **Cache**: Redis
* **Infra**: Docker

---

## 🔧 실행 방법 (Local Setup)

### 1. Spring Boot 실행

```bash id="2zq8p0"
./gradlew bootRun
```

---

### 2. FastAPI 서버 실행

```bash id="b6r0gc"
py -3.10 -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

```bash id="q3s1fv"
python -m app.scripts.ingest_regulations
uvicorn app.main:app --host 127.0.0.1 --port 8000
```

---

### 3. Redis 실행

```bash id="5b9o4s"
docker run -d --name local-redis -p 6379:6379 redis:7
```

---

## 🚀 개선 경험 (Problem → Solution)

### ❗ 문제

* 키워드 기반 검색 방식에서 정확도 부족
* AI 서버 응답 속도 지연

### ✅ 해결

* 벡터 기반 검색 구조(RAG) 도입
* 입력 단계에서 금지 키워드 필터링 적용
* 데이터 처리 흐름 개선 및 불필요한 연산 감소

---

## 📈 결과

* 검색 정확도 향상
* 응답 속도 개선
* 안정적인 API–AI 연동 구조 구축

---

## 📝 배운 점

* API–DB–AI 서버 간 데이터 흐름 설계의 중요성 이해
* 단순 기능 구현이 아닌 구조 설계가 성능에 미치는 영향 체감

---

## 📌 Note

본 프로젝트는 팀 프로젝트로 진행되었으며, 본 레포는 개인 포트폴리오 용도로 재구성되었습니다.
