# Arjun Vavullipathy — Capabilities

## Skills Matrix

| Category | Technologies & Concepts |
| :--- | :--- |
| **AI / LLM** | LLM orchestration, multi-agent systems (CrewAI), RAG, semantic dedup & embeddings, model routing & fallback chains, structured/typed outputs, prompt chaining, token-cost optimization, Langfuse/Langtrace observability, OpenRouter |
| **Models** | Claude (Sonnet 4.5), Gemini (2.0 Flash / embedding-001), GPT-4o / 4o-mini, Groq (Llama 3.x / Mixtral), local LLMs (llama.cpp), text-embedding-3-small |
| **Backend** | Python, Node.js, TypeScript, FastAPI, Flask, Express, AWS Lambda, event-driven & async architecture, Temporal workflows, serverless |
| **Frontend** | Next.js 14–16 (App Router), React 18/19, Tailwind CSS, Framer Motion, Zustand, shadcn/ui, Vite |
| **Data / Storage** | PostgreSQL, Supabase, Prisma, MongoDB, pgvector, Pinecone, S3-based vector caching, SQLite, semantic guard filtering |
| **ML / DS** | TensorFlow/Keras (CNN-LSTM hybrids), scikit-learn, PCA / factor analysis, K-Means clustering, Random Forest, RDKit (cheminformatics), pandas/NumPy, OpenCV |
| **Dev tooling / Platform** | Codebase intelligence (dependency-graph analysis, risk scoring), git hooks, GitHub Actions, Chrome extensions (MV3), Electron, Docker, Vercel, Cloudinary, Replicate |
| **Ops** | Token cost tracking, parallel/batch execution (ThreadPoolExecutor), fallback chains, rate limiting, async processing, cron orchestration |

## What He Can Build (proven)
- **Production AI pipelines** — event-driven, multi-phase, cost-optimized (SEO Automation: Slack → Lambda → 9-phase workflow → CMS).
- **Multi-agent systems** — specialized agent crews with orchestration & validation (OCS Financial, CareerOS, Wednesday Agent Skills greenfield agents).
- **AI-powered full-stack products** — Next.js/React + Supabase/Postgres with real auth, RLS, streaming, gamification (LAIPath, SoulThread, CareerOS, GetGist).
- **Codebase-intelligence / dev tooling** — static dependency-graph analysis, risk scoring, PR triage across multiple AI platforms (Wednesday Agent Skills).
- **Deep-learning applications** — hybrid CNN-BiLSTM models with full-stack deployment (Drug-Likeness Predictor).
- **Privacy-first desktop apps** — multi-process Electron with local LLM + embeddings + 3D visualization (My Memories).
- **Data-science analyses** — clustering, dimensionality reduction, predictive modeling with dashboards.

## Engineering Principles
1. **Design for cost before scale.** Unit economics first — optimized Gemini ($1/M) over $10/M alternatives before scaling to 50 blogs/week.
2. **Fallback-first architecture.** Every API call has a degradation path (e.g., Gemini → GPT-4o-mini; real news → curated → mock).
3. **Structured outputs over raw text.** Typed JSON schemas and validation gates; unstructured LLM output is treated as a system failure.
4. **Reliability > features.** Near-100% success on core workflows beats adding complexity.
5. **Epistemic honesty / cited intelligence.** AI assertions cite their evidence or are marked as gaps — "measure-or-abstain" (Wednesday OS).
6. **Constraints as features.** Scoping what an AI can do (semantic topic guards, mandatory reflection) turns a distraction machine into a focused tool.

## Signature Techniques
- **Semantic guard / dedup** — cosine-similarity gates against stored vectors to prevent overlap and keep agents on-topic.
- **Two-Lambda async pattern** — decouple a fast frontend ack (<100ms) from long backend processing (5–30 min).
- **Conditional regeneration** — only regenerate expensive AI output when an evaluation signals it's needed (70% fewer calls).
- **Zero-LLM static analysis** — answer most codebase questions from a pre-computed dependency graph instead of paying per query.
- **Model routing** — primary/fallback model selection tuned for cost-per-token under quality gates.
