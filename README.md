# 🦜🔗 LangChain Implementation & Fullstack GPT

> **Implementation of exploring RAG, Memory, and Chains through various LLM services.**

## 🛠️ Tech Stack
- **Framework:** `LangChain`, `FastAPI`, `Streamlit`
- **Language Model:** `OpenAI (GPT-3.5-turbo)`, `Google Gemini`
- **Language:** `Python 3.10+`
- **Tools:** `Git/GitHub`, `LangChain`

---

## 📚 Learning Progress

### 🔹 LangChain Basics (Current)
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

**4. Advanced Prompting Techniques**
- Few-Shot Learning: 모델에게 예제(`Examples`)를 제공하여 답변의 톤앤매너와 형식을 유도하는 `FewShotPromptTemplate` 및 `FewShotChatMessagePromptTemplate` 구현.
- Dynamic Example Selection: 입력의 길이나 무작위 조건에 따라, 프롬프트에 포함될 예제를 동적으로 선택하는 `LengthBasedExampleSelector` 및 `Custom Selector(Random)` 활용.
- Prompt Pipeline: 역할 부여(Intro), 예제(Example), 시작(Start) 등 여러 프롬프트 조각을 파이프라인으로 연결하여 복잡한 지시사항을 체계적으로 구성 `(PipelinePromptTemplate)`.
- Prompt Serialization: 프롬프트 템플릿을 json이나 yaml 파일로 저장하고 로드하여 코드와 프롬프트 데이터의 분리 관리.

**5. Optimization & Efficiency**
- Caching Strategies: `InMemoryCache` 및 `SQLiteCache`를 도입하여 동일한 질문에 대한 중복 API 호출을 방지, 비용 절감 및 응답 속도 최적화.
- Cost Tracking: `get_openai_callback`을 활용하여 체인 실행 시 소모되는 토큰 양과 예상 비용을 실시간으로 추적 및 모니터링 .
- Model Serialization: 설정된 LLM 모델(파라미터 포함)을 저장(save)하고 불러오는(`load_llm`) 과정을 통해 실험 환경의 재현성 확보

**6. Memory & Context Management**
- Memory Types 대화의 맥락 유지를 위한 다양한 메모리 전략 학습 및 구현
  - `ConversationBufferMemory`: 모든 대화 기록을 Raw Text로 저장-
  - `ConversationBufferWindowMemory`: 최신 $k$개의 대화만 유지하는 슬라이딩 윈도우 방식
      1.`ConversationSummaryMemory`: LLM을 활용해 대화 내용을 요약하여 저장(토큰 절약)
      2.`ConversationSummaryBufferMemory`: 최근 대화는 그대로 유지하고, 토큰 제한 (max_token_limit)을 넘어가면 오래된 대화부터 요약하는 하이브리드 방식
      3.`ConversationKGMemory`: 대화 속 엔티티(Entity) 간의 관계를 지식 그래프(Knowledge Graph) 형태로 저장
- **Memory Integration with LCEL**
  - `RunnablePassthrough.assign`을 활용하여 체인 실행(invoke) 시점에 메모리를 동적으로 로드(load_memory_variables)하고 프롬프트에 주입하는 파이프라인 구축
  - Context Injection: `MessagesPlaceholder`를 사용하여 유동적인 길이의 대화 내역(chat_history)을 프롬프트 템플릿의 적절한 위치에 할당하는 구조 설계
  - State Management: `save_context` 메서드를 통해 사용자 입력(Input)과 AI 응답(Output)을 쌍(Pair)으로 메모리에 지속적으로 업데이트하여 멀티턴(Multi-turn) 대화 구현

---




