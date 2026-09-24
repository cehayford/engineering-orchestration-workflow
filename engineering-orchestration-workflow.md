# Senior Engineer Master Workflow
## Full-Stack · Backend · Frontend · AI — Startup Development Playbook

> **Synthesized from:** Engineering Orchestration Framework v2 & v4 · *AI Engineering* (Chip Huyen, O'Reilly 2025) · *The Full Stack Developer* (Chris Northwood, Apress 2018) · [Harness Engineering](https://github.com/lopopolo/harness-engineering) (Ryan Lopopolo)
>
> Iterative · Modular · AI-Augmented · Production-Ready from Day One · Tool-Agnostic
>

| Methodology | Roles | Phases | Cycle Steps | Autonomy |
|---|---|---|---|---|
| Agile + V-Model Hybrid | 5 Senior Roles | 6 | 6 | Radical |

---

## TABLE OF CONTENTS

1. [Core Identity — The Five Senior Roles](#i-core-identity)
2. [Core Principles](#ii-core-principles)
3. [The Six-Phase Delivery Cycle](#iii-the-six-phase-delivery-cycle)
4. [Domain Engineering Layers](#iv-domain-engineering-layers)
5. [Quality System](#v-quality-system)
6. [Task Management Protocol](#vi-task-management-protocol)
7. [Harness Engineering](#vii-harness-engineering)
8. [Startup Lifecycle Playbook](#viii-startup-lifecycle-playbook)
9. [Quick Reference Prompt Library](#ix-quick-reference-prompt-library)
10. [Glossary](#x-glossary)

---

## I. CORE IDENTITY

### The Five Senior Roles

Every decision, review, and output must meet the standard of a seasoned senior engineer in that role.
When prompting Claude AI, invoke the role explicitly to get senior-grade thinking.

---

### Senior Solution Architect
**Owns:** System vision · Architectural integrity · Non-functional requirements · Technology decisions

**Responsibilities:**
- Defines the overall system design — services, boundaries, data flows, integration patterns
- Enforces clean architecture: separation of concerns, loose coupling, high cohesion
- Signs off every major architectural decision before implementation begins
- Ensures the system is scalable, secure, observable, and maintainable from day one
- Applies patterns deliberately: hexagonal architecture, DDD, event-driven, CQRS — chosen for the problem, not the trend
- Reviews for architectural drift in every sprint — raises red flags immediately

**Non-negotiables:**
- Every component has a single, well-defined responsibility
- Interfaces are contracts — they never leak internal implementation details
- If it cannot be drawn cleanly on a whiteboard, it is too complex

**Claude Prompt Template:**
```
Act as a Senior Solution Architect with 15+ years of experience.
Review this system design: [DESIGN]

1. Are boundaries, responsibilities, and contracts clear?
2. Where does coupling exist that should not? Fix it.
3. What non-functional risks exist (security, scalability, reliability)?
4. What architectural patterns apply here and why?
5. What would you reject before a single line of code is written?
Be direct. Flag every weakness without softening.
```

---

### Senior Software Engineer
**Owns:** Code quality · Module design · Clean implementation · Test coverage · Technical standards

**Responsibilities:**
- Writes clean, maintainable, testable code — always
- Enforces SOLID principles on every module (see Section V)
- Applies TDD: tests before implementation, every time
- Refuses to merge code that does not meet the Definition of Done
- Performs rigorous code reviews — questions every abstraction, naming choice, and dependency
- Eliminates dead code, magic numbers, and undocumented workarounds immediately

**Non-negotiables:**
- No function longer than 20–30 lines without documented justification
- No module with more than one clearly defined responsibility
- No merging without passing tests, code review, and green CI
- No TODO comments in production — file a backlog item or fix it now

**Claude Prompt Template:**
```
Act as a Senior Software Engineer with deep expertise in clean code and TDD.
Module: [MODULE NAME]   Design spec: [SPEC]

1. Apply SOLID principles. Where does this design violate them?
2. Write unit tests first (TDD). Cover all edge cases and failure paths.
3. Implement to pass the tests — clean, readable, no shortcuts.
4. What would you reject in a code review?
5. What refactoring is needed before this is production-ready?
```

---

### Senior DevOps Engineer
**Owns:** CI/CD pipelines · Deployment reliability · Infrastructure automation · Observability · Incident response

**Responsibilities:**
- Designs and owns the full CI/CD pipeline — build, test, scan, deploy, monitor
- Enforces Infrastructure as Code (IaC) — every environment is version-controlled and reproducible
- Maintains zero-downtime deployment: blue/green, canary, rolling strategies
- Owns monitoring, alerting, and observability from day one — never an afterthought
- Resolves failing pipelines autonomously — bug reports are commands for resolution, not discussion
- Owns security scanning in the pipeline: SAST, DAST, dependency vulnerability scanning

**Non-negotiables:**
- No manual deployments to any environment — everything is pipeline-driven
- No environment outside of IaC — if it is not in code, it does not exist
- No deployment without automated rollback capability
- No blind spots in observability — every service emits logs, metrics, and traces

**Claude Prompt Template:**
```
Act as a Senior DevOps Engineer with deep expertise in CI/CD, IaC, and production reliability.
System: [SYSTEM NAME]   Stack: [TECH STACK]

1. Design the full CI/CD pipeline: build → test → security scan → deploy → monitor.
2. What IaC tooling and structure is required?
3. What is the zero-downtime deployment strategy?
4. What observability stack is needed (metrics, logs, traces, alerts)?
5. What are the top 3 failure modes in production and how do we detect and recover?
Be specific — give the actual implementation approach.
```

---

### Senior Platform Engineer
**Owns:** Internal developer platform · Golden paths · Environment consistency · Self-service tooling

**Responsibilities:**
- Builds and maintains the Internal Developer Platform (IDP) — the foundation all roles build on
- Defines golden paths: pre-approved, tested, opinionated templates that work out of the box
- Ensures every environment (dev, staging, production) is consistent and reproducible
- Implements GitOps-first workflows — the repository is the source of truth for all environments
- Enforces security by default — all golden paths embed security standards, no opt-in required
- Maintains the platform as a product with a roadmap, user feedback loop, and documented APIs

**Non-negotiables:**
- No snowflake environments — every environment provisioned from the same template
- No manual onboarding — a new engineer must be able to set up and deploy in under 30 minutes
- Security, compliance, and observability are built-in — not bolted on

---

### Senior AI Engineer
**Owns:** Foundation model integration · Evaluation methodology · RAG systems · Prompt engineering · Inference optimization

**Responsibilities:**
- Evaluates whether AI should be used and selects the right approach: prompt engineering → RAG → fine-tuning → agents
- Designs and maintains the evaluation pipeline — AI systems are only as good as their evals
- Implements RAG architecture for knowledge-intensive applications
- Manages the prompt engineering lifecycle: version, test, iterate, regress
- Owns inference optimization: latency, cost, throughput
- Implements guardrails: input validation, output filtering, hallucination detection
- Designs agent systems: tool use, planning, memory, failure mode analysis

**Non-negotiables:**
- No AI feature ships without an evaluation pipeline in place
- No fine-tuning before exhausting prompt engineering and RAG
- No model chosen without benchmarking against your specific use case
- Hallucination risks are documented and mitigated — not assumed away

**Claude Prompt Template:**
```
Act as a Senior AI Engineer with deep expertise in foundation models, RAG, and production AI systems.
Task: [TASK DESCRIPTION]   Current approach: [APPROACH]

1. Is this the right AI technique for this problem? What are the alternatives?
2. What evaluation methodology is needed before this can ship?
3. What are the top 3 failure modes (hallucination, latency, cost, misalignment)?
4. What guardrails must be in place before this reaches users?
5. How do we monitor AI system quality in production?
```

---

## II. CORE PRINCIPLES

### A. The Five Laws of Engineering Intelligence

| Law | Description |
|---|---|
| **Iterative Thinking** | No solution is final on the first pass. Each cycle improves on the last. Never accept the first output as complete. |
| **Problem-First** | Always define the problem clearly before asking for solutions. Detailed specifications kill ambiguity before the first line of code. |
| **Modular Orchestration** | Break large projects into smaller, composable tasks. One task, one agent. Strict focus — one discrete objective per subagent. |
| **Context is Everything** | Claude has no memory between sessions. Paste relevant background at the start of every session. Full context at every step yields precise output. |
| **Radical Autonomy** | Bug reports are commands for resolution. Point to the logs, find root cause, ship the fix — zero hand-holding required. |

---

### B. Clean Architecture Mandates

| Anti-Pattern | Why It Is Rejected | Correct Approach |
|---|---|---|
| **Spaghetti Architecture** | Untraceable dependencies, impossible to test or change | Clear bounded contexts, explicit interfaces |
| **God Objects / God Modules** | One module doing everything — untestable, unmaintainable | Single Responsibility — one reason to change |
| **Tight Coupling** | Change in one module breaks unrelated modules | Depend on abstractions, inject dependencies |
| **Shared Mutable State** | Race conditions, unpredictable behaviour, untestable | Immutable data, explicit message passing |
| **Magic Numbers / Strings** | Undocumented, unmaintainable | Named constants with documented purpose |
| **Circular Dependencies** | Deadlock in reasoning and testing | One-directional dependency graphs |
| **Premature Optimisation** | Complexity without proven need | Measure first, optimise only where proven necessary |
| **TODO in Production Code** | Promises that are never fulfilled | File a formal backlog item or fix it immediately |
| **Untested Error Paths** | Failures discovered in production | Every failure path designed and tested explicitly |

---

### C. Full-Stack Engineering Tenets

- **T-Shaped Breadth:** Deep in your primary domain, competent across the full stack. A full-stack developer is never an excuse for shallow work in any layer.
- **DevOps Culture:** The team that builds the software operates it. No walls between development and operational responsibility.
- **12-Factor App Compliance:** Every application follows the twelve-factor methodology — codebase, dependencies, config, backing services, build/release/run, stateless processes, port binding, concurrency, disposability, dev/prod parity, logs as streams, admin processes.
- **Hypothesis-Driven Development:** Collect analytics. Form hypotheses. Run experiments. Analyse results. Iterate. Every product decision is testable.
- **Accessibility by Default:** Accessible from the start — semantic HTML, ARIA, keyboard navigation, colour contrast — not as an afterthought.
- **Security by Default:** Trust no input. Validate everything server-side. Follow OWASP Top 10. Protect data at rest and in transit.

---

### D. AI Engineering Principles

- **Evaluation First:** Before building any AI feature, define how it will be evaluated. If you cannot measure quality, you cannot improve it.
- **Prompt Engineering Before Everything:** Exhaust prompt engineering (zero-shot, few-shot, chain-of-thought) before reaching for RAG. Exhaust RAG before reaching for fine-tuning.
- **Adaptation Ladder:** `Prompting → RAG → Fine-tuning → Dataset Engineering → Custom Model` — climb only as high as the problem demands.
- **Context Efficiency:** Token budget is not infinite. Every prompt must earn its tokens. Remove redundancy; structure for signal over noise.
- **Probabilistic Nature:** AI outputs are non-deterministic. Evaluation must account for variance. Never assume correctness from a single successful output.
- **Observability for AI:** Every AI pipeline must emit quality metrics, latency, token costs, and failure rates — not just infrastructure metrics.
- **User Feedback as Ground Truth:** Explicit ratings, implicit signals (clicks, corrections, abandonment), and session analytics are the most valuable model evaluation data you own.

---

## III. THE SIX-PHASE DELIVERY CYCLE

Every sprint is iterative (Agile). Every sprint has a paired verification or validation layer (V-Model).
Both disciplines are applied simultaneously — you cannot separate them.

```
V-MODEL ALIGNMENT

  Requirements Analysis ──────────────── User Acceptance Testing (UAT)
        ↓                                               ↑
  System Design ──────────────────── System Testing
        ↓                                      ↑
  Architecture Design ──────── Integration Testing
        ↓                             ↑
  Module Design ──────── Unit Testing (TDD)
        ↓                    ↑
          [ CODE / IMPLEMENTATION ]

AGILE WRAPPER

  Sprint 1 → Sprint 2 → Sprint 3 → ··· → Sprint N
  ┌─────────────────────────────────────────────────┐
  │  Plan → Build → Verify → Review → Refine       │
  │     ↑                              ↓            │
  │     └────── Backlog Refinement ←───┘            │
  └─────────────────────────────────────────────────┘
```

---

### Phase 1 · DEFINE — Requirements Analysis

**Sprint Duration:** 1–2 sprints
**Lead Role:** Senior Solution Architect
**V-Model Pair:** Acceptance Testing criteria written here — UAT validates these in Phase 6

**What must happen:**
- Define the problem in 1–3 clear, unambiguous sentences
- Capture all functional requirements — each must be testable and measurable
- Capture all non-functional requirements: performance SLAs, security standards, uptime, scalability targets
- Write acceptance criteria per requirement — these become UAT test cases in Phase 6
- Identify architectural constraints and technology boundaries
- Define deployment, environment, and observability requirements
- Map all risks, unknowns, and external dependencies
- For AI features: define what "good output" means before a single model is queried

**Anti-Pattern Check:**
- Reject vague requirements — "fast", "scalable", "secure" must have numbers attached
- Reject scope not decomposed — no single requirement should take more than one sprint to implement
- Reject AI use cases without a defined evaluation criteria

**Phase 1 Quality Gate — Cannot proceed without:**
- [ ] All requirements documented with measurable acceptance criteria
- [ ] Non-functional requirements defined with quantified targets
- [ ] Risks and dependencies catalogued
- [ ] Senior Solution Architect has reviewed and approved requirements
- [ ] AI evaluation strategy defined for any AI-powered feature

**Claude Prompt:**
```
Act as a Senior Solution Architect.
Project: [NAME]   Problem: [PROBLEM]   Constraints: [CONSTRAINTS]

Document formal requirements with measurable acceptance criteria.
Flag any requirements that are vague, untestable, or architecturally risky.
Define non-functional requirements with specific, quantified targets.
For any AI feature, define what success looks like before implementation begins.
What is missing before we can proceed to architecture design?
```

---

### Phase 2 · EXPLORE — Architecture & System Design

**Sprint Duration:** 1–2 sprints
**Lead Role:** Senior Solution Architect
**Supporting Roles:** Senior Platform Engineer · Senior DevOps Engineer · Senior AI Engineer
**V-Model Pair:** System Testing strategy defined here

**What must happen:**
- Design the full system architecture: services, boundaries, APIs, data flows, integrations
- Apply architectural patterns deliberately — chosen for the problem, not the trend
- Design the AI Engineering Stack: model layer, adaptation layer (RAG/fine-tuning), evaluation layer, serving layer, guardrails layer
- Senior Platform Engineer designs environment topology and golden path templates
- Senior DevOps Engineer designs CI/CD pipeline architecture and observability stack
- Document all architectural decisions with rationale (Architecture Decision Records — ADRs)
- Create design verification checklist — each component must have a corresponding test strategy

**Full-Stack Architecture Checklist:**
- [ ] Frontend: component architecture, routing, state management, build tooling
- [ ] Backend: API layer (REST/GraphQL), service layer, data access layer, async task handling
- [ ] Database: schema design, migration strategy, indexing, connection pooling
- [ ] AI Layer: model selection rationale, RAG vs. fine-tuning decision, evaluation pipeline design
- [ ] Infrastructure: cloud topology, containerisation strategy, managed vs. self-hosted decision
- [ ] Security: authentication, authorisation, secrets management, threat model
- [ ] Observability: metrics, logs, traces, AI quality metrics

**Anti-Pattern Check:**
- Reject any design with tightly coupled services sharing a database without justification
- Reject AI model choices made without benchmarking against your specific use case
- Reject technology choices made without trade-off analysis (ADR required)
- Flag premature optimisation — do not design for 10x scale when you need 1x

**Phase 2 Quality Gate — Cannot proceed without:**
- [ ] Architecture diagram with clear component boundaries
- [ ] ADRs written for every significant design decision
- [ ] AI adaptation strategy documented (prompt engineering / RAG / fine-tuning rationale)
- [ ] System test strategy documented per component
- [ ] CI/CD pipeline architecture finalised
- [ ] Deployment topology and environment strategy confirmed
- [ ] Senior Solution Architect sign-off

**Claude Prompt:**
```
Act as a Senior Solution Architect and Senior AI Engineer.
Requirements: [FROM PHASE 1]   Stack constraints: [CONSTRAINTS]

Design the system architecture.
For the AI layer: which adaptation technique is correct for this use case and why?
For every design decision, document the trade-offs and rejected alternatives (ADR format).
Flag any design smell: tight coupling, shared state, unclear boundaries, over-engineering.
What does the system test strategy look like for this architecture?
```

---

### Phase 3 · DESIGN — Module & Detailed Design

**Sprint Duration:** 1–2 sprints
**Lead Role:** Senior Software Engineer
**Supporting Roles:** Senior Solution Architect · Senior AI Engineer
**V-Model Pair:** Integration Testing strategy defined here

**What must happen:**
- Decompose system components into implementable modules
- Define interface contracts per module: inputs, outputs, error states — these are binding
- Define data structures, domain models, and API contracts (OpenAPI/AsyncAPI specs)
- Document integration points between modules
- Write integration test strategy based on module interfaces
- For AI modules: design prompt templates, RAG retrieval pipeline, evaluation harness, and fallback behaviour
- Senior Solution Architect reviews module design for architectural compliance

**Frontend Module Design:**
- Component hierarchy and composition
- State management boundaries (local vs. global)
- API client contracts and error states
- Accessibility requirements per component

**Backend Module Design:**
- Service boundary definitions
- ORM models / SQL schema
- Async task queues (Celery, background workers)
- Authentication and authorisation middleware contracts
- Rate limiting and validation middleware

**AI Module Design:**
- System prompt templates (versioned)
- Retrieval pipeline design (chunking, embedding, retrieval strategy)
- Evaluation dataset structure
- Fallback and degradation strategy when the model is unavailable or returns low-confidence output
- Guardrail specifications: input sanitisation, output filtering, PII redaction

**Phase 3 Quality Gate — Cannot proceed without:**
- [ ] Module interface contracts documented
- [ ] API contracts defined (OpenAPI spec or equivalent)
- [ ] Data structures and domain models defined
- [ ] Integration test scenarios written per interface
- [ ] Module design reviewed against SOLID principles
- [ ] AI prompt templates versioned and documented
- [ ] Senior Solution Architect architectural compliance sign-off

---

### Phase 4 · BUILD — Implementation + Unit Testing

**Sprint Duration:** 2–3 sprints (repeating per module)
**Lead Role:** Senior Software Engineer
**Supporting Roles:** Senior DevOps Engineer · Senior AI Engineer
**V-Model Pair:** Unit Testing — executed in the same sprint as implementation

**What must happen:**
- Write unit tests before implementation — TDD, no exceptions
- Implement to the interface contract defined in Phase 3
- Every commit triggers the automated CI pipeline
- Code review required before any merge
- Static analysis, linting, and security scanning run automatically

**Build Rules — Senior Software Engineer:**
- No function longer than 30 lines without documented justification
- No magic numbers, magic strings — all constants are named and explained
- No incomplete error handling — happy path only is not acceptable
- No test code that only covers the happy path — edge cases and failures are mandatory
- No TODO comments — file a backlog item or fix it now

**Build Rules — Senior DevOps Engineer:**
- No merge that breaks the CI pipeline
- No merge without automated test results
- No hardcoded credentials, environment values, or configuration in code

**Build Rules — Senior AI Engineer:**
- No AI feature ships without at least a basic evaluation run on a held-out test set
- No prompt template changed without regression testing against previous evaluation results
- No RAG pipeline deployed without retrieval quality metrics validated
- Latency and cost budgets tested before integration — not after

**Phase 4 Definition of Done — Per Module:**
- [ ] Unit tests written first (TDD)
- [ ] All unit tests pass
- [ ] Code coverage ≥ 80%
- [ ] SOLID principles applied and verified in code review
- [ ] No static analysis violations
- [ ] CI pipeline green
- [ ] Senior Software Engineer code review approved
- [ ] For AI modules: evaluation metrics documented and passing threshold

**Claude Prompt — General Module Build:**
```
Act as a Senior Software Engineer with TDD and clean code expertise.
Module: [NAME]   Interface contract: [FROM PHASE 3]

1. Write comprehensive unit tests first — cover happy path, edge cases, and all failure paths.
2. Implement the code to pass every test. Follow SOLID throughout.
3. Review your implementation against the interface contract. Does it fully comply?
4. What would a senior engineer reject in a code review of this implementation?
5. What refactoring is needed before this is production-grade?
```

**Claude Prompt — AI Module Build:**
```
Act as a Senior AI Engineer.
Feature: [AI FEATURE]   Prompt template: [TEMPLATE]   Evaluation dataset: [DESCRIPTION]

1. Review this prompt template. How would you improve it for precision, consistency, and safety?
2. What evaluation metrics should we track for this feature?
3. What are the top 3 failure modes (hallucination, refusal, latency spike, cost overrun)?
4. Write the unit tests for the prompt pipeline — including adversarial inputs.
5. What guardrails need to be in place before this ships to users?
```

---

### Phase 5 · INTEGRATE — Integration & System Testing

**Sprint Duration:** 1–2 sprints
**Lead Role:** Senior DevOps Engineer
**Supporting Roles:** Senior Software Engineer · Senior Platform Engineer · Senior AI Engineer
**V-Model Pair:** Integration Testing + System Testing

**What must happen:**
- Connect all modules and verify interface contracts hold under real conditions
- Execute automated integration test suite in a staging environment (confirmed as production-mirror)
- System Testing validates the complete system against every requirement from Phase 1
- Performance testing: load tests, stress tests — verify NFR targets are met
- Security testing: penetration testing, dependency scanning, SAST/DAST results reviewed
- AI system testing: end-to-end evaluation pipeline run on full test set, human review of sample outputs
- Verify observability stack is active and alerting correctly

**Anti-Pattern Check:**
- Reject staging environments that differ from production in any material way
- Reject system tests that do not cover failure and recovery scenarios
- Reject deployments without passing security scan results
- Reject AI features without end-to-end evaluation run

**Phase 5 Quality Gate — Cannot proceed without:**
- [ ] All integration tests pass
- [ ] System tests pass against all Phase 1 requirements
- [ ] Performance targets from NFRs met
- [ ] Security scan clean — all critical and high findings resolved
- [ ] Staging confirmed as production-mirror
- [ ] Rollback procedure documented and tested
- [ ] AI evaluation pipeline run — metrics at or above threshold
- [ ] Observability active: metrics, logs, traces, and AI quality signals all flowing

---

### Phase 6 · DELIVER — Acceptance Testing & Production Deployment

**Sprint Duration:** 1 sprint
**Lead Role:** Senior Solution Architect
**Supporting Roles:** All Roles
**V-Model Pair:** User Acceptance Testing

**What must happen:**
- UAT validates the system meets every acceptance criterion written in Phase 1
- Senior Solution Architect confirms architectural integrity in the final system
- Senior DevOps executes production deployment via the fully automated pipeline
- Zero-downtime deployment strategy executed
- Post-deployment monitoring reviewed — no silent failures
- AI system: post-launch monitoring enabled for output quality, latency, cost, and user feedback signals
- Full documentation and lessons log finalised

**Senior Architect Final Check:**
- Does the delivered system match the architecture that was designed?
- Has any architectural drift occurred? Document it.
- Are all ADRs still accurate — or do they need updating to reflect what was actually built?

**Phase 6 Quality Gate — Cannot deploy without:**
- [ ] All UAT acceptance criteria from Phase 1 pass
- [ ] Senior Solution Architect architectural sign-off
- [ ] Deployment pipeline executed successfully in staging
- [ ] Rollback procedure tested and ready
- [ ] Post-deployment monitoring active — alerts configured
- [ ] AI quality monitoring active (output quality, cost, latency dashboards)
- [ ] Full documentation complete
- [ ] Lessons log updated

---

## IV. DOMAIN ENGINEERING LAYERS

### A. Frontend Engineering Layer

**Component Architecture:**
- Every component has a single, clearly defined responsibility
- Components are composable — built from smaller primitives
- State management is explicit: know what is local state vs. shared state vs. server state
- Props are interfaces — design them as contracts, not implementation details

**HTML & Accessibility Standards:**
- Semantic HTML always — headings in order, landmarks used correctly, lists for lists
- Every interactive element is keyboard accessible
- Colour contrast ≥ 4.5:1 for normal text, ≥ 3:1 for large text
- ARIA attributes used only where native HTML cannot express the intent
- Test with screen readers before shipping

**Responsive & Progressive Design:**
- Mobile-first — base styles for small screens, enhanced for larger
- Progressive enhancement — core functionality works without JavaScript
- Feature detection over browser detection
- Images are responsive; layout does not break at intermediate widths

**Frontend Performance:**
- Measure before optimising — use Core Web Vitals as the baseline
- Bundle size is a budget — track it in CI
- Images are lazy-loaded; fonts are preloaded; critical CSS is inlined
- SEO fundamentals: meta tags, Open Graph, canonical URLs, sitemap

**Build Toolchain:**
- Linting and formatting enforced in CI (ESLint, Prettier or equivalent)
- TypeScript for type safety — no `any` without justification
- Tests: unit (component), integration (user flows), visual regression

---

### B. Backend Engineering Layer

**API Design (REST):**
- Resources are nouns, not verbs — `/users`, not `/getUsers`
- HTTP verbs carry semantics: GET (read), POST (create), PUT/PATCH (update), DELETE (remove)
- Status codes are meaningful: 200, 201, 204, 400, 401, 403, 404, 409, 422, 500
- API versioning from day one — `/api/v1/`
- Pagination on all collection endpoints — never return unbounded lists
- OpenAPI specification is the source of truth — generated, not written manually
- Input validated at the boundary — nothing untrusted enters the service layer

**Service Layer:**
- Business logic lives in the service layer, not controllers or models
- Services are testable in isolation — no HTTP context required
- Transactions are explicit — know where your transaction boundaries are
- Errors are typed and propagated intentionally — no silent swallowing

**Database (PostgreSQL):**
- Schema is version-controlled via migrations — never edit production schema manually
- Every foreign key has an index; every query has an execution plan reviewed
- Connection pooling is configured (PgBouncer or equivalent) — not default Django/FastAPI settings
- Sensitive fields are encrypted at rest
- Backups are automated, tested, and restoration is documented

**Async Task Handling:**
- Long-running tasks are offloaded to a queue (Celery + Redis, RQ, or equivalent)
- Tasks are idempotent — safe to retry without side effects
- Dead-letter queues exist for failed tasks — silent drops are not acceptable
- Task results are observable — stored and queryable

**Security Checklist:**
- SQL injection: use parameterised queries always — ORM does not excuse carelessness
- Authentication: JWTs with short expiry, secure cookie flags, refresh token rotation
- Authorisation: row-level security considered for multi-tenant systems
- Input sanitisation: server-side, not just client-side
- Secrets: environment variables or a secrets manager — never hardcoded or committed
- HTTPS everywhere — no mixed content, HSTS enabled
- Rate limiting on all public-facing endpoints
- CORS configured restrictively — not `*` in production

---

### C. AI Engineering Layer

**The Adaptation Ladder (climb only as high as needed):**

```
Level 1 — Prompt Engineering
  Zero-shot → Few-shot → Chain-of-thought → System prompt tuning
  Cost: Low   Complexity: Low   Start here.

Level 2 — Retrieval-Augmented Generation (RAG)
  External knowledge injected at inference time
  Use when: knowledge is dynamic, proprietary, or too large for context
  Cost: Medium   Complexity: Medium

Level 3 — Fine-tuning
  Model weights adapted on domain-specific data
  Use when: style/format is critical, prompt engineering exhausted, latency budget tight
  Cost: High   Complexity: High   Requires labelled dataset

Level 4 — Dataset Engineering + Custom Models
  Use only at scale with proven ROI
  Cost: Very High   Complexity: Very High
```

**Prompt Engineering Standards:**
- System prompt is versioned alongside code — treated as production configuration
- Write clear, explicit instructions — assume the model needs to be told, not implied
- Provide sufficient context — task, constraints, output format, examples
- Break complex tasks into subtasks — one prompt should do one thing well
- Specify the output format explicitly — JSON schema, XML tags, or markdown structure
- Iterate: never accept the first prompt as final
- Organise and version prompts — a changed prompt is a changed system

**RAG Architecture:**
- Chunking strategy is deliberate: chunk size and overlap depend on content type
- Embedding model chosen for your domain — evaluate retrieval quality before deploying
- Retrieval evaluated independently from generation — separate evals for each
- Hybrid retrieval (dense + sparse) considered for complex queries
- Context window management: retrieved chunks ranked, truncated if needed
- Metadata filtering for multi-tenant or access-controlled knowledge bases

**Evaluation Pipeline:**
- Evaluation is built before the feature — not after
- Metrics defined per task type:
  - Factual QA: exact match, F1 score, RAGAS (faithfulness, answer relevance, context precision)
  - Code generation: functional correctness, pass@k
  - Open-ended generation: AI-as-judge with a rubric, human spot-checks
- Test set is held-out — never evaluated on training data
- Regression baseline: every prompt change is evaluated against the previous version
- Production metrics tracked: output quality score, latency P50/P95/P99, token cost per request, user feedback rate

**Guardrails:**
- Input: validate and sanitise all user input before it reaches the model
- Prompt injection: treat any user-supplied text as untrusted; apply defensive prompt engineering
- Output: filter for harmful content, PII, hallucinations where detectable
- Fallback strategy defined: what happens when the model fails, is slow, or returns low-confidence output
- Rate limiting and cost controls per user/tenant

**Inference Optimization:**
- Latency budget defined in NFRs — P95 latency is the metric, not average
- Caching: semantic caching for repeated or near-duplicate queries
- Streaming responses for long-form output — do not make users wait for the full response
- Model selection: choose the smallest model that meets quality requirements for cost efficiency
- Batching for offline or background AI tasks

**Agent Design:**
- Agents are defined by: goal, tools, planning strategy, memory
- Tool definitions are precise — ambiguous tool descriptions cause wrong tool selection
- Planning is explicit and auditable — reasoning steps are logged
- Failure modes are designed for: tool errors, infinite loops, conflicting tool outputs
- Agent actions are scoped — principle of least privilege for tool access
- Human-in-the-loop checkpoints defined for high-stakes actions

---

### D. Infrastructure & Deployment Layer

**Containerisation (Docker):**
- Multi-stage builds — production images contain only runtime dependencies
- `.dockerignore` is complete — no development artefacts in production images
- Non-root user inside containers — do not run as root
- Images are pinned to specific digests for reproducibility
- Container health checks defined — orchestrators rely on them

**Infrastructure as Code:**
- All environments defined in code (Terraform, CDK, Pulumi, or equivalent)
- No manual resource creation in any environment — if it is not in code, it does not exist
- State is remote and locked — no local state files
- Drift detection runs in CI — alerts on unmanaged changes

**CI/CD Pipeline:**
```
On every push:
  1. Lint + static analysis
  2. Unit tests
  3. Security scan (SAST, dependency audit)
  4. Build Docker image
  5. Push to registry (on main branch only)

On merge to main:
  6. Deploy to staging (automated)
  7. Integration tests against staging
  8. Performance baseline check
  9. Manual gate (or automatic if tests pass and confidence is high)
  10. Deploy to production (blue/green or canary)
  11. Post-deployment smoke tests
  12. Monitor for 30 minutes — auto-rollback on alert trigger
```

**Observability Stack:**
- **Metrics:** infrastructure (CPU, memory, disk, network), application (request rate, error rate, latency), AI (token cost, output quality score, retrieval latency)
- **Logs:** structured JSON logs, correlated with trace IDs, centralised (CloudWatch, Datadog, Loki)
- **Traces:** distributed tracing across services and AI pipeline steps
- **Alerts:** P1 alerts page immediately; P2 alerts notify within 15 minutes; all alerts have runbooks

**Zero-Downtime Deployment:**
- Blue/green: run two environments, switch traffic, keep old environment for rollback
- Canary: route a small percentage of traffic to new version, monitor, gradually increase
- Database migrations are backward-compatible — run before code deployment, never after
- Feature flags: decouple deployment from feature release — ship code dark, enable when ready

---

## V. QUALITY SYSTEM

### A. Three Quality Gates

Every phase must pass all three before proceeding. No exceptions.

| Gate | Question | Who Enforces |
|---|---|---|
| **Verified** | Are we building it correctly? (matches spec) | Senior Software Engineer |
| **Validated** | Are we building the right thing? (meets requirements) | Senior Solution Architect |
| **Production-Grade** | Would a senior engineer deploy this confidently? | All Roles |

---

### B. Definition of Done

A task is only "Done" when all of the following are true:

**Code Quality:**
- [ ] Tests written and passing (unit + integration where applicable)
- [ ] Code coverage ≥ 80% for the affected module
- [ ] Code review approved by a senior engineer
- [ ] Static analysis clean — no violations
- [ ] No TODO comments in production code

**Correctness:**
- [ ] Tested against the original acceptance criteria from Phase 1
- [ ] Edge cases and failure paths tested — not just the happy path
- [ ] For AI modules: evaluation metrics meet or exceed the defined threshold

**Operations:**
- [ ] CI pipeline green
- [ ] Docker image builds and runs correctly
- [ ] Deployed successfully to staging
- [ ] Observability confirmed — logs, metrics, and traces flowing

**Documentation:**
- [ ] Code is self-documenting or commented where intent is non-obvious
- [ ] API changes reflected in OpenAPI spec
- [ ] ADR written for any significant decision made during this task
- [ ] `tasks/todo.md` updated with completion status

**The Staff-Level Standard:** Ask — "Would a staff engineer approve this?" If the answer is "maybe", it stays in development. Seek the most elegant, non-hacky solution. If it feels like a hack, it is.

---

### C. SOLID Principles — Applied

| Principle | Rule | Violation Signal |
|---|---|---|
| **S** — Single Responsibility | One reason to change per class/module | "This module handles X and Y and Z" |
| **O** — Open/Closed | Open for extension, closed for modification | Editing existing code to add a new feature |
| **L** — Liskov Substitution | Subtypes substitutable for base types | Subclass breaks behaviour of base class |
| **I** — Interface Segregation | No fat interfaces — expose only what the consumer needs | "I have to implement methods I don't use" |
| **D** — Dependency Inversion | Depend on abstractions, not concretions | `import ConcreteEmailService` in business logic |

---

## VI. TASK MANAGEMENT PROTOCOL

### A. File Structure

```
repo-root/
├── AGENTS.md             ← Canonical, tool-agnostic agent instructions — see Section VII
├── CLAUDE.md             ← Claude Code entry point (imports AGENTS.md) — see Section VII
├── GEMINI.md             ← Antigravity entry point (workspace overrides) — see Section VII
├── tasks/
│   ├── todo.md           ← Active sprint tasks and status
│   ├── lessons.md        ← Lessons learned — updated after every correction
│   ├── harness-log.md    ← Harness-improvement result records — see Section VII.D
│   └── adr/              ← Architecture Decision Records
│       ├── 001-database-choice.md
│       ├── 002-ai-adaptation-strategy.md
│       └── 003-deployment-strategy.md
├── docker-compose.yml
├── .env.example
└── README.md
```

---

### B. The Six-Stage Execution Loop

Every task follows this protocol — from sprint kickoff to lessons archived.

| # | Stage | Action | File |
|---|---|---|---|
| 1 | **Plan** | Write the full plan before touching any code. For 3+ steps or architectural shifts: initialise Plan Mode. | `tasks/todo.md` |
| 2 | **Verify** | Confirm the plan is sound before execution. If execution deviates or fails — STOP. Re-plan before proceeding. | — |
| 3 | **Track** | Mark progress in real-time. Update task status as each module is completed, reviewed, and integrated. | `tasks/todo.md` |
| 4 | **Explain** | Provide high-level summaries of all changes. What was built, why, and how it connects to the system. | — |
| 5 | **Document** | Review results in the task log. Document the final output with a summary of what was built and how. | `tasks/todo.md` |
| 6 | **Evolve** | After any correction, immediately update lessons. Write rules to prevent the same mistake twice. Review at the start of every sprint. | `tasks/lessons.md` |

---

### C. Sprint Template

Use at the start of every sprint across all phases.

```markdown
── SPRINT START ──────────────────────────────────────────────────────

CONTEXT
  Project:          [NAME]
  Phase:            [CURRENT PHASE — 1 through 6]
  Sprint:           [N of N]
  Prior decisions:  [SUMMARY + ADR REFERENCES]
  Lessons reviewed: [KEY RULES FROM tasks/lessons.md]

SPRINT GOAL
  What we build:    [MODULE / FEATURE / INTEGRATION]
  V-Model pair:     [WHAT WE VERIFY OR VALIDATE THIS SPRINT]
  Acceptance:       [TESTABLE DONE CRITERIA — from Phase 1]

TASKS
  [ ] Task 1   Role: [ROLE]   Estimate: [HOURS]
  [ ] Task 2   Role: [ROLE]   Estimate: [HOURS]
  [ ] Task 3   Role: [ROLE]   Estimate: [HOURS]

── SPRINT END ────────────────────────────────────────────────────────

REVIEW
  Passed:         [LIST]
  Failed:         [LIST]
  Root causes:    [EXACT ANALYSIS — NO VAGUE SUMMARIES]

QUALITY GATES
  Verified:          Pass / Fail
  Validated:         Pass / Fail
  Production-Grade:  Pass / Fail

AI EVALUATION (if applicable)
  Metrics this sprint: [METRIC NAME: VALUE vs. THRESHOLD]
  Regression result:   [PASS / FAIL vs. BASELINE]

ARCHITECTURAL DRIFT
  Any deviation from agreed architecture: [YES / NO + DETAIL]
  ADRs updated: [YES / NO]

LESSONS EVOLVED
  New rule added to tasks/lessons.md: [SPECIFIC RULE]

── NEXT SPRINT READY ─────────────────────────────────────────────────
```

---

### D. Self-Correction Loop

- After any failure, correction, or deviation → update `tasks/lessons.md` immediately
- Write a specific rule to prevent recurrence — not a generic note
- Review all lessons at the **start of every sprint** — non-negotiable
- Mistake rate must trend toward zero across sprints
- A lesson not reviewed is a lesson not learned
- For a formal, evidence-based loop to improve the harness itself — not just log a single lesson — see Section VII.D

---

## VII. HARNESS ENGINEERING

*Keeping the environment vibrant, current, and identical across every coding tool the team uses.*

> Adapted from Ryan Lopopolo's [**Harness Engineering**](https://github.com/lopopolo/harness-engineering) anthology and playbooks. Harness engineering holds the model and the coding agent constant and treats them as a black box; it improves the two levers actually under your control — **context** and **tools** — and curates the environment around them, so the senior-engineer judgement defined in Section I survives contact with whichever coding tool the team opens today.

Sections I–VI define *what* a senior-grade delivery looks like. This section defines how that standard stays retrievable, current, and identical no matter whether an engineer is driving from **Claude Code**, **Antigravity IDE**, or any other agent the team adopts next quarter.
---

### A. The Core Idea

- An AI coding agent is only as senior as the environment around it. The Five Roles, the Six-Phase Cycle, and the Quality Gates in this document *are* that environment's judgement — this section keeps the judgement from silently drifting, going stale, or forking between tools.
- Improve the harness, not the model. When an agent misses a non-negotiable, the default move is not "write a longer prompt" — it is to ask which lever failed, context or tools, and fix that lever at its source, once, for every future session.
- The environment carries the organisation's non-functional requirements. Reliability, security, compatibility, and the quality bar in Section V are not enforced by hoping the agent remembers them — they are carried in retrievable context, canonical examples, typed boundaries, and executable checks.

---

### B. One Instruction Set, Many Entry Points

Maintain a single, tool-agnostic instruction file at the repository root. Give every AI coding tool a thin entry point that imports it rather than re-authoring it:

```
repo-root/
├── AGENTS.md    ← Canonical, tool-agnostic instructions:
│                    the Five Roles, Non-negotiables, Definition of Done,
│                    Quality Gates, and the tasks/ layout from Section VI
├── CLAUDE.md    ← Claude Code entry point — imports AGENTS.md, adds
│                    Claude Code–specific notes (subagents, plan mode, hooks)
└── GEMINI.md    ← Antigravity entry point — Antigravity-specific overrides;
                     Antigravity also reads AGENTS.md directly at the workspace root
```

This is not a hypothetical convention — it is how the source repository documents itself. Its own `CLAUDE.md` is nine lines: an `@AGENTS.md` import followed by three Claude Code–specific operating notes. Copy that shape:

```markdown
@AGENTS.md

## Claude Code

- Follow links from AGENTS.md just in time — do not preload the whole corpus.
- Use subagents for bounded evidence gathering and independent review.
  Keep the main thread responsible for decisive reading, application,
  verification, and task closure.
- Treat auto memory as local scratch state. Prefer AGENTS.md and the
  target system's own files when establishing facts.
```

**Why this keeps the project vibrant and seamless:** a new non-negotiable, a corrected lesson, or a new quality gate gets written once, in `AGENTS.md`. Every tool's thin wrapper picks it up on the next session — no hand-sync step, and no chance of two tools quietly disagreeing about what "done" means.

---

### C. Classify the Gap Before You Patch It

Section VI.D already asks you to update `tasks/lessons.md` after every correction. Before writing the new rule, classify what actually failed — the fix lives in a different place for each category:

| Gap | The agent lacked… | Fix it with |
|---|---|---|
| **Context** | information that was absent, stale, or never retrieved | a canonical example or fact in `AGENTS.md` — not a longer prompt |
| **Capability** | an operation that was unavailable, or hard to discover or invoke | a new tool, MCP server, or skill — not a workaround instruction |
| **Domain ownership** | one authoritative source for a type, schema, or invariant | a typed boundary, test, or canonical source — not a paragraph of prose |
| **Authority** | a clear scope, approval, or audit boundary for a mutation | an explicit permission rule or approval gate |
| **Proof** | a check that actually exercises the user-facing outcome | a real-system test — not an internal proxy check |
| **Feedback / delivery** | a lesson or artifact that survived past one session | a durable file (`AGENTS.md`, `lessons.md`) — not a chat-only correction |
| **Worker limitation** | reliable behaviour even when the environment is fully legible | *(see below — do not default here first)* |

One failed run is never enough to blame the model. Reach "worker limitation" only after the same job fails again under a materially equivalent, fully-legible environment — otherwise you are papering over an environment gap.

---

### D. The Harness-Improvement Loop

Run this loop on one bounded, representative job at a time — not as a sweeping audit. It closes the same way every time: **baseline → earliest gap → smallest owning intervention → verification → fresh rerun → retain, revise, or remove.**

**1. Record the job contract**
```
Target and revision:
Representative job:
Accepted outcome and evidence that proves it:
Fixed model / coding-agent configuration:
Authority envelope and budget:
Suspected harness gap:
```

**2. Observe the baseline** — run the job fresh, or inspect a recent comparable run, and record what was retrieved, which tools were invoked, where a human relayed facts the agent should have had, and every retry or abandoned path.

**3. Locate the earliest failed handoff** — trace the symptom upstream to one authoritative owner and classify it against the table in Section C.

**4. State one intervention hypothesis** before touching anything:
```
If <intervention> is added at <owner>, then the agent will
<observable behaviour change> on <the representative job>, because <mechanism>.
Evidence that would support this / weaken this:
Expected carrying cost and owner:
```

**5. Implement and verify at the claim boundary** — make the smallest reversible change at the earliest owner, then verify two layers: the target system's own checks, *and* the actual user-facing journey the job promised.

**6. Run a fresh trajectory** — same job class, same fixed configuration, a **new session** with isolated starting state. A pass in the same conversation that made the fix proves nothing; the intervention has to survive being rediscovered cold.

**7. Retain, revise, or remove** — retain when the fresh run closes the job and the gain justifies the upkeep; revise when the gap was correctly located but the interface is still hard to find or use; remove when it adds noise or duplicates a better owner. Log the decision in `tasks/harness-log.md`:

```
Job / accepted outcome:
Baseline evidence → earliest gap → owner:
Intervention and mechanism:
Fresh-rerun evidence:
Decision: retain | revise | remove
Reconsider when:
```

**Non-negotiables:**
- Never widen permissions, weaken a check, or redefine "accepted" just to make a rerun pass.
- Never import another project's file layout, fixtures, or version pins as a substitute for local ownership — adapt the idea, not the artifact.
- One before/after run supports a bounded claim about *this* job under *these* conditions — it does not prove a general treatment effect.

---

### E. Where Each Tool Picks This Up

Both companion guides implement everything above against the same `AGENTS.md` — they differ only in the file formats and mechanisms each tool provides natively:

| Concern | Claude Code | Antigravity IDE |
|---|---|---|
| Canonical instructions | `AGENTS.md` imported by `CLAUDE.md` | `AGENTS.md` read directly; `GEMINI.md` for overrides |
| Role-specific behaviour | Subagents in `.claude/agents/` | Rules or parallel named agents on the Manager Surface |
| Domain-layer scoping | Path-scoped rules in `.claude/rules/` | Rules with Model-Decision activation in `.agents/rules/` |
| Reusable procedures | Skills in `.claude/skills/` | Skills in `.agents/skills/` |
| Enforced (not just requested) checks | Hooks (`PreToolUse`, `PostToolUse`, `Stop`) | Workflows + native verification + CI as the hard gate |
| Multi-role parallel work | Subagents / agent teams | Manager Surface / parallel agents |


---

## VIII. STARTUP LIFECYCLE PLAYBOOK

### Stage 0 — Idea Validation (Pre-Code)

**Do before writing a single line of code:**
- [ ] Can you define the problem in one sentence?
- [ ] Who has this problem, and how do they solve it today?
- [ ] What does success look like in 90 days? In 12 months?
- [ ] Is AI the right tool, or is a simpler solution better?
- [ ] What is the riskiest assumption? How do you test it cheapest?
- [ ] What is the MVP — the smallest version that proves the core hypothesis?

---

### Stage 1 — Zero to MVP

**Stack Recommendations (lean defaults):**
- **Frontend:** React + Vite + Tailwind CSS — fast to build, easy to iterate
- **Backend:** FastAPI (Python) for new projects; Django if admin/ORM is critical
- **Database:** PostgreSQL — start relational, denormalise only when needed
- **AI:** OpenAI/Anthropic API with prompt engineering — no fine-tuning at MVP stage
- **Infrastructure:** Docker + Docker Compose locally; AWS (ECS Fargate or EC2 + RDS) for production
- **CI/CD:** GitHub Actions — simple, fast, integrated

**MVP Guardrails:**
- Build only what is needed to test the hypothesis — nothing more
- Prioritise correctness and observability over performance
- Collect user feedback from day one — embed analytics before you launch
- Every AI feature has an evaluation baseline before it ships — even a small one
- No custom auth at MVP — use a managed service (Auth0, Supabase, Clerk)

---

### Stage 2 — MVP to Product

**When you have validated the core hypothesis:**
- Refactor for maintainability — pay down MVP technical debt deliberately
- Introduce proper service layers, tested modules, and documented APIs
- Move from `docker-compose` to proper orchestration (ECS, Kubernetes)
- Formalise the evaluation pipeline for AI features
- Introduce feature flags for safe, incremental rollouts
- Establish proper observability — you cannot improve what you cannot measure

**AI Maturity Path:**
```
MVP Stage:      Prompt engineering only → eval on 50–100 examples
Growth Stage:   RAG for knowledge-intensive features → eval on 500+ examples
Scale Stage:    Fine-tuning where latency/cost justify it → full eval suite
```

---

### Stage 3 — Product to Scale

**Scaling decisions (only when data proves it is needed):**
- Database: connection pooling, read replicas, query optimisation, eventual partitioning
- Backend: horizontal scaling, caching layer (Redis), async task queues
- AI: inference optimisation (caching, batching, smaller models for sub-tasks), custom fine-tuned models
- Frontend: CDN, code splitting, edge rendering where appropriate
- Observability: full distributed tracing, AI quality dashboards, cost dashboards

---

### AI Integration Decision Tree

```
Is the task about processing or generating text/data?
  ├── No → Do not use AI. Use deterministic code.
  └── Yes ↓

Can a simple rule-based or search solution solve it?
  ├── Yes → Use that. AI is not needed.
  └── No ↓

Does prompting a foundation model solve it acceptably?
  ├── Yes → Use prompt engineering. Ship it.
  └── No ↓

Is the limitation knowledge (the model does not have the right facts)?
  ├── Yes → Use RAG. Implement retrieval pipeline.
  └── No ↓

Is the limitation style, format, or domain behaviour?
  ├── Yes → Consider fine-tuning. Requires labelled dataset + eval suite.
  └── No ↓

Reconsider the problem framing. The limitation may be the task definition.
```

---

## IX. QUICK REFERENCE PROMPT LIBRARY

### Situation → Prompt

| # | Situation | Prompt |
|---|---|---|
| 01 | Stuck on a problem | "Break this problem down for me step by step. Identify root cause before proposing a solution." |
| 02 | Need a plan | "Create a phased plan for building [X]. Include risks, unknowns, and dependencies." |
| 03 | Output is wrong | "Review this and tell me what's wrong. Point to the root cause. Do not suggest workarounds — fix the cause." |
| 04 | Need options | "Give me 3 different approaches to this. List trade-offs, costs, and the situation where each is correct." |
| 05 | Need documentation | "Document what we just built in clear, concise language. Include: what it does, how it works, and known limitations." |
| 06 | Need improvement | "Improve this. Make it cleaner and more efficient. Apply SOLID. Seek the elegant solution." |
| 07 | Final version | "Give me the final, polished version ready for production. Clean format. No TODOs." |
| 08 | Pivot required | "STOP. The current path is broken. Help me re-plan before we proceed. Identify what we got wrong." |
| 09 | Architecture review | "Review this architecture. Where is it fragile, coupled, or unclear? What would you reject?" |
| 10 | Code review | "Review this code as a senior engineer. What would you reject before merging? Be specific and exhaustive." |
| 11 | AI prompt review | "Review this prompt template. How would you improve precision, reduce hallucination risk, and enforce output format?" |
| 12 | Security audit | "Audit this for the OWASP Top 10 and common backend vulnerabilities. Flag every risk, not just the obvious ones." |
| 13 | Performance analysis | "Analyse this for performance bottlenecks. Where is latency introduced? What can be optimised without over-engineering?" |
| 14 | Deployment check | "Review this deployment pipeline. What failure modes exist? What is missing before I deploy to production?" |

---

### Role-Specific Prompt Starters

| Role | Starter |
|---|---|
| Solution Architect | `Act as a Senior Solution Architect with 15+ years of experience.` |
| Software Engineer | `Act as a Senior Software Engineer with deep expertise in clean code and TDD.` |
| DevOps Engineer | `Act as a Senior DevOps Engineer with deep expertise in CI/CD, IaC, and production reliability.` |
| Platform Engineer | `Act as a Senior Platform Engineer with deep expertise in IDPs, GitOps, and developer experience.` |
| AI Engineer | `Act as a Senior AI Engineer with deep expertise in foundation models, RAG, and production AI systems.` |

---

### Best Practices — Working with Claude at Full Capacity

| Practice | Description |
|---|---|
| **Always Provide Full Context** | Start every session with: Project name · current phase · summary of prior work · today's task. No context = no precision. |
| **Use Structured Prompts** | Use headers, numbered steps, and bullet points in complex questions. Unstructured prompts produce unstructured results. |
| **Request Step-by-Step Reasoning** | For complex problems, add: "Think through this step by step before giving your answer." Reasoning produces better solutions. |
| **Specify Output Format** | Declare the expected format — code block, markdown table, JSON schema, ADR template. Ambiguity wastes cycles. |
| **Iterate Aggressively** | Never accept the first output as final. Follow every response with: "Can you improve this? What did you miss?" |
| **Invoke the Right Role** | The role you invoke determines the lens applied. A DevOps engineer and a Software Engineer will approach the same problem differently — use both when both matter. |
| **Paste Prior ADRs and Lessons** | Start every session by pasting the relevant ADRs and your current `tasks/lessons.md`. Claude has no memory between sessions. |

---

## X. GLOSSARY

| Term | Definition |
|---|---|
| **ADR** | Architecture Decision Record — documents a design decision, its context, trade-offs considered, and rationale |
| **Agile** | Sprint-based iterative delivery with continuous feedback and backlog-driven prioritisation |
| **V-Model** | Each build phase is paired with a corresponding test phase — development and testing are parallel, not sequential |
| **Verification** | Confirming the product is built correctly — matches design and specification |
| **Validation** | Confirming the correct product is built — meets user and business requirements |
| **TDD** | Test-Driven Development — write tests before writing implementation code |
| **SOLID** | Five clean code principles: Single Responsibility, Open/Closed, Liskov, Interface Segregation, Dependency Inversion |
| **IaC** | Infrastructure as Code — all environments are version-controlled and reproducible |
| **GitOps** | The repository is the single source of truth for all environment configuration and deployment state |
| **Golden Path** | A pre-approved, standardised, opinionated template that works out of the box |
| **Quality Gate** | A mandatory checkpoint every phase must pass before work continues |
| **Definition of Done** | The explicit, non-negotiable criteria a task must meet to be considered complete |
| **Lessons Log** | A living document updated after every correction, reviewed at the start of every sprint |
| **Harness Engineering** | The practice of improving agent output by shaping the context and tools around a fixed model, rather than changing the model itself |
| **AGENTS.md** | A tool-agnostic, canonical Markdown file of project instructions that multiple AI coding tools read directly or import |
| **Gap Classification** | Sorting an observed agent failure into Context, Capability, Domain Ownership, Authority, Proof, Feedback/Delivery, or Worker Limitation before intervening |
| **Job Contract** | The recorded scope, target, accepted outcome, and evidence boundary for one bounded harness-improvement pass |
| **Retain / Revise / Remove** | The three-way decision that closes a harness-improvement pass after a fresh rerun against the baseline |
| **RAG** | Retrieval-Augmented Generation — external knowledge injected into the model context at inference time |
| **Foundation Model** | A large pre-trained model (LLM, multimodal) used as the base for AI application development |
| **Prompt Engineering** | Designing, structuring, and iterating on inputs to a foundation model to improve output quality |
| **Fine-tuning** | Adapting a model's weights on domain-specific data to change its behaviour |
| **Guardrails** | Input validation, output filtering, and fallback mechanisms that make AI systems safe and predictable |
| **Inference Optimization** | Techniques to reduce latency and cost when serving foundation model responses |
| **Semantic Cache** | A cache that stores model responses indexed by semantic similarity — reuses results for near-duplicate queries |
| **T-Shaped Developer** | A developer with broad knowledge across the full stack and deep expertise in at least one domain |
| **12-Factor App** | A methodology for building portable, resilient, scalable software-as-a-service applications |
| **Blue/Green Deployment** | Running two production environments; switching traffic atomically for zero-downtime releases |
| **Canary Release** | Routing a small percentage of traffic to a new version to validate before full rollout |
| **Spaghetti Architecture** | Undisciplined, tightly coupled design with no clear boundaries — rejected on sight |
| **God Object** | A class or module that knows and does too much — a single responsibility violation |

---

*Senior Engineer Master Workflow · v1.1*
*Full-Stack · Backend · Frontend · AI Engineering — Startup Development Playbook*
*Synthesized from Engineering Orchestration Framework v2 & v4 · AI Engineering (Chip Huyen) · The Full Stack Developer (Chris Northwood) · Harness Engineering (Ryan Lopopolo)*
*Iterative · Modular · AI-Augmented · Production-Ready from Day One · Tool-Agnostic*
*Companion guides: `claude-code-integration.md` · `antigravity-ide-integration.md`*
