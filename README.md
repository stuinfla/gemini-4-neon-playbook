# The Gemini 4 Neon Coding Playbook

The 20 highest-leverage practices that drive 95% of code quality, speed, and quota efficiency with **Google Gemini 4 Neon** across Antigravity, AGY CLI, Cursor, and direct API scripts.

- **[Download the 5-Page Playbook PDF](https://github.com/stuinfla/gemini-4-neon-playbook/raw/main/Gemini-4-Neon-Playbook.pdf)**
- **[Copy-Paste `GEMINI.md` Starter Template](./GEMINI.md)**

## Highlights
1. **Default real engineering to `High`, not `XHigh`** (avoids ~70% extra token/latency burn for marginal gains).
2. **Never toggle thinking level mid-session** — flipping effort wipes 100% of Neon's 95%-discounted implicit KV cache. Escalate via a fresh subagent instead.
3. **Lock a 10-line blueprint + explicit "Do NOT" boundaries** before multi-file edits.
4. **Write a failing test harness first**, then steer Neon mid-stream on the warm cache instead of wiping the session.
5. **Pair Neon (Planner/UX Architect) with Hydrogen (Executor)** and run an independent read-only `Neon High` adversarial audit before shipping.
