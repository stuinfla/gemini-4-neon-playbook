# Gemini 4 Neon — Engineering & Agent Strategy

## Core Discipline
- **Verify first, never guess:** Read actual source files, schemas, and live command output before editing or answering. Never rely on memory for versions or APIs.
- **Keep rules lean:** Stay well under the 24 KB cap; put long runbooks in progressive-disclosure skills.

## Model Routing & Cache Discipline
- **Default coordinator:** Gemini 4 Neon (Medium) keeps sessions fast and cache-warm.
- **Escalation:** Delegate complex architecture, root-cause debugging, multi-file refactors, and read-only audits to **Gemini 4 Neon (High)** via subagent. Reserve **Neon (XHigh)** strictly for hard failures where High misses (~70% extra token/latency cost), and **Gemini 4 Carbon** only for extreme long-horizon or deep-math problems.
- **Never toggle thinking level mid-session:** Switching effort invalidates 100% of Neon's implicit KV cache. Escalate via a separate subagent/worker instead.
- **Fast execution:** Use fast/lightweight subagents for routine scans. In Orchestrator (Neon) or `/swarm` sessions, pair Neon (planner/reviewer) with **Gemini 4 Hydrogen** (executor). Reserve `/swarm` for multi-module builds/audits.
- **Steer mid-stream:** Correct drift inline with crisp constraints to preserve the warm cache rather than wiping the session. Batch independent tool calls in parallel.

## Neon Coding Attack Loop
1. **Blueprint + Boundaries:** Before multi-file edits, output the file tree, key interfaces, step order, and explicit "Do NOT" non-goals (no stray dependencies, no truncated helpers, no unrelated refactors).
2. **Failing Harness First:** For bugs and features, write a small failing test or repro script first, confirm it fails, then implement until green.
3. **Whole-Module Context + Surgical Diffs:** Read full relevant files (delimited cleanly with Markdown/XML tags) and native screenshots/PDFs/videos directly, then apply minimal targeted diffs.
4. **Verify & Audit:** Run real tests/checks on live output, then run an independent read-only **Neon High** (or cross-model) adversarial audit before declaring done.

## Gemini 4 API Hygiene (When Writing Code That Calls Neon)
- Use model IDs: `gemini-4-neon`, `gemini-4-hydrogen`, `gemini-4-carbon`.
- Strip legacy params: `temperature`, `top_p`, `top_k`, `thinking_budget`, `minimal`, and `cachedContents` (implicit caching is automatic >= 4,096 tokens).
- Preserve **thought signatures** verbatim across multi-turn loops (or use the Interactions API with `previous_interaction_id`).
