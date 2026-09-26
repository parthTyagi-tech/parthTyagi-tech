<div align="center">

# Parth Tyagi

### GenAI Infrastructure & Agentic Systems Engineer
Deterministic guardrails over non-deterministic models · Sub-350ms voice pipelines · Fault-tolerant RAG at production scale

<br/>

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=for-the-badge)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Pinecone](https://img.shields.io/badge/Pinecone-00C389?style=for-the-badge)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![GCP](https://img.shields.io/badge/Google%20Cloud-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

[![Resume](https://img.shields.io/badge/R%C3%A9sum%C3%A9-PDF-FF6B35?style=for-the-badge&logo=readdotcv&logoColor=white)](https://drive.google.com/file/d/1uaBkoc8SGx50-5laFi3tSnLhOo8g2Bf3/view?usp=sharing)
[![Portfolio](https://img.shields.io/badge/Portfolio-Live-58A6FF?style=for-the-badge&logo=vercel&logoColor=white)](https://parthtyagi-tech.github.io/portfolio/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/tyagiparth/)
[![Email](https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:parthtyagi3389@gmail.com)

</div>

---

## About Me

I build the layer between *"an LLM can generate this"* and *"this is safe to ship."* That means deterministic guardrails wrapped around model output, async queue-driven infrastructure that survives dropped connections, and evaluation pipelines that catch regressions before a user does. I'm a B.Tech Mathematics & Computing undergrad at Central University of Karnataka, but the systems below run in production, not notebooks — real auth, real databases, real traffic.

---

## Core Technical Arsenal

<table>
<tr>
<td valign="top" width="50%">

**AI / ML & Orchestration**
- LangGraph (state-machine agent orchestration)
- LangChain, LangSmith (eval & observability)
- Groq (Llama 3.3-70B), OpenAI, Vertex AI RAG
- LiveKit + Deepgram (real-time voice, WebRTC)
- scikit-learn, XGBoost

</td>
<td valign="top" width="50%">

**Data & Retrieval**
- Pinecone (vector search over domain corpora)
- PostgreSQL + SQLAlchemy
- Redis Streams (consumer groups, PEL, DLQ)
- Embedding pipelines, sub-ms intent routing
- Immutable, audit-logged decision trails

</td>
</tr>
<tr>
<td valign="top" width="50%">

**Deployment & MLOps**
- Docker
- GCP Cloud Run (stateless autoscaling)
- GCP Cloud Tasks (async pub/sub queues)
- Render, Vercel
- CI/CD, webhook-driven job pipelines

</td>
<td valign="top" width="50%">

**Languages & Core Tools**
- Python, JavaScript, SQL
- C++, R, MATLAB
- Git, FastAPI, React, Vite
- JWT Auth, Google OAuth 2.0

</td>
</tr>
</table>

---

## Featured Production Systems

### MediAssist — Clinical RAG Agent & Real-Time Voice AI
**Purpose:** Clinical Q&A that can't afford LLM latency or hallucination risk on red-flag symptoms, paired with a voice agent that can't afford to block on retrieval.

**Key Tech:** `Flask` `Groq (Llama 3.3-70B)` `Pinecone` `Redis Streams` `LiveKit` `Deepgram` `LangSmith`

**Impact:**
- Deterministic Trie/Regex intent router resolves emergency queries in **<1ms**, bypassing the LLM entirely
- Lean inference path holds the service under **<50MB RAM** on shared hosting
- Redis Streams consumer groups + SHA-256 idempotency keys + DLQ routing keep end-to-end response **<350ms**
- 11-metric LLM-as-judge pipeline (30-case offline benchmark + 20% online shadow evals) catches quality regressions before users do
- Full-duplex voice across **7 languages** via LiveKit SFU + Deepgram STT/TTS with VAD-driven turn detection

<!-- REPLACE_WITH_LIVE_DEMO_URL -->
[![Live Demo](https://img.shields.io/badge/Live%20Demo-medibot--22m0.onrender.com-success?style=for-the-badge)](https://medibot-22m0.onrender.com)
[![Repo](https://img.shields.io/badge/Source-Repository-181717?style=for-the-badge&logo=github)](https://github.com/parthTyagi-tech/medibot)

---

### Dynamic Pricing Intelligence Platform — Autonomous Multi-Agent Swarm
**Purpose:** Reprice products across 14 live marketplaces via continuous agent reasoning — without ever letting an agent set a price that loses money or looks like a hallucination.

**Key Tech:** `LangGraph` `asyncio` `GCP Cloud Tasks` `React` `PostgreSQL` `JWT Auth`

**Impact:**
- Supervisor → Scrapers → Reasoning → Approver agents run a continuous **Plan → Act → Observe → Adapt** loop
- Hard margin floor (`Price ≥ Cost + Margin`) + ±50% sanity bound enforced **in code, not prompted** — hallucinated pricing made structurally impossible
- Parallel fan-out via `asyncio.gather` over async pub/sub queues delivers **~3x throughput** and a **sub-3s** decision cycle
- Every approval persisted to an immutable, JWT-scoped RBAC audit log — every decision reviewable and reversible
- Agent reasoning streamed live to a React dashboard via SSE for human-in-the-loop sign-off

[![Repo](https://img.shields.io/badge/Source-Repository-181717?style=for-the-badge&logo=github)](https://github.com/parthTyagi-tech/dynamic-pricing-intelligence-platform)

---

### AI-Driven Fitness Intelligence System — Full-Stack Applied ML
**Purpose:** Ship a biometric prediction product end-to-end, solo-owned — model, API, auth, database, and deployment — for real active users.

**Key Tech:** `XGBoost` `scikit-learn` `Flask` `PostgreSQL` `Google OAuth`

**Impact:**
- Multi-target regression across 12 correlated biometric outputs at **0.21% MAE**, **R² = 0.995**
- Optimized Flask inference path serves predictions in **<50ms**
- Full lifecycle solo ownership: training, API, OAuth, schema design, and deployment on Render

[![Live App](https://img.shields.io/badge/Live%20App-ai--fitness--api--68n1.onrender.com-success?style=for-the-badge)](https://ai-fitness-api-68n1.onrender.com)
[![Repo](https://img.shields.io/badge/Source-Repository-181717?style=for-the-badge&logo=github)](https://github.com/parthTyagi-tech/AI-Fitness-API)

---

## Professional Engineering Footprint

**AI Engineer Intern — Intellexia Tech Pvt. Ltd.** · *May – Jul 2026*
Built Transpera, an AI video dubbing platform on the HeyGen API — a webhook-driven pipeline on **GCP Cloud Tasks** for long-running jobs, a stateless migration to **Google Cloud Storage** unlocking **Cloud Run** autoscaling, and a real-time multilingual voice agent on a cyclic **LangGraph** state machine backed by **Vertex AI RAG**.

**AI/ML Intern — YBI Foundation** · *May – Jul 2025*
Engineered classification and regression pipelines (**scikit-learn**, **Pandas**) reaching **97% predictive accuracy**, raised baseline classification **F1-score from 0.70 → 0.85** through cross-validation and hyperparameter tuning.

---

## GitHub Stats & Connect

<div align="center">

<!-- REPLACE_WITH_GITHUB_USERNAME if different from parthTyagi-tech -->
![GitHub Stats](https://github-readme-stats.vercel.app/api?username=parthTyagi-tech&show_icons=true&theme=dark&hide_border=true)
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=parthTyagi-tech&layout=compact&theme=dark&hide_border=true)

<br/>

**Open to Full-Stack AI Engineer, LLM/RAG Engineer, and Applied AI Systems roles**

[![Portfolio](https://img.shields.io/badge/View%20Full%20Portfolio-58A6FF?style=for-the-badge&logo=vercel&logoColor=white)](https://parthtyagi-tech.github.io/portfolio/)
[![Email](https://img.shields.io/badge/parthtyagi3389%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:parthtyagi3389@gmail.com)

</div>
