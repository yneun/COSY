# 🧠 COSY - AI 규제 적합성 판단 어시스턴트

RAG(Retrieval-Augmented Generation) 기반으로 사용자 입력을 분석하고,
국가별 규제 데이터를 바탕으로 적합성을 판단하는 AI 어시스턴트입니다.

---

## 👤 My Role

- Spring Boot 기반 백엔드 API 설계 및 구현
- MySQL 데이터베이스 설계 및 연동
- API–DB 간 데이터 처리 로직 구현
- 서비스 기능 구현 및 데이터 흐름 관리

(본 프로젝트는 팀 프로젝트로 진행되었으며, 본 레포는 개인 포트폴리오 용도로 재구성한 것입니다.)

---

## 🚀 주요 기능

* 사용자 입력 기반 규제 적합성 판단
* Vector DB 기반 의미적 유사도 검색
* 금지 키워드 필터링을 통한 보안 및 성능 개선
* Redis 기반 캐싱 구조 적용 (팀 협업)

---

## 🧠 Architecture

User → Spring Boot API → MySQL  
                      ↘ FastAPI (RAG 서버) → Vector DB → LLM

---

## ⚙️ Tech Stack

- **Backend**: Spring Boot
- **Database**: MySQL
- **AI**: RAG, FastAPI (팀 프로젝트 구성 요소)
- **Cache**: Redis

---

## 🔧 실행 방법 (Local Setup)

### 1. FastAPI 서버 실행

```bash
py -3.10 -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

```bash
python -m app.scripts.ingest_regulations
uvicorn app.main:app --host 127.0.0.1 --port 8000
```

👉 http://127.0.0.1:8000/docs

---

### 2. Redis 실행

```bash
docker run -d --name local-redis -p 6379:6379 redis:7
```

---

## 🚀 개선 경험 (Problem → Solution)

### ❗ 문제

* 키워드 기반 검색 → 낮은 정확도
* 벡터 검색 도입 후 → 응답 속도 저하

### ✅ 해결

* 벡터 임베딩 기반 검색 구조로 개선
* 입력 단계에서 금지 키워드 필터링 추가
* 데이터 전처리 및 검색 범위 제한으로 성능 개선

---

## 📈 결과

* 검색 정확도 향상
* 응답 속도 개선
* 안정적인 데이터 처리 구조 확보

---

## 📝 배운 점

* 단순 구현보다 **구조 설계가 성능과 품질에 큰 영향**을 미친다는 것을 체감
* 문제 해결 시 다양한 접근을 비교하며 개선하는 과정의 중요성 학습
