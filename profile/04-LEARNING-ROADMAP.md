# Arjun Vavullipathy — Learning Roadmap to Top 1%

*Target: top 5% in ~18 months, top 1% on a 3–4 year horizon. Synthesized from an external skill assessment (top 12–15% for YOE) + analysis of the actual codebase (Wednesday OS, SEO Pipeline, Agent Skills).*

---

## The Lane Decision: **Evaluation Science (primary) + Retrieval (strong secondary)**

You keep being asked "evaluation or retrieval?" Here's the answer and the why:

**Pick Evaluation as your moat.** Three reasons grounded in your own work:
1. **Your instinct already lives here.** Wednesday OS's `Gap` type, `supersededAt` history, confidence scoring, and "measure-or-abstain / cited-intelligence" rule are an *evaluation mindset* expressed in a type system. You didn't copy that — it's how you think. Lean into it.
2. **It's the rarer, less-crowded lane.** Everyone is doing RAG. Far fewer engineers can tell you *why most evals are statistically invalid*. Scarcity = leverage.
3. **It's the named gap in your own assessment.** "The LLM layer is sophisticated but the *evaluation* of that layer is absent." Closing your single biggest weakness while it's also the highest-leverage lane is a rare two-for-one.

**Retrieval is your #2, not a competitor.** You cannot evaluate a RAG system without understanding retrieval deeply — so going deep on eval *forces* retrieval competence. They compound. Treat retrieval as the supporting skill that makes your eval work credible.

> **Your one-line positioning to build toward:** *"The engineer who can tell you whether your LLM system actually works — and prove it."*

---

## Operating Principles (how to run this roadmap)

1. **Ship-to-prove, don't study-to-collect.** You learn by building. Every deep topic below has a **BUILD** (a thing you make) and a **WRITE** (a public post). No topic is "done" until both exist.
2. **Depth over breadth — you already have breadth.** 21 projects is enough surface area. From here, 3–4 topics go *uncomfortably deep*; everything else stays at literacy.
3. **Mine your own systems.** Don't invent toy projects. Wednesday OS, eval-core, and the SEO pipeline are your lab. Instrument them, break them, measure them.
4. **Be wrong in public, then correct.** The 12%→1% gap is *demonstrated* knowledge — publish takes, defend or update them. Credibility is built in the open.

---

## Phase 0 — Close the named gaps (Months 0–2)
*These are the specific weaknesses the assessment flagged. Fix them first; they're cheap and they unblock everything.*

| Gap | Concrete action | Proof |
|---|---|---|
| No systematic eval of Juno's narrations | Build a small offline eval harness: golden set of inputs → expected narration properties → automated scoring | A `juno-eval` report run on real data |
| pgvector HNSW used but untuned | Measure recall@k vs latency while sweeping `m` / `ef_construction` / `ef_search` on your real embeddings | A tuning table + the chosen config, documented |
| Observability stops at the cascade | Add structured logging + a quality signal (not just "did it fail" but "did quality silently degrade") to one LLM path | A dashboard/log schema that catches silent degradation |
| Can't *name* the distributed patterns you built | Map your two-tier async / idempotency / append-only design to their textbook names (saga, outbox, eventual consistency) | A one-page "patterns in Wednesday OS" doc |

---

## Tier 1 — Go Extremely Deep (your moat: Months 2–12)

### 1. Evaluation Science  ⭐ PRIMARY
**Learn:** LLM-as-judge failure modes & bias; G-Eval methodology; RAGAS internals (faithfulness, answer/context relevance); statistical significance in evals (why N=20 "vibes" is invalid — confidence intervals, sample size); offline vs online eval; regression eval / eval-driven development.
- **Resources:** Hamel Husain's eval writing; Eugene Yan (eugeneyan.com) on evals & LLM patterns; the RAGAS paper; G-Eval paper; Chip Huyen — *AI Engineering* (2024); Anthropic's eval docs.
- **BUILD:** Turn your Phase-0 Juno harness into a reusable **eval framework** — golden datasets, LLM-judge with bias controls, statistical reporting, CI integration (regression gate). This becomes a flagship.
- **WRITE:** *"Why most LLM evals are statistically invalid (and what I did instead)."*

### 2. Retrieval Architecture  ⭐ SECONDARY
**Learn:** HNSW *internals* (graph construction, the params you tuned in Phase 0 — now understand *why*); hybrid search (BM25 + dense, fusion/RRF); late-interaction (ColBERT); reranking (cross-encoder vs bi-encoder, when each wins); chunking strategy as a first-class variable.
- **Resources:** Pinecone learning center; the ColBERT paper (Khattab & Zaharia); Jason Liu & Jerry Liu's RAG writing.
- **BUILD:** Take SEO-pipeline semantic dedup or Wednesday OS RAG and add **hybrid + reranking**; measure retrieval quality before/after with the eval framework from #1.
- **WRITE:** *"Retrieval, not generation, is where your RAG quality actually comes from."*

### 3. LLM Systems at Production Scale
**Learn:** what happens *inside* the serving layer — KV cache, continuous batching, speculative decoding; quantization (GPTQ / AWQ / GGUF) and the quality/latency/cost tradeoffs; cost modeling per token end-to-end.
- **Resources:** vLLM codebase & docs; Lilian Weng's blog; Tim Dettmers / QLoRA on quantization.
- **BUILD:** Self-host one open model (vLLM or llama.cpp — you already use llama.cpp in My Memories), benchmark batching/quantization, and write a cost-vs-latency comparison against the APIs you use.
- **WRITE:** *"What I learned hosting my own model after a year of just calling APIs."*

---

## Tier 2 — Go Solid (Months 6–18, in parallel)

### 4. Distributed Systems Fundamentals
**Learn (applied, not recited):** CAP in practice, eventual consistency, idempotency design, the saga & outbox patterns, exactly-once vs at-least-once.
- **Resource:** Kleppmann — *Designing Data-Intensive Applications*. **Read it deeply, don't skim.** This single book moves your "distributed fundamentals" percentile the most.
- **Proof:** the "patterns in Wednesday OS" doc from Phase 0, expanded — defend each tradeoff.

### 5. Probabilistic Systems & Uncertainty
**Learn:** confidence intervals, calibration (are your confidence scores *calibrated*?), Bayesian updating basics.
- **Resource:** Murphy — *Probabilistic Machine Learning* (free online), relevant chapters only.
- **Why:** your `Gap` type and confidence scoring are proto-Bayesian — formalize so you can defend them precisely. Directly strengthens the eval lane.

---

## Tier 3 — Maintain Literacy Only (ongoing, do NOT go deep)
- Transformer internals: attention, positional encoding, why multi-head. (Enough to explain, not implement.)
- RLHF/DPO concepts: why it works, not how to train it.
- Containers/K8s: enough to not be helpless in deployment.
- *Resource:* skim as needed — Karpathy's "Let's build GPT" once for transformers; don't sink months here.

---

## Cadence & Milestones

| Horizon | Focus | Milestone (proof) |
|---|---|---|
| **Month 2** | Phase 0 complete | Eval harness + HNSW tuning table + patterns doc exist |
| **Month 6** | Eval framework shipped + 2 posts | `eval-core`-grade framework public; "invalid evals" post has readers/comments |
| **Month 12** | Retrieval + serving depth | Hybrid+rerank shipped & measured; self-hosted model benchmarked; 4–6 posts total |
| **Month 18** | Known for evals | People reference your eval writing; DDIA read; you can defend every Wednesday OS tradeoff cold → **top ~5%** |
| **Year 3–4** | The lane owns you | You're "the eval person"; published takes challenged & defended → **top 1%** |

---

## Anti-Patterns (what NOT to do)
- ❌ Collect more small/demo projects — breadth is solved; it now dilutes.
- ❌ Chase ML research / training large models — wrong lane for you (see `05-CAREER-EVALUATION` once written; needs an MS, no edge).
- ❌ Study topics without shipping a BUILD + WRITE — that's how knowledge stays at 12%.
- ❌ Go deep on Tier 3. Literacy is the goal there.

---

## The two things that actually move 12% → 1%
1. **Be known for ONE thing** (evaluation). Write until people tag you in eval conversations.
2. **Be wrong in public and correct yourself.** Demonstrated knowledge > private knowledge.

*Generated 2026-06-29. Pairs with `03-PROJECTS.md` (your lab) and the career evaluation.*
