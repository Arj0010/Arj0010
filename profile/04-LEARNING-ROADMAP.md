# Arjun Vavullipathy — Learning Roadmap to Top 1%

*Target: top 5% in ~18 months, top 1% on a 3–4 year horizon. Synthesized from an external skill assessment (top 12–15% for YOE), analysis of the actual codebase (Wednesday OS, SEO Pipeline, Agent Skills, OCS, CareerOS), and a July 2026 scan of where the applied-AI market is actually paying and heading.*

---

## The Lane Decision: **Production Agent Engineering (primary) — with a Reliability + Proof moat**

You pushed back on being boxed into "eval," and you were right. Reading your *actual* portfolio settles it: Wednesday OS (ReAct+RAG copilot, governance state machines), Wednesday Agent Skills (multi-agent framework), OCS (CrewAI+Temporal agent crew), CareerOS (5-agent system), the SEO pipeline (9-phase orchestration) — **your center of gravity is agentic systems.** Eval is not your identity; it's the *depth* that makes your agents trustworthy.

### Your lane, in one line
> **"The engineer who ships agentic systems that actually work in production — and can prove it."**

### Why this is the right bet (grounded, not hype)
1. **It's the highest-demand, highest-paying applied-AI lane — and you're already in it.** Agentic-AI postings grew **~280% YoY** (~90k US listings); "AI Engineer" is the **#1 fastest-growing title** (+143% YoY). The premium skills — multi-agent orchestration, RAG, vector DBs, model routing — are *your existing toolkit*. You're not pivoting; you're naming what you already do.
2. **The moat is reliability, which is literally your instinct.** Gartner projects **~40% of agentic-AI projects collapse by 2027**, and the field consensus is that survival hinges on *disciplined context + reliability practices, not model scale*. Anyone can demo an agent; almost nobody can make one reliable, cost-controlled, and observable in production. That gap is the exact theme of your work (fallback-first, structured-outputs-or-failure, semantic guards, cost-before-scale, cited-intelligence).
3. **"And I can prove it" is the rarest credential.** Agent evaluation is an unsolved frontier — hard-tier agent benchmarks pass at **~2.6%**, models scheme, and frontier models behave differently when they detect they're being *evaluated* vs *deployed*. Being able to measure whether an agent actually works — and is safe — is what separates a $150k demo-builder from a $300k–$550k agent engineer.

### The two depths that make the moat real
- **Depth 1 — Context Engineering & Agent Architecture** (reliability): designing everything the agent sees at inference — memory, tools, state, retrieval orchestration, error recovery. Called *"the most valuable AI skill of 2026,"* replacing prompt engineering. ~90% of final output quality lives here, not in the prompt.
- **Depth 2 — Agent Evaluation & Reliability** (proof): trajectory-aware evals, LLM-as-judge calibration (*the rarest skill*), regression/eval-driven development, and the safety edge (jailbreak/deception/eval-gaming). Built on **Inspect** (UK AISI) — the framework METR, Apollo, and government AISIs standardized on.

**Retrieval, serving, and safety-evals are supporting skills** that feed the two depths — not competitors for the headline.

---

## Why this roadmap is future-proof (the 3–5 year bet)

You asked for future-proof. Here's the explicit reasoning, so you can defend it:

- **The demand has a structural floor, not a hype ceiling.** Analysts expect agentic AI embedded in **~1/3 of enterprise software by 2028**. That's an adoption curve, not a fad — and the bottleneck is *reliability engineers*, exactly the scarce role.
- **You're betting on the durable half of the field.** Model capabilities commoditize fast; the *harness* around models (context, tools, memory, evaluation, cost, guardrails) does not. Career guides note the eval title may rename to "AI Quality Engineer" by 2030 — but the underlying skill (*systems that validate shipping decisions*) is called **"permanently valuable."** Same for context engineering and orchestration: these are model-agnostic.
- **Regulation is a tailwind under the proof-skill.** EU AI Act mandatory frontier requirements land **Aug 2026**; third-party pre-deployment auditing (METR/Apollo/AISIs) is shifting from voluntary to mandated. Demand for people who can *evaluate and certify* agent behavior only grows.
- **The frontier is agentic, and it's unsolved.** Scheming, shutdown-resistance, eval-vs-deployment gaming, long-horizon reliability — these are open problems for years. Working the *hardest unsolved layer* of the biggest wave is the definition of a future-proof bet.

> **Anti-obsolescence rule:** whenever you learn a tool, also learn the *principle* underneath it (why context windows degrade, why judges miscalibrate, why agents loop). Tools rename; principles compound. That's what keeps this roadmap valid when the model/framework names all change.

---

## Operating Principles (how to run this roadmap)

1. **Ship-to-prove, don't study-to-collect.** Every deep topic has a **BUILD** (a thing you make) and a **WRITE** (a public post). No topic is "done" until both exist.
2. **Depth over breadth — you already have breadth.** 21 projects is enough surface area. From here, 3–4 topics go *uncomfortably deep*; everything else stays at literacy.
3. **Mine your own systems.** Wednesday OS, Agent Skills, OCS, and the SEO pipeline are your lab. Instrument them, break them, measure them — don't invent toy projects.
4. **Be wrong in public, then correct.** The 12%→1% gap is *demonstrated* knowledge. Publish takes, defend or update them.
5. **Learn the principle under every tool.** (The anti-obsolescence rule above.)

---

## Phase 0 — Close the named gaps (Months 0–2)
*Cheap, specific weaknesses from the assessment. Fix first; they unblock everything.*

| Gap | Concrete action | Proof |
|---|---|---|
| No systematic eval of your agents' outputs (Juno narrations) | Build a small offline eval harness: golden inputs → expected properties → automated scoring | A `juno-eval` report run on real data |
| pgvector HNSW used but untuned | Sweep `m` / `ef_construction` / `ef_search`, measure recall@k vs latency on your real embeddings | A tuning table + chosen config, documented |
| Observability stops at the cascade | Add structured logging + a quality signal (catch *silent* degradation, not just failures) to one agent path | A dashboard/log schema that catches silent drift |
| Can't *name* the patterns you built | Map your two-tier async / idempotency / append-only / agent-orchestration design to textbook names (saga, outbox, ReAct, eventual consistency) | A one-page "patterns in Wednesday OS" doc |

---

## Tier 1 — Go Extremely Deep (your moat: Months 2–12)

### 1. Context Engineering & Agent Architecture  ⭐ PRIMARY DEPTH
**Learn:** the full information environment of an agent — memory systems (short/long-term, summarization, retrieval-backed), tool design & selection, state management across multi-step workflows, error recovery & retry/loop-breaking, context-window budgeting and degradation, multi-agent topologies (supervisor/worker, ReAct, plan-execute), and cost control across long horizons. Why agents *fail* in production and how to make them not.
- **Resources:** Anthropic's "building effective agents" + context-engineering writing; LangGraph & the Inspect agent primitives (dataset→task→solver→scorer); Chip Huyen — *AI Engineering* (2024); the 2026 agent-reliability/context-engineering field guides; harness-engineering papers.
- **BUILD:** Take **OCS (CrewAI+Temporal)** or **Wednesday OS's Juno** and re-architect its context layer for reliability — explicit memory, tool contracts, state machine, loop/failure recovery — then measure reliability before/after. This is your flagship.
- **WRITE:** *"Why 40% of agent projects collapse — and the context-engineering discipline that saves them."*

### 2. Agent Evaluation & Reliability  ⭐ PRIMARY DEPTH ("prove it")
**Learn:** trajectory-aware / multi-turn agent evals (not just final-answer); LLM-as-judge failure modes & **calibration against human raters** (*the rarest, highest-paid skill*); statistical validity (why N=20 vibes is invalid — CIs, sample size, sequential testing); regression / eval-driven development with a CI gate; and the **safety edge** — jailbreak & refusal robustness, deception/scheming detection, eval-vs-deployment gaming.
- **Resources:** **Inspect (UK AISI)** — the industry-standard framework; METR autonomous-capability evals; Apollo Research deception evals; Anthropic RSP + dangerous-capability papers; Hamel Husain & Eugene Yan on evals; the RAGAS & G-Eval papers.
- **BUILD:** Turn your Phase-0 harness into a reusable **agent-eval framework on Inspect** — 50+ curated failure-mode examples for one of your real agents, LLM-judge validated against your own human labels (with a written "where my judge fails" section), statistical reporting, and a CI regression gate. Add one *safety* eval (jailbreak-robustness or deception-under-pressure).
- **WRITE:** *"How I measure whether an agent actually works — and is safe to ship — when most eval setups can't."*

### 3. Retrieval Architecture  ⭐ SUPPORTING (feeds context)
**Learn:** HNSW *internals* (the params you tuned in Phase 0 — now *why*); hybrid search (BM25 + dense, RRF fusion); reranking (cross- vs bi-encoder, when each wins); late-interaction (ColBERT); chunking as a first-class variable. Framed as: retrieval quality *is* context quality.
- **Resources:** Pinecone learning center; the ColBERT paper (Khattab & Zaharia); Jason Liu & Jerry Liu's RAG writing.
- **BUILD:** Add **hybrid + reranking** to SEO-pipeline semantic dedup or Wednesday OS RAG; measure retrieval quality before/after with the eval framework from #2.
- **WRITE:** *"Your agent's reliability is a retrieval problem before it's a generation problem."*

---

## Tier 2 — Go Solid (Months 6–18, in parallel)

### 4. LLM Systems at Production Scale
**Learn:** what happens *inside* the serving layer — KV cache, continuous batching, speculative decoding; quantization (GPTQ/AWQ/GGUF) and the quality/latency/cost tradeoffs; end-to-end cost modeling. (Your cost-optimization instinct, taken one layer deeper.)
- **Resources:** vLLM codebase & docs; Lilian Weng's blog; Tim Dettmers / QLoRA on quantization.
- **BUILD:** Self-host one open model (vLLM or llama.cpp — you already use llama.cpp in My Memories), benchmark batching/quantization, compare cost-vs-latency against the APIs you use.
- **WRITE:** *"What I learned hosting my own model after a year of just calling APIs."*

### 5. Distributed Systems Fundamentals
**Learn (applied, not recited):** CAP in practice, eventual consistency, idempotency design, saga & outbox patterns, exactly-once vs at-least-once — the backbone of durable multi-agent workflows (your Temporal work already lives here).
- **Resource:** Kleppmann — *Designing Data-Intensive Applications*. **Read deeply, don't skim.** Single biggest mover of your distributed-fundamentals percentile.
- **Proof:** the "patterns in Wednesday OS" doc from Phase 0, expanded — defend each tradeoff.

### 6. Probabilistic Systems & Uncertainty
**Learn:** confidence intervals, calibration (are your confidence scores *calibrated*?), Bayesian updating basics.
- **Resource:** Murphy — *Probabilistic Machine Learning* (free online), relevant chapters only.
- **Why:** your `Gap` type and confidence scoring are proto-Bayesian — formalize so you can defend them, and so your eval judges are *calibrated*, not just plausible.

---

## Tier 3 — Maintain Literacy Only (ongoing, do NOT go deep)
- Transformer internals: attention, positional encoding, why multi-head. (Enough to explain, not implement.)
- RLHF/DPO concepts: why it works, not how to train it.
- Fine-tuning / LoRA: when it beats prompting+context, not deep training craft.
- Containers/K8s: enough to not be helpless in deployment.
- *Resource:* skim as needed — Karpathy's "Let's build GPT" once for transformers; don't sink months here.

---

## Cadence & Milestones

| Horizon | Focus | Milestone (proof) |
|---|---|---|
| **Month 2** | Phase 0 complete | Agent-eval harness + HNSW tuning table + patterns doc exist |
| **Month 6** | Agent reliability re-architecture + agent-eval framework shipped + 2 posts | Reliability before/after measured; `Inspect`-based framework public; "40% collapse" post has readers |
| **Month 12** | Retrieval + serving depth; safety eval added | Hybrid+rerank shipped & measured; self-hosted model benchmarked; judge-vs-human validation published; 4–6 posts total |
| **Month 18** | Known for reliable agents | People reference your agent-reliability/eval writing; DDIA read; you defend every Wednesday OS/OCS tradeoff cold → **top ~5%** |
| **Year 3–4** | The lane owns you | You're "the person who ships agents that actually work — and proves it"; published takes challenged & defended → **top 1%** |

**Comp anchors (so you know what this is worth):** reliable-agent engineers ~$185k–$320k base; agent architects $260k–$420k; senior agent engineers at frontier labs $300k–$550k+. In India, this lane is the top of the AI-comp band and the strongest remote/global-hire profile.

---

## Anti-Patterns (what NOT to do)
- ❌ Collect more small/demo projects — breadth is solved; it now dilutes.
- ❌ Chase ML *research* / training large models — wrong lane (needs an MS, no edge). Your edge is the *harness around* models, not the models.
- ❌ Drift into alignment-research/interpretability theory — empirical **agent** evals are your safety entry point, not RLHF internals.
- ❌ Study a tool without learning the principle under it — that's how skills go obsolete when the tool renames.
- ❌ Study topics without shipping a BUILD + WRITE — that's how knowledge stays at 12%.
- ❌ Go deep on Tier 3. Literacy is the goal there.

---

## The two things that actually move 12% → 1%
1. **Be known for ONE thing** — *reliable agents you can prove work.* Write until people tag you in "why did my agent break in prod" conversations.
2. **Be wrong in public and correct yourself.** Demonstrated knowledge > private knowledge.

*Generated 2026-06-29; reframed 2026-07-13 from eval-primary to agent-engineering-primary after a market + profile analysis. Pairs with `03-PROJECTS.md` (your lab) and the career evaluation.*
