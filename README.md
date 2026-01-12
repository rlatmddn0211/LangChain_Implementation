# 🦜🔗 LangChain Implementation & Fullstack GPT

> **Implementation of exploring RAG, Memory, and Chains through various LLM services.**

## 🛠️ Tech Stack
- **Framework:** `LangChain`, `FastAPI`, `Streamlit`
- **Language Model:** `OpenAI (GPT-3.5-turbo)`, `Google Gemini`
- **Language:** `Python 3.10+`
- **Tools:** `Git/GitHub`, `LangChain`

---

## 📚 Learning Progress

### 🔹 Chapter 3: LangChain Basics (Current)
LangChain의 핵심 구조와 LCEL(LangChain Expression Language)을 활용한 체인 구성 학습/구현

**1. Model I/O & Configuration**
- **LLM Integration:** OpenAI 및 Google Gemini 모델 연동 및 환경 변수(`.env`)를 통한 API Key 보안 관리.
- **Model Parameters:** `Temperature` 조절을 통한 창의성 제어, `Streaming` 모드를 활용한 실시간 응답 구현.
- **Callbacks:** 모델 생성 과정 모니터링 및 이벤트 처리.

**2. Prompt Engineering**
- **Prompt Templates:** `PromptTemplate`을 활용한 재사용 가능한 프롬프트 구조 설계.
- **Role-Based Messaging:** `SystemMessage`, `HumanMessage`, `AIMessage`를 활용한 페르소나 및 역할 부여.

**3. Chains & LCEL (LangChain Expression Language)**
- **Chain Construction:** `.invoke()` 메서드를 활용한 체인 실행 및 결과 반환.
- **Output Parsers:** LLM의 Raw Text 출력을 원하는 포맷(List, JSON 등)으로 변환하는 파서 구현.
- **Chain Composition:** `|` (Pipe) 연산자를 활용한 직관적인 체인 연결.
- **Data Flow Management:** `RunnableMap` (Dictionary 구조)을 활용하여 이전 체인의 출력값(예: `{"advice": senior_chain}`)을 다음 체인의 문맥(Context)으로 전달하는 파이프라인 구축.

---

