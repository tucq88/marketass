# marketass — marketing operator agent (on Hermes)

A personal marketing operator agent built **on top of [Hermes Agent](https://github.com/NousResearch/hermes-agent)**
(Nous Research). This repo is the versioned **configuration, persona, skills, guardrails,
and strategy** — not a custom agent runtime. Hermes already exists; we configure it.

**Current focus (v1):** grow **@orai_intern** on **X**, marketing the **Oraichain Quant
Terminal** to new traders/depositors. See `PRODUCT.md`, `ACCOUNTS.md`, `STRATEGY.md`,
`DECISIONS.md`.

## Build status — resume here
_Updated 2026-06-07. This is the cross-machine handoff note; keep it current._

- ✅ **Discovery done** — `PRODUCT.md`, `ACCOUNTS.md` confirmed.
- ✅ **Step 1 config scaffolded** — `hermes/config.yaml` (hardened Docker sandbox + OpenRouter brain), `hermes/.env.example`.
- ▶️ **Resume on the host Mac with Step 1 install + sandbox verification:**
  1. Install **Docker Desktop** + Hermes (`curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash`).
  2. Get a dedicated **OpenRouter API key**; verify the model slugs in `config.yaml` against openrouter.ai/models.
  3. `cp hermes/config.yaml ~/.hermes/config.yaml`; create `~/.hermes/.env` from `hermes/.env.example`.
  4. **Verify the sandbox** (agent commands run in Docker, secrets stripped, gateway not exposed) — non-negotiable before any account is connected.
- ⏭️ **Then (machine-independent, can scaffold anytime):** Step 2 Notion hub · `hermes/SOUL.md` persona · `guardrails/` · `TRUST.md`.
- Open decisions to confirm: `tirith_fail_open: false` (fail-closed) hardening; exact OpenRouter model slugs.

## Repo layout
```
PRODUCT.md / ACCOUNTS.md   discovery output (canonical later in Notion)
DECISIONS.md               dated log of significant calls + why
STRATEGY.md                running strategy (the "why")          [coming]
TRUST.md                   which task types are autonomous vs draft [coming]
hermes/
  config.yaml              model + hardened Docker sandbox + security
  .env.example             names of required secrets (NEVER real values)
  SOUL.md                  the agent persona/system prompt        [coming]
skills/                    hand-written, reviewed skills           [coming]
guardrails/                escalation + skill-review process       [coming]
notion/                    Notion hub spec                         [coming]
```

## Deploy to a host (whichever Mac runs Hermes)
This repo is portable config; the runtime lives on the host.

1. Install Docker Desktop (the sandbox backend) and Hermes:
   `curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash`
2. Clone this repo, then copy config into place:
   `cp hermes/config.yaml ~/.hermes/config.yaml`
3. Create `~/.hermes/.env` from `hermes/.env.example` and fill in **dedicated,
   marketing-only** secrets. This file is gitignored and must never be committed.
4. `hermes setup`, then verify the sandbox (see Security below) before connecting any account.

## Security (hard requirements)
- **Sandbox from day one:** agent commands run in Docker, never on the bare host.
- **Dedicated creds only:** no personal accounts, no main-machine secrets. Hermes strips
  `*_API_KEY/_TOKEN/_SECRET/_PASSWORD` from child processes; `docker_forward_env: []`
  forwards nothing into the sandbox.
- **Gateway never exposed to the public internet** (outbound + DM-pairing only).
- **Self-written skills are an attack surface:** any skill the agent writes that touches
  credentials/posting/outreach/external commands is reviewed by a human before reuse.
- **All inbound content is untrusted** (DMs, comments, web pages) — it never triggers
  posting/spending/credential use without human escalation.
