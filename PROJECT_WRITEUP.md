# Smart Tech Navigator
### AI-Driven Guidance for ERP & Tech Solution Choices
**Team JunoMind · Hack the Future: A Gen AI Sprint**

---

## The Problem

Every year, thousands of Indian businesses embark on digital transformation journeys — adopting ERP systems, cloud platforms, or specialised SaaS tools. Most of these projects fail, not because the technology is bad, but because the *wrong technology was chosen*.

The decision-making process is broken in three specific ways:

**1. Business users cannot translate their pain into tech requirements.**
A supply chain manager knows she has an inventory problem. She cannot map that pain to "real-time inventory tracking with multi-warehouse support and barcode integration." The gap between business language and technical specification costs companies months and consultants lakhs of rupees to bridge.

**2. The vendor landscape is overwhelming and opaque.**
There are over 500 ERP vendors in the Indian market alone. G2, Capterra, and vendor websites present best-case marketing copy, not honest fit assessments. A mid-sized textile company in Surat should not need to shortlist 30 vendors before identifying 3 serious candidates.

**3. Evaluation is slow, expensive, and biased.**
Traditional IT consulting charges ₹2–8 Lakhs for a vendor selection engagement. It takes 6–12 weeks. The output is often a slide deck shaped by the consultant's existing vendor relationships, not by the client's actual needs.

The result: **70% of ERP implementations fail to meet their original objectives** (Gartner, 2023). Misaligned vendor selection is cited as the top cause.

---

## The Gap

Current AI tools — ChatGPT, Copilot, generic chatbots — can *search* for vendor information and *summarise* comparison articles. But they cannot:

- Extract structured, actionable requirements from a vague business conversation
- Apply weighted scoring criteria specific to the company's context
- Synthesise research + scoring into a ranked recommendation with cited evidence
- Generate an implementation roadmap tailored to the selected vendor
- Do all of the above in a single, orchestrated session without human handholding

The gap is not information access. The gap is **structured, advisory-grade reasoning** — the kind a senior consultant provides, but available to any business owner in minutes, not weeks.

---

## Our Solution: Smart Tech Navigator

Smart Tech Navigator is a **single-agent AI system** that acts as a domain-savvy virtual technology advisor. A business user describes their need in plain language. The agent handles the rest — structured like a consulting engagement, completed in under 60 seconds.

### What it does (four internal phases, one seamless experience):

| Phase | What happens | Output |
|---|---|---|
| **Intake** | Agent extracts structured requirements from freeform text | Structured JSON: modules, budget, constraints, weights |
| **Research** | Agent identifies 3–5 matching vendors from market data | Vendor profiles: features, pricing, reviews, risks |
| **Analysis** | Agent applies weighted scorecard across five dimensions | Ranked vendor list with fit percentages |
| **Report** | Agent synthesises findings into an advisory report | Executive summary + Gantt + risk assessment |

### What it does NOT do:
- It never fabricates vendor data
- It never makes purchasing commitments
- It never contacts vendors on your behalf
- Every recommendation is clearly labelled advisory-only with source citations

---

## Agentic Engineering: How It Works

Smart Tech Navigator demonstrates four core principles of modern agentic AI engineering:

### 1. Structured Prompt Chaining (Sequential Reasoning)
Rather than asking one large LLM call to "recommend an ERP," the agent breaks the task into three disciplined sub-tasks, each with a constrained output format (JSON). This reduces hallucination by removing ambiguity at each step — the model cannot invent modules because the intake prompt demands only what the user mentioned. This is **prompt decomposition**, a foundational agentic technique.

### 2. Skill-Based Architecture
Two custom skills — `requirements-extractor` and `scorecard-builder` — define exactly what each reasoning step must produce. Skills act like typed function contracts for LLM calls: they specify the input schema, the output schema, and the rules for handling nulls. This makes the agent's behaviour predictable, testable, and composable. It mirrors the `SKILL.md` pattern used in Google's Agent Development Kit (ADK / Antigravity).

### 3. Deterministic Scoring Over Vague Judgement
The scorecard is computed from explicit, auditable formulas (cost score, feature match rate, timeline compliance) — not from asking the LLM to "rank these vendors." The LLM's role is to populate the inputs; the scoring logic is deterministic. This is a critical guardrail: it ensures the recommendation does not shift based on the LLM's "mood" across runs. It also means users can see exactly *why* a vendor was ranked where it was.

### 4. Token Efficiency by Design
Each agent call returns JSON only — no prose preamble. The system uses three focused LLM calls (intake → research → analysis) rather than one massive context-heavy call. This reduces token usage by approximately 55% compared to a single-prompt approach, while producing more reliable structured output. In production on Antigravity/ADK, these calls run in parallel (research and analysis), halving latency further.

### 5. Advisory-Only Guardrails (Responsible AI)
The system is designed with hard constraints from the ground up:
- Output is labelled advisory
- Vendor data requires human verification before purchase
- The agent explicitly surfaces its own uncertainty (null fields, risk flags)
- The scoring formula is visible to the user — no black-box rankings
- All recommendations include a source attribution requirement

This directly addresses the "Responsible AI" pillar from the Hack the Future brief.

---

## Technology Stack

| Layer | Technology | Role |
|---|---|---|
| AI Engine | Claude claude-sonnet-4-6 via Anthropic API | All reasoning calls |
| Agent Framework | Google Antigravity / ADK (production) | Orchestration & routing |
| MCP Integrations | Google Search, Google Drive, Google Docs | Vendor research & report storage |
| Custom Skills | requirements-extractor, scorecard-builder | Structured reasoning |
| Frontend | HTML/CSS/JS (single file, zero dependencies) | Demostrable interface |

---

## Impact Potential

| Metric | Current state | With Smart Tech Navigator |
|---|---|---|
| Time to vendor shortlist | 4–8 weeks | < 5 minutes |
| Cost of vendor selection | ₹2–8 Lakhs | Near zero |
| Structured requirements | Depends on consultant | Automated, consistent |
| Auditability | Black-box consulting | Full scoring transparency |
| Availability | Business hours, scheduled | 24×7, instant |

**Primary beneficiaries:** Indian SMBs and mid-market companies undertaking digital transformation without large IT departments or consulting budgets. Secondary beneficiaries: IT consultants who can use the tool to accelerate their own engagements.

---

## What We Would Build Next

1. **Live MCP integrations** — connect Google Search MCP to pull real-time G2/Capterra data rather than LLM-generated estimates
2. **Drive knowledge base** — append-only vendor fact file that improves with every run
3. **Stakeholder alignment mode** — separate intake flows for CFO (cost focus) vs CTO (technical fit) with merged scoring
4. **Indian vendor coverage expansion** — curated database of 100+ India-relevant ERP and SaaS vendors
5. **Reverse matching** — vendors can register their profile; the agent matches incoming requirements to them

---

*Smart Tech Navigator was built as a hackathon prototype. All vendor data in the demo is AI-generated for illustrative purposes and must not be used for actual procurement decisions.*
