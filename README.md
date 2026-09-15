<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=170&section=header&text=Parth%20Tyagi&fontSize=50&fontColor=fff&animation=fadeIn&fontAlignY=36&desc=Full-Stack%20AI%20Engineer%20%7C%20Multi-Agent%20Systems%20%7C%20RAG%20%26%20Voice%20AI&descAlignY=57&descSize=15" width="100%"/>

**Full-Stack AI Engineer building deterministic multi-agent architectures, low-latency voice AI, and scalable RAG pipelines.**

B.Tech Mathematics & Computing @ Central University of Karnataka · Production systems on GCP Cloud Run, Cloud Tasks, and Vertex AI

[![Resume](https://img.shields.io/badge/Résumé-PDF-FF6B35?style=for-the-badge&logo=readdotcv&logoColor=white)](https://parthtyagi-tech.github.io/portfolio/)
[![Portfolio](https://img.shields.io/badge/Portfolio-Live-58A6FF?style=for-the-badge&logo=vercel&logoColor=white)](https://parthtyagi-tech.github.io/portfolio/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/tyagiparth/)
[![Email](https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:parthtyagi3389@gmail.com)

</div>

---

## Production Impact & Core Competencies

| Production AI & Agents | Backend & Distributed Systems | Data & Retrieval Systems |
|---|---|---|
| LangGraph state-machine orchestration | GCP Cloud Run (stateless autoscaling) | Pinecone vector search over medical corpora |
| Autonomous multi-agent swarms (Plan→Act→Observe→Adapt) | GCP Cloud Tasks (async pub/sub queues) | Embedding pipelines + intent-based routing |
| Deterministic guardrails over raw LLM output | Webhook-driven long-running job pipelines | PostgreSQL + SQLAlchemy persistence layers |
| Groq (Llama 3.3-70B), OpenAI, Vertex AI RAG | FastAPI / Flask, `asyncio.gather` concurrency | Auto-summarized conversational memory |
| Real-time voice agents (LiveKit, Deepgram, VAD) | Server-Sent Events for streaming reasoning traces | Immutable audit logs for decision traceability |

---

## Featured Production Systems

### 1. Dynamic Pricing Intelligence Platform — *Flagship Multi-Agent System*

> Autonomous agent swarm that extracts, verifies, and reprices products across live marketplaces with governed, explainable decisions.

- **Architecture —** Goal-driven agent swarm (Supervisor, Scrapers, Reasoning, Approver) running continuous **Plan-Act-Observe-Adapt** loops; orchestration scaled through asynchronous pub/sub task queues (local / **GCP Cloud Tasks**), with agent reasoning steps streamed to a React dashboard over **Server-Sent Events**.
- **Determinism over probability —** Hard margin floors (`Price ≥ Cost + Margin`) and ±50% sanity bounds intercept LLM output before it reaches the pricing engine, eliminating hallucinated decisions; every approval persists to an immutable audit log with JWT-scoped RBAC and human-in-the-loop sign-off.
- **Metrics —** Sub-3s end-to-end decision cycles via parallel `asyncio.gather` fan-out · **14 marketplaces** continuously monitored · ~3× throughput vs. sequential agent execution.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square)
![Asyncio](https://img.shields.io/badge/Asyncio-306998?style=flat-square)
![GCP Cloud Tasks](https://img.shields.io/badge/Cloud%20Tasks-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

[![Repo](https://img.shields.io/badge/Source-Repository-181717?style=for-the-badge&logo=github)](https://github.com/parthTyagi-tech/dynamic-pricing-intelligence-platform)

---

### 2. MediAssist — *Production RAG + Real-Time Voice AI*

> Retrieval-grounded medical assistant with multilingual voice, persistent memory, and streaming responses.

- **Architecture —** Flask + LangChain RAG pipeline over **Pinecone**, served by **Groq (Llama 3.3-70B)** with intent-based routing that separates retrieval-bound queries from conversational turns; responses stream token-by-token rather than blocking on full generation.
- **Voice layer —** Real-time multilingual agent across **7 languages** using LiveKit, Deepgram, and VAD-driven turn detection, with self-healing session recovery on dropped connections.
- **State —** Persistent user memory with auto-summarized chat history via SQLAlchemy, keeping context retrieval effectively zero-latency as history grows.
- **Infrastructure —** Deployed on Render behind Flask + Gunicorn.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=chainlink&logoColor=white)
![Groq](https://img.shields.io/badge/Groq%20Llama%203.3--70B-F55036?style=flat-square)
![Pinecone](https://img.shields.io/badge/Pinecone-00C389?style=flat-square)
![LiveKit](https://img.shields.io/badge/LiveKit-D92D20?style=flat-square)
![Deepgram](https://img.shields.io/badge/Deepgram-13EF93?style=flat-square&logoColor=black)

[![Live Demo](https://img.shields.io/badge/Live%20Demo-medibot--22m0.onrender.com-success?style=for-the-badge)](https://medibot-22m0.onrender.com)
[![Repo](https://img.shields.io/badge/Source-Repository-181717?style=for-the-badge&logo=github)](https://github.com/parthTyagi-tech/medibot)

---

### 3. AI Fitness Intelligence System — *Production ML + Low-Latency Inference*

> Full-stack biometric prediction platform serving real users, owned end-to-end from training to deployment.

- **Architecture —** Regression pipeline predicting **12 biometric outputs**, wrapped in a Flask inference API with Google OAuth and PostgreSQL-backed user state.
- **Metrics —** **0.21% MAE**, R² ≈ 0.995, sustained **sub-50ms backend inference** per request.
- **Ownership —** Feature design, model training and tuning, API surface, auth, database schema, and production deployment on Render — single-owner across the full stack.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-0E76A8?style=flat-square)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![OAuth](https://img.shields.io/badge/Google%20OAuth-4285F4?style=flat-square&logo=google&logoColor=white)

[![Live App](https://img.shields.io/badge/Live%20App-ai--fitness--api--68n1.onrender.com-success?style=for-the-badge)](https://ai-fitness-api-68n1.onrender.com)
[![Repo](https://img.shields.io/badge/Source-Repository-181717?style=for-the-badge&logo=github)](https://github.com/parthTyagi-tech/AI-Fitness-API)

---

## Professional Engineering Footprint

**AI Engineer Intern — Intellexia Tech Pvt. Ltd.** · May 2026 – July 2026

- Deployed **Transpera**, an AI video dubbing platform, architecting a webhook-driven asynchronous job pipeline on **GCP Cloud Tasks** to manage long-running HeyGen API translation jobs without holding request threads open.
- Refactored backend storage from local disk to **Google Cloud Storage**, removing stateful dependencies and unblocking stateless horizontal autoscaling on **Google Cloud Run**.
- Built a real-time multilingual voice agent on a **LangGraph state-machine** architecture backed by **Vertex AI RAG**, maintaining context integrity across conversational turns.

**AI/ML Intern — YBI Foundation** · May 2025 – July 2025

- Engineered end-to-end classification and regression pipelines (scikit-learn, Pandas); cross-validation and hyperparameter tuning raised classification F1 from **0.70 → 0.85** and improved baseline predictive accuracy by **97%**.

---

## System Architecture Philosophy

| Default I reject | What I build instead | Why it matters in production |
|---|---|---|
| Raw LLM output as the decision | Deterministic guardrails wrapping the model | Hallucinations become impossible, not improbable |
| Synchronous blocking calls | Webhook + queue-driven async pipelines | Long-running jobs never hold a request thread |
| Stateful local disk | GCS-backed stateless services | Horizontal autoscaling on Cloud Run |
| Sequential agent execution | Parallel fan-out via `asyncio.gather` | Sub-3s decision cycles instead of minutes |
| Black-box outputs | Immutable audit logs + streamed reasoning traces | Every decision is reviewable and reversible |
| "It runs in the notebook" | Live public URL, auth, and a real database | Shipped beats demoed |

---

## Tech Stack

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white)
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=for-the-badge)

**AI & Agent Frameworks**

![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=for-the-badge)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=chainlink&logoColor=white)
![Vertex AI](https://img.shields.io/badge/Vertex%20AI-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)
![Groq](https://img.shields.io/badge/Groq-F55036?style=for-the-badge)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)
![LiveKit](https://img.shields.io/badge/LiveKit-D92D20?style=for-the-badge)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)

**Cloud & Distributed Systems**

![Cloud Run](https://img.shields.io/badge/Cloud%20Run-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)
![Cloud Tasks](https://img.shields.io/badge/Cloud%20Tasks-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)
![GCS](https://img.shields.io/badge/Cloud%20Storage-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Render](https://img.shields.io/badge/Render-46E3B7?style=for-the-badge&logo=render&logoColor=black)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)

**Databases & Retrieval**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=for-the-badge&logo=sqlalchemy&logoColor=white)
![Pinecone](https://img.shields.io/badge/Pinecone-00C389?style=for-the-badge)
![JWT](https://img.shields.io/badge/JWT%20Auth-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)

---

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=parthTyagi-tech&show_icons=true&theme=tokyonight&hide_border=true&rank_icon=github&include_all_commits=true" width="49%" />
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=parthTyagi-tech&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" width="40%" />

</div>

---

<div align="center">

**Open to Full-Stack AI Engineer, LLM/RAG Engineer, and Applied AI Systems roles.**

[![Portfolio](https://img.shields.io/badge/View%20Full%20Portfolio-58A6FF?style=for-the-badge&logo=vercel&logoColor=white)](https://parthtyagi-tech.github.io/portfolio/)
[![Email](https://img.shields.io/badge/parthtyagi3389@gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:parthtyagi3389@gmail.com)

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=100&section=footer" width="100%"/>

</div>
