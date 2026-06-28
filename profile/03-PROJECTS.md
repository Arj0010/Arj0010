# Arjun Vavullipathy — Projects (Curated & Tiered)

Tiered by system complexity. Short map: `/home/arjun/Projects/index.txt`. Repos: github.com/Arj0010.

---

## █ ADVANCED — production-grade, multi-service, complex orchestration

### Wednesday OS — Pulse  ·  `knowledge-builder`  ·  Production (Wednesday)
**AI delivery-intelligence platform.** Turns the raw exhaust of how software gets built — commits, PRs, Jira, call transcripts, attendance, NPS — into an objective, continuously-updated, *cited* picture of project health and team well-being. Replaces self-reported status with telemetry.
- **Architecture:** two-tier async system. Connectors (GitHub/Jira/Fathom/Slack/Razorpay) → raw staging tables → cron-driven AI extraction (Gemini) → KnowledgeBlocks (typed, cited, confidence-scored facts) → pgvector semantic clustering → Two-Step-CoT memory synthesis → governance state machines + Juno conversational copilot (ReAct + RAG).
- **Principles enforced in code:** epistemic honesty (a metric is real or marked a gap), cited intelligence (every claim resolves to its signals), programmatic governance (date-gated state machines).
- **Stack:** Next.js 16, TypeScript, Prisma 7, Neon Postgres + pgvector, Gemini, Supabase Auth, shadcn/ui.
- **Scale:** ~1,277 files; 5 production modules; live across multiple client engagements.

### SEO Automation Pipeline  ·  `seo-automation`  ·  Production (Wednesday) — **FLAGSHIP**
**Event-driven AI content system** replacing a 4-person manual SEO workflow (analyst, writer, editor, publisher).
- **Architecture:** Slack `/seo-launch` → Gateway Lambda (200 OK in <100ms) → async Worker Lambda runs a 9-phase workflow: seed filtering (cosine-sim semantic guard) → intent detection → parallel competition/brand analysis → content-gap → up to 7 rounds of validated generation → Webflow CMS publish with JSON-LD schema.
- **Key decisions:** two-Lambda async pattern (beats Slack's 3s timeout); three-level semantic dedup (phases 1/3/6); model routing (Gemini 2.0 Flash primary, GPT-4o-mini fallback); S3 JSON embeddings over a vector DB for unit economics (<2000 embeddings).
- **Stack:** Python 3.13, Claude Sonnet 4.5, DataForSEO, Google Sheets/Docs, CrewAI, AWS Lambda; 87 py files.
- **Impact:** ~95% cost cut (₹1,000→₹25/blog), ~98% time cut (5h→5min), 10–12× output.

### Wednesday Agent Skills  ·  `ai-agent-skills`  ·  Production v2 (Wednesday)
**Codebase-intelligence + multi-agent skill framework** for Claude Code, Gemini CLI, Cursor, and Copilot — git discipline, PR triage, brownfield mapping, greenfield planning.
- **Architecture:** 17 modular skills with cross-platform adapters. A zero-LLM static dependency-graph analyzer + git-history parser + risk scorer answers most codebase questions for free; greenfield planning spawns parallel Research/Architect/PM/Security agents.
- **Stack:** Node 18+, Octokit, Ink (terminal UI), git hooks, GitHub Actions, OpenRouter/Anthropic.
- **Signal:** full scan <30s; ~$0.10 one-time summaries, <$0.05/mo ongoing; 8 languages; ~7,100 LOC.
- **Insight:** code understanding is a semantic problem, not a syntactic one — summaries beat AST dumps.

### My Memories  ·  `my-memories`  ·  MVP (Personal)
**Privacy-first offline desktop app** that auto-captures and indexes ChatGPT/Claude/Gemini conversations into a searchable local knowledge graph.
- **Architecture:** multi-process Electron — dedicated parsers per source → local LLM (llama.cpp) entity/insight extraction → Xenova Transformers embeddings → SQLite knowledge graph → React 19 + Three.js 3D entity visualization + semantic "memory chat". 100% offline, no telemetry.
- **Stack:** Electron, React 19, TypeScript, better-sqlite3, node-llama-cpp, Xenova Transformers, Three.js.
- **Signal:** ~73 TS files; runs LLM + embeddings fully locally.

### GetGist  ·  `GetGist`  ·  MVP (Personal)
**AI study companion Chrome extension** — in-LMS (Canvas) summaries, Q&A, and quizzes on text selection, with exam-integrity guardrails.
- **Architecture:** content script → background service worker → Supabase Edge Function proxy (hides API keys, enforces rate limits). Streaming responses; "Safe Mode" auto-detects exam URLs and disables itself (cannot be overridden).
- **Stack:** Chrome MV3, React, TypeScript, Tailwind, Supabase (Auth/PG/Edge Fns), GPT-4o-mini, Vite.
- **Insight:** learning systems fail without cross-session memory persistence.

---

## █ INTERMEDIATE — real full-stack / AI apps, single coherent system

### CareerOS  ·  `CareerOS`  ·  MVP — AI career operating system
Ikigai mapping, dynamic T-shape skill roadmaps, and real-time market-value tracking via a **5-agent system** (Discovery, Architect, Recalibrator, Coach, Hive). Next.js 16 + React 19 + Zustand + Supabase + GPT-4o + Vercel AI SDK + Langfuse; Zod-typed agent outputs. ~44 TS files.

### OCS Financial Agent Crew  ·  `ocs-financial-agent-crew`  ·  MVP/WIP
**Multi-agent financial coaching** — Q&A analyst + article-recommender agents on **CrewAI orchestrated by Temporal** async workflows; MongoDB history, Pinecone vector search, daily scheduled embedding refresh, Tavily search. ~3,100 LOC. *Insight: financial decisions are workflows, not single-shot outputs.*

### LAIPath  ·  `LAIPath`  ·  MVP — adaptive learning system
Solves the 90% self-directed-learning abandonment rate. Generates daily syllabi, enforces mandatory reflection gates, and **adapts the path to actual progress**. Core loop: generate → interact → reflect → evaluate → *conditional* regenerate. An embedding-based semantic guard (cosine sim) keeps the AI mentor on-topic. React 18 + Express + OpenAI + Supabase + Vercel. **70% fewer API calls** via conditional regeneration; gamified token economy. ~5,600 LOC.

### SoulThread  ·  `Soul-Thread`  ·  Production — AI newsletter platform
Free AI newsletter generator with **voice-profile training** and a **smart fallback chain** (real news from Reddit/HN/GitHub → curated trends → mock) so content always generates. Community features + LinkedIn voice-matched post generator. Next.js 16 + React 19 + Supabase (PG + RLS) + optional OpenAI + Resend. ~7,500 LOC.

### Drug-Likeness Predictor  ·  `drug-likeness-predictor`  ·  Academic (BCA capstone)
**Hybrid CNN-BiLSTM-LSTM** deep-learning model predicting compound drug-likeness from SMILES notation, trained on 250k ZINC molecules; one-hot SMILES encoding; Flask app with RDKit 2D + Py3Dmol 3D viewers. **~85% accuracy, 0.89 ROC-AUC, <100ms inference; >99% time & cost savings** vs. manual screening. TensorFlow 2.15.

### Agreement Maker  ·  `Agreement_Maker`  ·  MVP — AI legal assistant
Generates legal contracts from plain descriptions (18-point structure across 24 contract types) with optional Groq/Llama refinement, plus interactive legal Q&A. Multi-format export (TXT/DOCX/PDF). Flask + Groq + python-docx + ReportLab. ~1,900 LOC; well-documented.

### ResumeBot  ·  `ResumeBot`  ·  MVP — AI resume builder
Resume/cover-letter optimization with ATS analysis and multi-format processing (DOCX/PDF/image OCR). Dual interface (FastAPI REST + Gradio UI). Google Gemini 2.0-flash + PyPDF2 + pytesseract. ~1,637 LOC.

### PlanLift  ·  `PlanLift`  ·  MVP — 2D→3D render platform
Converts 2D architectural blueprints (PNG/JPG/PDF) to photoreal 3D renders with style presets (Modern/Minimal/Rustic/Luxury). Next.js 15 frontend posting to an external render backend; Cloudinary CDN + Replicate.

### AURYNTIX  ·  `PORTFOLIO`  ·  WIP — immersive portfolio prototype
Linux-style terminal UI (virtual filesystem + command parser), scroll-triggered pipeline animation, and Spline 3D integration with CRT aesthetic. React 19 + Vite 7 + Spline + Framer Motion. ~3,665 LOC. *(Experimental alternate to the active MYSITE portfolio.)*

### Project Iridium  ·  `project-iridium`  ·  WIP — data-science portfolio repo
Multi-project DS repo: a Flask + NLP **Resume Analyzer** (NER extraction + job-fit ML) plus telecom-churn, EV-population analyses and Power BI exercises. Python (Flask, scikit-learn, spaCy) + Jupyter + Power BI.

### AI Engineer Interview Bootcamp  ·  `ai-engineer-bootcamp`  ·  Reference/Learning
Self-built job-description-driven curriculum: RAG, LangChain/LangGraph, agentic AI (ReAct, multi-agent), STAR storytelling. 6 modular paths + 25 docs (~9.8k lines) + a hands-on RAG app + 40+ interview Q&As. *(Personal prep asset, not a product.)*

---

## █ BEGINNER / FOUNDATIONAL — single-scope academic & no-code learning builds

| Project | What | Technique / Result |
| :--- | :--- | :--- |
| **PhiQuest** (`Golden_Ratio`) | CV notebook + Tkinter GUI measuring facial golden ratio; SQLite store | OpenCV Haar cascades + GUI + DB |
| **Suicide Trends Dashboard** (`Sucide_Prediction_Dashboard_using_ML`) | EDA + prediction on India data 2001–12 | Random Forest + ipywidgets dashboard; 237K rows |
| **Patient Segmentation** (`Clustering_PatientSegmentation`) | Cluster hospital patients into 8 segments | K-Means on PCA features; silhouette 0.185 |
| **Divorce Factor Analysis** (`PCA_for_Divorce_Prediction`) | 5 latent factors from 55 survey items | Factor Analysis; KMO 0.964; 82.5% variance |
| **Didi AI Program** (`didi-ai-program`) | 4-week no-code curriculum to ship 5 AI automation tools | Claude Code + Google Sheets + no-code (teaching kit) |

---

*Excluded from the count: `the-art-of-command-line` (fork of jlevy's repo), `Arj0010` (GitHub profile readme), `MYSITE` (the data-collection portfolio site itself).*
