# Prompt-to-Production PR Checklist

A comprehensive, no-fluff checklist for PRs across frontend, backend, and integration workflows using AI.

> 💡 Read this first:
>
> You don’t need to adopt every item here to see real productivity gains.
>
> Think of this as a _menu_ — not a mandate.
>
> Start with a few high-leverage changes (like AI scaffolding or test prompts), then layer on more as your workflow evolves.
>
> The goal isn’t to be perfect.
>
> It’s to build a system that gets smarter with every PR.

Throughout this checklist, “AI” refers to modern large language models (LLMs) such as **Claude (Opus or Sonnet), GPT-4, Copilot, and other context-aware AI assistants** integrated into your IDE or dev environment.

References to tools like “Jira/Notion” should be read as **“your preferred project management or documentation platform.”**

---

### 1. Frame the Feature

**Why it matters:** Spending 5–10 minutes here typically saves 3–5 hours of rework, clarification, or late-cycle refactoring.

**Goal:** Scope clearly before coding. Prevent churn by using AI to clarify the problem, not just generate code.

**Pro Tip:** If your AI outputs are vague, your specs were too. Ask AI to “think like a senior engineer” — not just generate a plan.

**Checklist:**

- [ ] Scoped the feature using AI with a spec-generation prompt

- [ ] Prompt generated clarifying questions and surfaced hidden product assumptions

- [ ] Output pasted into project workspace (e.g. task ticket or documentation) as a design artifact or shared spec

- [ ] Ticket spec validated against real system constraints (e.g. known APIs, state flows, auth models)

- [ ] Prompt summary included in PR or linked for auditability

- [ ] For full-stack: Prompted AI to identify and resolve integration boundaries — e.g. shared types, API schemas, frontend/backend handshake requirements

- [ ] Prompt structured to return output in markdown or a predefined schema for pasting/reuse

- [ ] AI-generated spec reviewed or cross-checked with team/domain expert

---

### 2. Forge the Foundation

**Goal:** Use AI to scaffold with speed and structure. Avoid repetitive setup work and build reusable prompt assets.

**Why it matters:** Most dev time is lost in setup churn. Smart scaffolding removes the friction layer.

**Pro Tip:** Avoid “super prompts.” Instead, chain smaller ones to keep output modular — just like your code.

**Checklist:**

- [ ] Used AI to scaffold core files or components

- [ ] Prompt included tech stack, validation library, folder path, or other context

- [ ] Output reviewed for:
    - [ ] Clean architecture (folder structure, naming, separation of concerns)
    - [ ] Overgeneration, hidden coupling, or invalid defaults

- [ ] Prompt reused or adapted from internal Prompt Library

- [ ] Prompt saved/updated to Prompt Library after use

- [ ] Scaffold diff includes prompt citation as inline comment or PR link

- [ ] For full-stack: Checked that frontend + backend scaffolds share consistent data shapes, field names, and validation logic

- [ ] AI-generated code run through linter + formatter (e.g., ESLint, Prettier, stylelint)

- [ ] Prompt explicitly included input/output contracts (e.g., data types, schemas)

- [ ] Prompt included AI model reference in comments or PR description (if needed for traceability)

---

### 3. Fortify with Tests

**Goal:** Prevent bugs with AI-generated tests — not just patch them after they hit prod.

**Why it matters:** Test prompts are more reusable than tests — they capture output and intent.

**Pro Tip:** Every test is a reusable prompt. Save them, evolve them, and ship them with confidence.

**Checklist:**

- [ ] AI-generated test cases included (unit, E2E, schema, boundary, negative cases)

- [ ] Prompt written before feature code, based on feature spec or prompts

- [ ] Prompt included real edge conditions:

    - [ ] Empty/malformed input
    - [ ] Auth + permission conditions
    - [ ] Slow/broken networks or retries
    - [ ] Concurrency or async flows

- [ ] Prompt validated with Promptfoo:
    - [ ] Output structure matches expected shape
    - [ ] No hallucinations or omitted cases
    - [ ] Test coverage appropriate for business risk

- [ ] Output passed Guardrails schema validation

- [ ] Prompt + test combo added to Prompt Library or prompt-regression CI suite

- [ ] For full-stack: Added E2E tests using UI or API-level test tools (e.g. Playwright, Cypress, Postman)

- [ ] Prompt includes testing library and tool version (e.g., Jest 29, Zod 3.x) to prevent syntax drift

- [ ] Promptfoo + Guardrails results logged in CI for auditability

- [ ] High-value test prompts flagged for refactoring into reusable prompt templates

- [ ] Covered common frontend states (loading, error, null) and backend risk factors (e.g., XSS, SQLi, timeouts)

---

### 4. Fine-Tune the Flow

**Goal:** Move from “it works” to “it’s production-grade.” AI should refine your thinking, not just your syntax.

**Why it matters:** AI won’t catch everything — but it helps you think better and faster.

**Pro Tip:** Ask AI to simulate a senior reviewer or PM. Train it to give you the review you wish you had.

**Checklist:**

- [ ] Used AI to review full file or PR diff with prompts like:

    “Review this for async, readability, and error handling.”

    “What race conditions or accessibility gaps might exist?”

- [ ] Feedback accepted or rejected with documented reasoning in PR

- [ ] Prompt used to generate refactor suggestions with rationale (e.g. “This violates SRP.”)

- [ ] Asked AI for tradeoff-based design feedback (e.g. “What are pros/cons of this abstraction?”)

- [ ] Accessibility and performance issues flagged and addressed (e.g., aria-\*, debouncing)

- [ ] For full-stack: Asked AI to review cross-layer abstractions for tight coupling (e.g., component depends too tightly on raw API shape or schema)

- [ ] Asked AI to flag performance pitfalls (e.g., large renders, N+1 queries, memory leaks)

- [ ] Prompt included relevant security threats or threat model hints when applicable

- [ ] AI feedback reviewed for project code style and team norms before adoption

- [ ] Any accepted AI refactors noted in commit message or PR comment with source prompt

---

### 5. Finalize + Ship

**Goal:** Use AI to finish the meta-layer — changelogs, commit messages, reviewer guidance — with zero drag.

**Why it matters:** Bad PR hygiene breaks trust, slows teams, and increases review friction. AI-native devs don’t skip this.

**Pro Tip:** Let AI handle 80% of this. You just need to verify, not start from scratch.

**Checklist:**

- [ ] Used AI to generate:
    - [ ] PR title and description
    - [ ] Changelog entry (user-facing impact + tech context)
    - [ ] Descriptive commit messages
    - [ ] AI prompted to roleplay as PM/QA and check that summary is readable and relevant

- [ ] Reviewer checklist included:
    - [ ] What changed
    - [ ] What to test
    - [ ] Edge cases covered

- [ ] PR cleaned up: removed WIP comments, TODOs, debug logs

- [ ] Prompt sourced from full diff or structured commit history for accuracy

- [ ] Output formatted to match Conventional Commit or Changelog schema requirements

- [ ] Prompt or summary tool noted in PR description (for visibility/auditability)

- [ ] If available: PR auto-comment generated by AI agent or bot as reviewer primer

- [ ] Reviewer instructions surfaced explicitly in prompt (e.g. “Highlight risk areas for reviewer to focus on”)

---

### 6. Feedback & Learn

**Goal:** Turn bugs into system upgrades — update prompts, tests, and understanding every time something breaks.

**Why it matters:** Your system should get smarter with every failure. Feedback loops are the compounding layer.

**Pro Tip:** If AI generated the bug, it likely didn’t have enough context. Instead of just fixing the code, improve the prompt that produced it. You’re not just patching — you’re upgrading the system that wrote it.

**Checklist:**

- [ ] Stacktrace pasted into AI for diagnosis + fix + regression test

- [ ] AI-generated regression test added to suite

- [ ] Prompt that caused issue updated or improved

- [ ] Prompt improvement logged or versioned for future reuse

- [ ] Failure pattern added to Promptfoo test coverage

- [ ] Prompt+test loop closed within same PR or postmortem doc

- [ ] If low-severity: root cause + fix explained in plain language in PR or test comment

- [ ] For full-stack: Added notes if the bug occurred due to a cross-layer mismatch (e.g., schema change not reflected in client prompt or validation)

- [ ] Bug severity annotated in prompt/test repo (e.g., high, low, flaky)

- [ ] Guardrails schema updated if failure revealed a structural gap

- [ ] Regression prompt added to Promptfoo with meta-comment (context, author, linked fix)

- [ ] New prompt or test added to “Known Prompt Pitfalls” for onboarding/reference

---

### Final Word

A great PR is technically correct, structured, transparent, testable, and teachable.

This checklist gives you an AI-native system for producing high-quality full-stack work — even at speed.


**You’re training the system as you ship code.**

---

### 📊 Want to Audit Your Workflow?

Use the [AI-Native Developer Scorecard](https://tally.so/r/nWB0gQ) to see where you are in the journey — and what to improve next.

---

### Stay Sharp

Want more systems, checklists, and frameworks like this?

**Subscribe to my newsletter** for weekly deep dives on AI-native development:

👉 [Prompt/Deploy](https://prompt-deploy.beehiiv.com/subscribe)
