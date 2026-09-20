<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=180&section=header&text=Parth%20Tyagi&fontSize=48&fontColor=fff&animation=fadeIn&fontAlignY=36&desc=Full-Stack%20AI%20Engineer%20%E2%80%94%20Multi-Agent%20Systems%2C%20RAG%20%26%20Real-Time%20Voice%20AI&descAlignY=57&descSize=15" width="100%"/>

### Systems-focused AI Engineer building deterministic multi-agent architectures, sub-350ms voice pipelines, and fault-tolerant RAG infrastructure — in production, not notebooks.

B.Tech Mathematics & Computing · Central University of Karnataka
Ex-AI Engineer Intern @ Intellexia AI · Ex-AI/ML Intern @ YBI Foundation

[![Resume](https://img.shields.io/badge/R%C3%A9sum%C3%A9-PDF-FF6B35?style=for-the-badge&logo=readdotcv&logoColor=white)](https://drive.google.com/file/d/1jSM277m2g84-18GVY-5ENhuDXU_djkG9/view?usp=sharing)
[![Portfolio](https://img.shields.io/badge/Portfolio-Live-58A6FF?style=for-the-badge&logo=vercel&logoColor=white)](https://parthtyagi-tech.github.io/portfolio/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/tyagiparth/)
[![Email](https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:parthtyagi3389@gmail.com)

</div>

---

## About

I build the layer between "an LLM can generate this" and "this is safe to ship." That means deterministic guardrails around agent output, async infrastructure that survives dropped connections, and evaluation pipelines that catch regressions before users do. Across three production systems and two engineering internships, the common thread is the same: **make the non-deterministic parts of AI systems behave like the deterministic parts of everything else.**

---

## Core Competencies

| Production AI & Agents | Backend & Distributed Systems | Data & Retrieval |
|---|---|---|
| LangGraph state-machine orchestration | GCP Cloud Run — stateless autoscaling | Pinecone vector search over domain corpora |
| Autonomous multi-agent swarms (Plan→Act→Observe→Adapt) | GCP Cloud Tasks — async pub/sub queues | Embedding pipelines with sub-ms intent routing |
| Deterministic guardrails over LLM output | Redis Streams — consumer groups, PEL, DLQ | PostgreSQL + SQLAlchemy persistence |
| Groq (Llama 3.3-70B), OpenAI, Vertex AI RAG | Webhook-driven long-running job pipelines | Auto-summarized conversational memory |
| Real-time voice agents (LiveKit + Deepgram, WebRTC) | FastAPI/Flask, `asyncio` concurrency, SSE streaming | Immutable, audit-logged decision trails |

---

## Featured Production Systems

### 1 · MediAssist — Clinical RAG Agent & Real-Time Voice AI

**Problem:** clinical Q&A can't afford LLM latency or hallucination risk on red-flag symptoms, and voice agents can't afford to block on retrieval.

```
User (voice/text)
      │
      ▼
┌─────────────────┐     P0 red-flag match      ┌──────────────────┐
│ Intent Router    ├──────────< 1ms ───────────▶│  Emergency Path   │
│ (Trie / Regex)   │                             │ (bypasses LLM)    │
└────────┬─────────┘                             └──────────────────┘
         │ non-emergency
         ▼
┌─────────────────┐   embed + retrieve   ┌──────────────┐
│  Flask + Groq    ├─────────────────────▶│   Pinecone   │
│  (Llama 3.3-70B) │◀─────────────────────┤ vector store │
└────────┬─────────┘                      └──────────────┘
         │ streamed tokens
         ▼
┌─────────────────────────┐   async offload   ┌───────────────────┐
│ Redis Streams            ├───────────────────▶│ Memory / Summary /│
│ (consumer groups + DLQ)  │                     │ Evals workers     │
└─────────────────────────┘                     └───────────────────┘
         │
         ▼
┌─────────────────┐  7 languages, full-duplex
│ LiveKit + Deepgram│  WebRTC voice, VAD turn detection
└──────────────────┘
```

| Constraint | Architectural Solution | Production Metric |
|---|---|---|
| LLM latency on emergency queries | Deterministic Trie/Regex intent router runs before any model call | **< 1ms** red-flag detection |
| Memory footprint on shared hosting | Lean Flask + Groq inference path, no heavyweight ML runtime resident | **< 50MB RAM** |
| Duplicate/failed async jobs | Redis Streams consumer groups + SHA-256 idempotency keys + DLQ routing | **< 350ms** end-to-end response |
| Silent quality regressions | 11-metric LLM-as-judge, 30-case offline benchmark + 20% online shadow evals in LangSmith, Brevo alerting on triage violations | Continuous regression detection |
| Multilingual real-time voice without blocking | LiveKit SFU + Deepgram STT/TTS, VAD-driven turn detection, self-healing session recovery | **7 languages**, full-duplex |

`Python` `Flask` `LangChain` `Groq (Llama 3.3-70B)` `Pinecone` `Redis Streams` `LiveKit` `Deepgram` `LangSmith`

[![Live Demo](https://img.shields.io/badge/Live%20Demo-medibot--22m0.onrender.com-success?style=for-the-badge)](https://medibot-22m0.onrender.com)
[![Repo](https://img.shields.io/badge/Source-Repository-181717?style=for-the-badge&logo=github)](https://github.com/parthTyagi-tech/medibot)

---

### 2 · Dynamic Pricing Intelligence Platform — Autonomous Multi-Agent Swarm

**Problem:** repricing products across 14 live marketplaces needs continuous agent reasoning, but no agent should ever be able to set a price that loses money or looks like a hallucination.

```
┌────────────┐    goal    ┌─────────────┐    scrape     ┌───────────┐
│ Supervisor │───────────▶│  Scrapers   │──────────────▶│ Reasoning │
│   Agent    │            │  (x N)      │               │   Agent   │
└─────┬──────┘            └─────────────┘               └─────┬─────┘
      │  Plan → Act → Observe → Adapt (continuous loop)        │
      │                                                        ▼
      │                                              ┌───────────────────┐
      │                                              │  Deterministic     │
      │                                              │  Guardrail Layer   │
      │                                              │  Price ≥ Cost+Margin│
      │                                              │  ±50% sanity bound │
      │                                              └─────────┬──────────┘
      │                                                        │ passes
      ▼                                                        ▼
┌─────────────┐   GCP Cloud Tasks    ┌────────────┐   audit    ┌────────────┐
│  Approver   │◀────pub/sub queue────┤  Task Fan- │───write───▶│ Immutable  │
│   Agent     │                      │  out (async)│            │ Audit Log  │
└─────┬───────┘                      └────────────┘            └────────────┘
      │ SSE stream
      ▼
┌─────────────────┐
│ React Dashboard  │  live agent reasoning trace, human-in-the-loop sign-off
└──────────────────┘
```

| Constraint | Architectural Solution | Production Metric |
|---|---|---|
| LLM agents can hallucinate a price | Hard margin floor (`Price ≥ Cost + Margin`) + ±50% sanity bound enforced in code, not prompted | Hallucinated pricing made **structurally impossible** |
| Sequential agent execution is too slow for 14 marketplaces | Parallel fan-out via `asyncio.gather` over async pub/sub task queues | **~3x throughput** vs. sequential, **sub-3s** decision cycle |
| No visibility into why a price changed | Every approval persisted to an immutable, JWT-scoped RBAC audit log | Every decision reviewable & reversible |
| Operators need to watch reasoning live, not just outcomes | Agent reasoning steps streamed to a React dashboard via SSE | Real-time human-in-the-loop oversight |

`Python` `LangGraph` `asyncio` `GCP Cloud Tasks` `React` `PostgreSQL` `JWT Auth`

[![Repo](https://img.shields.io/badge/Source-Repository-181717?style=for-the-badge&logo=github)](https://github.com/parthTyagi-tech/dynamic-pricing-intelligence-platform)

---

### 3 · AI-Driven Fitness Intelligence System — Full-Stack Applied ML

**Problem:** ship a biometric prediction product end-to-end, owned solo — model, API, auth, database, and deployment — for real active users, not a demo.

```
┌──────────┐   Google OAuth 2.0   ┌───────────┐   REST   ┌───────────────┐
│  Client   │─────────────────────▶│  Flask API │─────────▶│ Regression Model│
└──────────┘                       └─────┬─────┘          │ (12 biometrics) │
                                          │                └───────────────┘
                                          ▼
                                   ┌──────────────┐
                                   │ PostgreSQL    │  user state + history
                                   └──────────────┘
```

| Constraint | Architectural Solution | Production Metric |
|---|---|---|
| Predicting 12 correlated biometric outputs accurately | Multi-target regression pipeline, tuned feature set | **0.21% MAE**, **R² = 0.995** |
| Real users need fast responses | Optimized inference path in the Flask API layer | **< 50ms** per request |
| Full lifecycle ownership | Solo-owned: training, API, OAuth, schema, deployment on Render | Live app serving active end-users |

`Python` `XGBoost` `scikit-learn` `Flask` `PostgreSQL` `Google OAuth`

[![Live App](https://img.shields.io/badge/Live%20App-ai--fitness--api--68n1.onrender.com-success?style=for-the-badge)](https://ai-fitness-api-68n1.onrender.com)
[![Repo](https://img.shields.io/badge/Source-Repository-181717?style=for-the-badge&logo=github)](https://github.com/parthTyagi-tech/AI-Fitness-API)

---

## Professional Engineering Footprint

### AI Engineer Intern — Intellexia Tech Pvt. Ltd. · *May – Jul 2026*

Worked on **Transpera**, an AI video dubbing platform built on the HeyGen API.

- **Async job orchestration:** designed a webhook-driven pipeline on **GCP Cloud Tasks** to manage long-running, multi-minute HeyGen translation jobs without holding request threads open or dropping sockets.
- **Stateless migration:** refactored backend storage from local disk to **Google Cloud Storage**, eliminating node-level filesystem dependencies and unlocking horizontal autoscaling on **Google Cloud Run**.
- **Voice agent architecture:** built a real-time multilingual voice agent on a cyclic **LangGraph** state-machine backed by **Vertex AI RAG**, preserving context across multi-turn conversations.

`GCP Cloud Tasks` `Google Cloud Storage` `Google Cloud Run` `LangGraph` `Vertex AI RAG`

### AI/ML Intern — YBI Foundation · *May – Jul 2025*

- Engineered end-to-end classification and regression pipelines (**scikit-learn**, **Pandas**), tuning models to **97% predictive accuracy** on structured evaluation benchmarks.
- Applied cross-validation and hyperparameter tuning to raise baseline classification **F1-score from 0.70 → 0.85**.
- Ran exploratory data analysis and visualization (**NumPy**, **Matplotlib/Seaborn**) to drive feature design and model selection.

`scikit-learn` `Pandas` `NumPy` `Matplotlib/Seaborn`

---

## Engineering Principles

| Default I reject | What I build instead | Why it matters in production |
|---|---|---|
| Raw LLM output as the decision | Deterministic guardrails wrapping the model | Hallucinations become structurally impossible, not just unlikely |
| Synchronous blocking calls | Webhook- and queue-driven async pipelines | Long-running jobs never hold a request thread open |
| Stateful local disk | GCS-backed, stateless services | Real horizontal autoscaling on Cloud Run |
| Sequential agent execution | Parallel fan-out via `asyncio.gather` | Sub-3s decision cycles instead of minutes |
| Black-box outputs | Immutable audit logs + streamed reasoning traces | Every decision is reviewable and reversible |
| "It runs in the notebook" | Live public URL, real auth, real database | Shipped beats demoed |

---

## Technology Stack

**Languages**
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![R](https://img.shields.io/badge/R-276DC3?style=flat-square&logo=r&logoColor=white)
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=flat-square)

**AI & Agent Orchestration**
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=chainlink&logoColor=white)
![Vertex AI](https://img.shields.io/badge/Vertex%20AI-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Groq](https://img.shields.io/badge/Groq-F55036?style=flat-square)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)
![LiveKit](https://img.shields.io/badge/LiveKit-D92D20?style=flat-square)
![Deepgram](https://img.shields.io/badge/Deepgram-13EF93?style=flat-square&logoColor=black)
![LangSmith](https://img.shields.io/badge/LangSmith-1C3C3C?style=flat-square)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-0E76A8?style=flat-square)

**Backend & Distributed Systems**
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)
![Redis](https://img.shields.io/badge/Redis%20Streams-DC382D?style=flat-square&logo=redis&logoColor=white)
![Cloud Tasks](https://img.shields.io/badge/GCP%20Cloud%20Tasks-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)

**Storage & Infrastructure**
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white)
![Pinecone](https://img.shields.io/badge/Pinecone-00C389?style=flat-square)
![JWT](https://img.shields.io/badge/JWT%20Auth-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Cloud Run](https://img.shields.io/badge/Cloud%20Run-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Cloud Storage](https://img.shields.io/badge/Cloud%20Storage-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Render](https://img.shields.io/badge/Render-46E3B7?style=flat-square&logo=render&logoColor=black)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)

---

<div align="center">

### Open to Full-Stack AI Engineer, LLM/RAG Engineer, and Applied AI Systems roles

[![Portfolio](https://img.shields.io/badge/View%20Full%20Portfolio-58A6FF?style=for-the-badge&logo=vercel&logoColor=white)](https://parthtyagi-tech.github.io/portfolio/)
[![Email](https://img.shields.io/badge/parthtyagi3389%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:parthtyagi3389@gmail.com)

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=100&section=footer" width="100%"/>

</div>
