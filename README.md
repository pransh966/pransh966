<div align="center">

# Hi, I'm Pranshul Khokhar 👋

### AI/ML & Full-Stack Engineer — Applied ML, RAG Systems & Web Applications

I design, build, and ship ML, LLM, and full-stack web systems end to end: data / model pipeline → authenticated API → deployed interface.

[![SentinelAI](https://img.shields.io/badge/Live%20Demo-SentinelAI-3E63DD?style=for-the-badge)](https://sentinel-ai-six-nu.vercel.app)
[![RepoMind](https://img.shields.io/badge/RAG%20Project-RepoMind-6E56CF?style=for-the-badge)](https://github.com/pransh966/RepoMind)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Pranshul%20Khokhar-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/pranshul-khokhar-12072005pransh/)
[![Email](https://img.shields.io/badge/Email-pranshulkhokhar%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:pranshulkhokhar@gmail.com)

</div>

---

### About me

I build ML and LLM products that ship as complete systems, not notebooks: the model is served behind a typed API, the API sits behind auth and a database, and there is a deployed interface on top. Two of those are live in my portfolio: **SentinelAI**, a fraud detection platform with real-time scoring and per-prediction SHAP explainability, and **RepoMind**, a retrieval-augmented (RAG) assistant that answers questions about a codebase with citations to the exact file and line range. Beyond ML, I build full-stack web applications for real products and brands (**Cheerish Nutrition**, **GoCrew**). Day to day I work across Python, FastAPI, PostgreSQL, React, and the retrieval/embedding layer underneath most LLM products.

- 🔭 **Building:** RepoMind (AST-aware RAG over codebases), SentinelAI (real-time + batch fraud detection), and GoCrew (group travel platform)
- 🎯 **Focus areas:** ML system design, retrieval architecture, model monitoring
- 💬 **Ask me about:** LightGBM/scikit-learn pipelines, SHAP explainability, FastAPI backends, FAISS retrieval, RAG system design, full-stack web development
- 🏆 **Recognition:** Top 10 of 100+ teams in a 24-hour hackathon
- 🎓 **Education:** B.Tech (AI/ML), GGSIPU

---

### 🛡️ Featured project — SentinelAI

**AI-powered fraud detection platform** — real-time transaction scoring, batch analysis, and per-prediction explainability. Trained on the IEEE-CIS Fraud Detection dataset (~590K transactions, 424 engineered features), served through FastAPI, with a React dashboard for scoring, batch analysis, and history.

**Engineering highlights:**
- Live decision threshold slider (0.10–0.90) with Aggressive/Balanced/Conservative presets — see precision/recall trade-offs instantly, no retraining
- Per-transaction **SHAP explainability**, row-aware for batch uploads, plus an aggregate "what's driving fraud risk" view
- Searchable, filterable, sortable batch results table with per-row SHAP inspection
- Metrics chosen for the problem — precision/recall surfaced explicitly instead of accuracy, since the data is ~3.5% fraud
- Live-updating dashboard: trend, probability distribution, risk breakdown, threshold impact simulator

<table>
<tr>
<td width="50%"><img src="./assets/dashboard.png" alt="SentinelAI Dashboard" /></td>
<td width="50%"><img src="./assets/batch-predict.png" alt="SentinelAI Batch Predict" /></td>
</tr>
</table>

**Stack:** LightGBM · scikit-learn · SHAP · FastAPI · PostgreSQL (Neon) · React 19 · Tailwind · Recharts
**Deployed on:** Vercel (frontend) + Render (backend), PostgreSQL on Neon

🔗 **[Live demo](https://sentinel-ai-six-nu.vercel.app)** — register and try it, no setup
📄 **[API docs](https://sentinel-ai5.onrender.com/docs)**

---

### 🧠 Featured project — RepoMind

**A codebase-aware RAG assistant** — point it at a repo and ask questions about the code in plain English; every answer is grounded in the actual source and cited down to the file and line range it came from.

```
repo files --> AST-aware chunking --> local embeddings --> FAISS index
                                                                 |
user question --> embed --> retrieve top-k --> LLM (grounded prompt) --> answer + citations
```

**Design decisions:**
- **AST-aware chunking, not fixed-size windows.** Fixed-size splitting routinely cuts a function in half mid-body and hurts retrieval quality. RepoMind parses Python with the `ast` module and chunks at function/class boundaries, so retrieval returns whole, coherent units of code — non-Python files fall back to a structure-aware sliding window rather than a fixed character count.
- **Grounded answers, not just retrieval.** The system prompt explicitly instructs the model to answer only from retrieved context and say so when it can't — a concrete guardrail against hallucination.
- **Local embeddings, pluggable generation.** Embedding runs locally via `sentence-transformers` — free, fast, works offline. Only the final answer-generation call needs a paid API key, and that provider is swappable (OpenAI / Anthropic / a zero-key mock for local dev and tests).
- **Multi-user by design** — JWT auth, per-user repos and query history in PostgreSQL, connect a repo by git URL or `.zip` upload, each repo gets its own FAISS index.
- **Rate limiting and a documented scaling path** — the repo spells out what changes at higher load: swap `IndexFlatIP` for `IndexHNSWFlat`, move state out of process, add streaming.

**Benchmarked:** ingestion pipeline run against a real open-source repo (`psf/requests`) — 37 files scanned into 254 AST-aware chunks in ~62ms on a single process, no GPU.

**Stack:** Python · FastAPI · FAISS · sentence-transformers · PostgreSQL · JWT · OpenAI/Anthropic-pluggable LLM layer · Docker
**Status:** source is public and fully documented. The hosted demo is being redeployed: I'm moving the embedding model out of the build image (smaller quantized model, lazy-loaded on first request) to fit the 512MB container limit.

🔗 **[Source & full README](https://github.com/pransh966/RepoMind)** — setup, API reference, architecture notes, and known limitations

---

### 🧰 Skills & tools

**Languages**
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white)

**Machine Learning**
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=flat-square&logo=keras&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-black?style=flat-square)
![SHAP](https://img.shields.io/badge/Explainability-SHAP-8A2BE2?style=flat-square)

**Retrieval & LLM systems**
![FAISS](https://img.shields.io/badge/FAISS-0467DF?style=flat-square)
![sentence-transformers](https://img.shields.io/badge/sentence--transformers-FF6B6B?style=flat-square)
![OpenAI API](https://img.shields.io/badge/OpenAI%20API-412991?style=flat-square&logo=openai&logoColor=white)
![Anthropic API](https://img.shields.io/badge/Anthropic%20API-D97757?style=flat-square)
![RAG](https://img.shields.io/badge/RAG-Grounded%20Generation-6E56CF?style=flat-square)

**Data**
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square)
![Seaborn](https://img.shields.io/badge/Seaborn-3776AB?style=flat-square)

**Full-stack web development**
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Tailwind](https://img.shields.io/badge/TailwindCSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![REST APIs](https://img.shields.io/badge/REST%20APIs-009688?style=flat-square)
![Responsive UI](https://img.shields.io/badge/Responsive%20UI-6E56CF?style=flat-square)

**Backend**
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square)
![JWT](https://img.shields.io/badge/JWT-black?style=flat-square&logo=jsonwebtokens)

**Frontend**
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Tailwind](https://img.shields.io/badge/TailwindCSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Recharts](https://img.shields.io/badge/Recharts-22B5BF?style=flat-square)

**Deployment & Tools**
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-black?style=flat-square&logo=vercel&logoColor=white)
![Render](https://img.shields.io/badge/Render-46E3B7?style=flat-square&logo=render&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)

---

### 🌐 Full-stack web development

#### 🧭 GoCrew — group travel platform *(in development)*

**Curated group trips for people who want to travel but don't have the right people to go with.** Travelers join a trip and travel as a "crew" led by a trip captain; GoCrew runs a small set of vetted operators instead of an open marketplace, so quality and safety stay controlled.

**Product design:**
- Three roles with role-based access: **Traveler** (browse, book, join the crew, review), **Captain** (trip manifest, incident log), **Admin** (trips, operators, costs, refunds, reports)
- **Minimum-group-size logic** — a trip confirms automatically once the minimum is reached, otherwise it is cancelled and everyone is refunded
- **Oversell-safe booking** and **Razorpay payments** with verified webhooks and refunds
- Per-trip profit & loss and operator payables for the admin
- Launch scope: weekend treks and road trips from Delhi NCR

**Architecture:** modular monolith (Router → Schema → Service → Repository per module) with an event bus and idempotency checks on payments, designed so it can scale without a rewrite.

**Stack:** FastAPI · PostgreSQL · SQLAlchemy · Alembic · Redis · Razorpay · Cloudinary · Docker · GitHub Actions

#### 🥗 Cheerish Nutrition — nutrition brand website

Full-stack web application, live at **[cheerishnutrition.com](https://cheerishnutrition.com)**.

---

### 📌 More projects

**Cinematch — Movie Recommendation System** — `Python · FastAPI · FAISS · Vanilla JS`
Embedding-based recommendation engine across 100,000+ ratings, 1,600+ movies, and 900+ users, using FAISS for approximate nearest-neighbor retrieval (0.71 avg top-1 / 0.64 avg top-5 cosine similarity on held-out queries). Productionized from a Streamlit prototype into a FastAPI service with a framework-free JS frontend: API keys kept server-side and out of source control, recommendation logic separated from presentation, an in-process response cache, and a `/health` endpoint that reports real service status.

**Social Media REST API** — `FastAPI · PostgreSQL · SQLAlchemy · JWT`
RESTful backend with JWT authentication, post management, and voting. Secure password hashing, Pydantic request validation, PostgreSQL schemas via SQLAlchemy ORM, interactive docs via Swagger UI and ReDoc.

---

### 📊 GitHub stats

<div align="center">

<img height="165" src="https://github-readme-stats.vercel.app/api?username=pransh966&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" />
<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=pransh966&layout=compact&theme=tokyonight&hide_border=true" />

<img src="https://github-readme-streak-stats.herokuapp.com/?user=pransh966&theme=tokyonight&hide_border=true" />

</div>

---

<div align="center">

📫 **Reach me:** [pranshulkhokhar@gmail.com](mailto:pranshulkhokhar@gmail.com) · [LinkedIn](https://www.linkedin.com/in/pranshul-khokhar-12072005pransh/) · [SentinelAI live demo](https://sentinel-ai-six-nu.vercel.app) · [RepoMind repo](https://github.com/pransh966/RepoMind)

</div>
