# DECISIONS.md

> Dated log of significant calls and *why*. Append-only — don't rewrite history; if a
> decision is reversed, add a new entry that supersedes the old one.

---

### 2026-06-07 — D1. Build ON Hermes, don't reinvent a runtime
Hermes Agent (Nous Research, MIT, released Feb 2026) is real and fits: self-hosted, six
sandbox backends, multi-channel gateway, `SKILL.md` (agentskills.io standard). This repo
holds config + persona + skills + strategy, not a custom agent runtime.

### 2026-06-07 — D2. LLM = hosted open-source, not local (proceeding, reversible)
Machine is a 16GB M2 Pro also used to build products. Local 8B models would starve dev
work AND give weaker marketing reasoning — the worst failure for a beginner relying on
the agent's judgment. Decision: strategist brain = capable hosted OSS (DeepSeek-V3 /
Nous Hermes 4) via OpenRouter (cents/day); routine/auxiliary tasks = cheapest tiny model
or local later. Revisit once real usage is known.

### 2026-06-07 — D3. v1 platform = X first; Telegram later
X is a discovery platform (algorithmic reach to non-followers) → grows *new qualified
reach*, the 90-day goal. Telegram is a community/conversion layer, added once there's
reach to convert.

### 2026-06-07 — D4. v1 anchor account = @orai_intern (new AI persona)
Chosen over @tucq88. Rationale: (a) cold-start risk is neutralized because @oraichain
(79K) + @tucq88 (800) can seed it; (b) an openly-AI account is the honest home for an AI
agent (no ghost-writing/ToS tension; automation becomes the feature); (c) narrative =
live demo of Oraichain's core competency (AI agents that do real work). @oraichain =
PROTECTED amplifier (never autonomous). @tucq88 = founder amplifier (human-approved).

### 2026-06-07 — D5. Sandbox backend = Docker for v1 (proposed, confirm in Step 1)
Local, free, full isolation (namespaces, cap-drop). Nothing runs on the bare host.
Modal/Daytona considered for always-on cloud later if the "keep working when I go quiet"
goal needs it.

### 2026-06-07 — D6. Primary target = new traders/depositors; $ORAI community = channel
Success measured by depositors/active traders (qualified reach), not follower count or
token sentiment (vanity reach, inflated by bots/farmers in crypto).

### 2026-06-07 — D7. Positioning wedge = spectrum of control + performance-backed vault
Differentiator: choose your custody level (non-custodial DEX ↔ performance-backed
custody vault), same AI engine. Buying trigger = losing money FOMO-trading manually;
core emotional benefit = **discipline** (AI removes the emotional failure mode).

### 2026-06-07 — D8. Phased autonomy: everything starts in draft-and-approve
Nothing posts or sends publicly without approval at first. Task types graduate to
autonomous individually as trust is earned, tracked in `TRUST.md`.
