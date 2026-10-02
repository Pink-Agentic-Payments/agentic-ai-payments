# Agentic AI Payments

Web version: [pink-agentic-payments.github.io/agentic-ai-payments](https://pink-agentic-payments.github.io/agentic-ai-payments/)

**Agentic AI payments are payments an AI agent initiates on a person's or company's behalf — the agent decides what to buy and when, but a separate policy layer (budgets, allowlists, human approval) decides whether the payment actually clears.** This repo is an open, source-linked guide to how that works today: the protocols agents use to pay, the providers that support them, and the controls that keep an agent from spending more than it should — with [Pink Agentic AI Payments](https://pinkwallet.com/agentic/) as a fully worked, runnable example.

Everything here is sourced. Every claim about a provider other than Pink links to that provider's own documentation, with a verbatim quote and an access date, pulled from two open datasets this org also publishes (see [Providers](#providers) below). Nothing here is paid placement — entries are selected on relevance, including competitors.

## Contents

- [How agents pay today](#how-agents-pay-today)
- [Providers](#providers)
- [Controlling agent spending](#controlling-agent-spending)
- [Try it: Pink Agentic AI Payments sandbox](#try-it-pink-agentic-ai-payments-sandbox)
- [Framework examples](#framework-examples)
- [FAQ](#faq)
- [Related reading](#related-reading)

## How agents pay today

No single protocol dominates; most providers in this guide support zero or one of the five named programs below, and several (including Pink) don't implement any of them yet — see the [providers table](#providers) and the dataset's [D3 breakdown](https://github.com/Pink-Agentic-Payments/agentic-payments-readiness#d3--self-described-protocol-support) for exactly who claims what.

- **[x402](https://docs.x402.org/faq)** — Turns the HTTP `402 Payment Required` status code into an onchain payment layer: a server can ask for payment inline in an HTTP response, and an agent's wallet signs and retries. Operational under Linux Foundation governance since 2026-07-14 as the x402 Foundation, with 40 member organizations. Apache-2.0.
- **[Agent Payments Protocol (AP2)](https://github.com/google-agentic-commerce/AP2)** — Google-originated protocol using "Mandates — tamper-proof, cryptographically-signed digital contracts that serve as verifiable proof of a user's instructions." Donated to the FIDO Alliance on 2026-04-28 to keep it "platform-agnostic and community-led." Apache-2.0.
- **[Agentic Commerce Protocol (ACP)](https://agenticcommerce.dev)** — "An interaction model and open standard for connecting buyers, their AI agents, and businesses to complete purchases seamlessly." Co-developed by Stripe and OpenAI; currently in beta. Apache-2.0.
- **[Visa Trusted Agent Protocol (TAP)](https://usa.visa.com/about-visa/newsroom/press-releases.releaseId.21716.html)** — A cryptographic message-signing standard (RFC 9421) merchants use to verify an agent's identity before checkout. Announced 2025-10-14 with Cloudflare; it verifies the agent, it does not itself move money.
- **[Mastercard Agent Pay](https://newsroom.mastercard.com/news/press/2025/april/mastercard-unveils-agent-pay-pioneering-agentic-payments-technology-to-power-commerce-in-the-age-of-ai)** — Announced 2025-04-29, built on Mastercard's existing tokenization used for mobile contactless and card-on-file payments. "Consumers will have complete control over what the agent is allowed to purchase on their behalf."

For a longer comparison of the three software-layer protocols, see [x402 vs AP2 vs ACP](https://pinkwallet.com/agentic/learn/x402-vs-ap2-vs-acp/) and this org's [awesome-agentic-payments](https://github.com/Pink-Agentic-Payments/awesome-agentic-payments) list, which also covers UCP, MPP, and other emerging programs.

## Providers

This table is built from the [agentic-payments-readiness](https://github.com/Pink-Agentic-Payments/agentic-payments-readiness) dataset (17 companies including the publisher, 7 scoring dimensions, every row sourced to the provider's own docs with a verbatim quote). Legend: **✓** yes · **◐** partial · **✗** no · **?** not verified in the dataset (not a confirmed absence) · **–** not applicable/no data found.

| Company | Agent SDK | MCP server | Sandbox | Spend limits | Card rail | Bank rail | Stablecoin rail | Pricing |
|---|---|---|---|---|---|---|---|---|
| **Payment processor / PSP** | | | | | | | | |
| Adyen | ✓ | ✓ | ? | ? | – | – | – | not found |
| Airwallex | ✓ | ✓ | ◐ | ? | ? | ? | ? | not found |
| Checkout.com | ? | ✓ | ✓ | – | – | – | – | not found |
| Mollie | ✓ | ✓ | ✓ | ? | ? | ◐ | ? | general rates |
| PayPal | ? | ✓ | ◐ | ✓ | ✓ | ? | ? | not found |
| Square | ✓ | ✓ | ✓ | ? | ◐ | ? | ? | general rates |
| Stripe | ✓ | ✓ | ✓ | ◐ | ? | ? | ✓ | general rates |
| Wise | ✗ | ✗ | ✗ | – | ? | ? | ? | not found |
| **Card network** | | | | | | | | |
| Visa | ✓ | ✓ | ✓ | ? | ✓ | – | ? | not found |
| Mastercard | ✓ | ✓ | ? | ? | – | – | – | not found |
| **Stablecoin / crypto infra** | | | | | | | | |
| Circle | ✓ | ✓ | ✓ | ✓ | ? | ? | ✓ | general rates |
| Coinbase | ✓ | ? | ✓ | ✓ | ✗ | ✗ | ✓ | not found |
| Tempo | ✓ | ✓ | ✓ | ✓ | ? | ? | ✓ | agent-specific |
| **Agent-payment specialist** | | | | | | | | |
| Skyfire | ✓ | ? | ✓ | ✓ | ✓ | ✓ | ✓ | not found |
| Payman | ✓ | ✓ | ? | ? | – | – | – | not found |
| Crossmint | ✓ | ✓ | ✓ | ✓ | ✓ | ? | ✓ | not found |
| **Publisher (self-scored)** | | | | | | | | |
| **Pink Agentic AI Payments** | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ? | not found |

Pink Agentic AI Payments is included as a row, labeled **publisher; self-scored; sandbox stage**, scored under the identical 7-dimension methodology applied to the other 16 companies — not an independent third-party assessment of Pink. See the dataset's ["How Pink Agentic AI Payments compares"](https://github.com/Pink-Agentic-Payments/agentic-payments-readiness#how-pink-agentic-ai-payments-compares) section for the sourced detail behind Pink's row, including where it is explicitly behind (no x402/AP2/ACP/Visa TAP/Mastercard Agent Pay support; early access, production not yet available; no published production pricing).

Full per-check detail, every quote, and the raw CSV: [agentic-payments-readiness](https://github.com/Pink-Agentic-Payments/agentic-payments-readiness) · [Hugging Face dataset viewer](https://huggingface.co/datasets/Agentic-Payment/agentic-payments-readiness).

## Controlling agent spending

Letting an agent authenticate to a payment rail is the easy half of the problem; the hard half is making sure it can't spend more than it should. The mechanisms providers actually document, in roughly increasing order of how much they can stop:

- **Budgets** — a cap over a time window (per day, per week, per month) that resets on schedule. Circle's wallet CLI enforces a monotonic `per-tx ≤ daily ≤ weekly ≤ monthly` chain; Tempo's wallet keys carry independent per-key limits.
- **Per-payment caps** — a ceiling on a single transaction, independent of any running total. The most commonly documented control type across the 14 providers/protocols in the crosswalk below.
- **Allowlists / category blocks** — restricting *who* an agent can pay (a merchant/recipient allowlist) or *what kind* of purchase (blocking categories like gift cards or crypto outright).
- **Approvals** — routing a payment to a human instead of silently allowing or blocking it. Documented by name for a minority of providers: Stripe's MCP write actions require confirmation via a URL that expires after 24 hours; Circle gates a limit *increase* behind a human-entered OTP.
- **Default-block** — treating anything a policy doesn't explicitly allow as blocked, rather than defaulting to allow. This is a design choice, not a universal default; check each provider's own docs for which way it falls.
- **Fraud signals** — checks that run regardless of amount, like a payee's bank details changing recently or an invoice number being paid twice.

No two providers name these the same way or enforce them at the same point (authorization-time at the card network, onchain, API server-side, or client-side SDK). This org publishes two datasets that map the differences field-by-field:

- **[agent-spending-controls-crosswalk](https://github.com/Pink-Agentic-Payments/agent-spending-controls-crosswalk)** — 14 providers/protocols plus the publisher, mapped to the exact field or setting each documents for amount caps, allowlists, category blocks, single-use credentials, approvals, expiry, and revocation, each with a quoted source.
- **[agent-spending-policy](https://github.com/Pink-Agentic-Payments/agent-spending-policy)** — a draft v0.1, vendor-neutral JSON Schema for describing an agent's spending policy, with every field mapped to its native equivalent (or lack of one) across the same 14 providers. Explicitly not a standard.

## Try it: Pink Agentic AI Payments sandbox

[Pink Agentic AI Payments](https://pinkwallet.com/agentic/) (by PinkWallet) is the approval layer between AI agents and company money: plain-language rules, per-agent budgets and human approvals decide each payment before a single-use card or bank transfer is issued. **Status: early access — a live public sandbox with test credentials; production is not yet available; no real money moves.**

**1. Create a free workspace** (no signup, no sales call):

```bash
curl -X POST https://agentic-sandbox.pinkwallet.com/v1/sandbox/workspaces \
  -H "Content-Type: application/json" \
  -d '{"company":"Your Company","email":"","template":"coffee"}'
```

This returns a `workspace_id`, 4 pre-registered agents (each with its own key, vault, monthly budget, and per-payment cap), and `urls.console` / `urls.mcp` / `urls.rest`. Confirmed live by this guide on 2026-10-02 (`HTTP 201`, one workspace created, deleted after inspection — no agent/admin key was committed to this repo).

**2. Connect an agent** — e.g. for Claude Code (full client list and configs: [pinkwallet.com/agentic/connect/](https://pinkwallet.com/agentic/connect/)):

```bash
claude mcp add --transport http pink https://agentic-sandbox.pinkwallet.com/mcp --header "Authorization: Bearer <AGENT_KEY>"
```

**3. Ask it to pay something.** Every payment request resolves to exactly one of three outcomes:

- **`allowed`** (HTTP 201) — within budget, known payee, a rule matched: a single-use virtual card or bank-transfer credential is issued immediately.
- **`pending_human`** (HTTP 202) — a rule routes it to a named approver or quorum; the request waits as a hold until approved, declined, or it times out.
- **`blocked`** (HTTP 403) — a circuit breaker (budget, ceiling, paused agent) or an unmatched default-block rule stops it outright, with no approval path.

Runnable, real-output versions of this same flow (curl, MCP SDK, REST, an agent loop) are in [sandbox-examples](https://github.com/Pink-Agentic-Payments/sandbox-examples).

## Framework examples

Runnable agent-framework integrations against the same live sandbox, from [sandbox-examples](https://github.com/Pink-Agentic-Payments/sandbox-examples):

- **[05-langgraph](https://github.com/Pink-Agentic-Payments/sandbox-examples/tree/main/05-langgraph)** — a [LangGraph](https://github.com/langchain-ai/langgraph) ReAct agent using `langchain-mcp-adapters`, covering all three decision outcomes plus a prompt-injection probe that gets blocked server-side.
- **[06-openai-agents-sdk](https://github.com/Pink-Agentic-Payments/sandbox-examples/tree/main/06-openai-agents-sdk)** — an [OpenAI Agents SDK](https://github.com/openai/openai-agents-python) agent using `MCPServerStreamableHttp`, OpenAI-first with a Gemini/LiteLLM fallback.
- **[07-haystack](https://github.com/Pink-Agentic-Payments/sandbox-examples/tree/main/07-haystack)** — a [Haystack](https://github.com/deepset-ai/haystack) `Agent` using the official `mcp-haystack` `MCPToolset`.

## FAQ

**What is agentic AI payment?**
A payment that an AI agent initiates — deciding what to buy and when — while a separate policy layer (budgets, allowlists, human approval, default-block rules) decides whether it's actually allowed to clear. See [What are agentic payments?](https://pinkwallet.com/agentic/learn/agentic-payments/) for a longer treatment.

**Is it safe?**
It depends entirely on what controls sit between the agent and the money, not on the agent's own judgment. The [providers table](#providers) above and the [spending-controls crosswalk](https://github.com/Pink-Agentic-Payments/agent-spending-controls-crosswalk) show that documented controls vary widely by provider — some document budgets, allowlists, single-use credentials and human approval together; others document far less. Read a provider's own docs for its specific guarantees before trusting it with real money.

**Which companies offer it?**
At least 17 are tracked in this guide's companion dataset, spanning payment processors (Stripe, Adyen, Checkout.com, Mollie, Square, PayPal, Airwallex, Wise), card networks (Visa, Mastercard), stablecoin/crypto infrastructure (Circle, Coinbase, Tempo), and agent-payment specialists (Skyfire, Payman, Crossmint), plus this guide's publisher, Pink Agentic AI Payments. See [Providers](#providers) above.

**Can an AI agent use a credit card?**
Several providers issue single-use or scoped virtual cards for agent payments rather than handing an agent a reusable card number — e.g. Pink's sandbox issues a single-use test-BIN card locked to one payee and amount, expiring 15 minutes after issue. See [Virtual cards for AI agents](https://pinkwallet.com/agentic/learn/virtual-cards-for-ai-agents/).

**How do you limit an AI agent's spending?**
With the mechanisms in [Controlling agent spending](#controlling-agent-spending) above: a budget over a time window, a per-payment cap, an allowlist or category block, a human-approval threshold, a default-block fallback for anything a rule doesn't cover, and fraud signals checked regardless of amount. The exact field names differ by provider — see the [crosswalk](https://github.com/Pink-Agentic-Payments/agent-spending-controls-crosswalk) and [How to set per-agent spending limits](https://pinkwallet.com/agentic/learn/how-to-set-per-agent-spending-limits/).

## Related reading

- [What are agentic payments?](https://pinkwallet.com/agentic/learn/agentic-payments/) — Pink's definitional explainer
- [Learn library](https://pinkwallet.com/agentic/learn/) — Pink's full set of agentic-payments guides (protocols, spending controls, industry setups)
- [Agentic Payments Readiness Report 2026](https://pinkwallet.com/agentic/research/agentic-payments-readiness-report-2026/) — the full write-up behind the [agentic-payments-readiness](https://github.com/Pink-Agentic-Payments/agentic-payments-readiness) dataset used in this guide's providers table
- [How to Stop an AI Agent From Overspending: 6 Failure Modes and the Controls That Catch Them](https://dev.to/quinn_854b15f517d8632ed4f/how-to-stop-an-ai-agent-from-overspending-6-failure-modes-and-the-controls-that-catch-them-3m88)
- [Should This AI Agent Be Allowed to Pay? Designing the Approval Layer Between Agents and Company Money](https://dev.to/quinn_854b15f517d8632ed4f/should-this-ai-agent-be-allowed-to-pay-designing-the-approval-layer-between-agents-and-company-20k7)
- [x402 vs AP2 vs ACP: Which Agent Payment Protocol Should You Build On? (2026)](https://dev.to/quinn_854b15f517d8632ed4f/x402-vs-ap2-vs-acp-which-agent-payment-protocol-should-you-build-on-2026-fij)
- [How to Give an AI Agent a Spending Limit (and Actually Enforce It Before It Pays)](https://dev.to/quinn_854b15f517d8632ed4f/how-to-give-an-ai-agent-a-spending-limit-and-actually-enforce-it-before-it-pays-17nh)
- [Payment MCP Servers Compared (2026): Which Providers Let AI Agents Move Money](https://dev.to/quinn_854b15f517d8632ed4f/payment-mcp-servers-compared-2026-which-providers-let-ai-agents-move-money-1ahc)
- [Remote MCP Servers With API Keys: What Works in 6 Clients (2026)](https://dev.to/quinn_854b15f517d8632ed4f/remote-mcp-servers-with-api-keys-what-works-in-6-clients-2026-4o2l)

## Related repos in this org

- [agentic-payments-readiness](https://github.com/Pink-Agentic-Payments/agentic-payments-readiness) — the provider-readiness dataset used in this guide
- [agent-spending-controls-crosswalk](https://github.com/Pink-Agentic-Payments/agent-spending-controls-crosswalk) — the spending-controls field-mapping dataset
- [agent-spending-policy](https://github.com/Pink-Agentic-Payments/agent-spending-policy) — the draft vendor-neutral policy schema
- [sandbox-examples](https://github.com/Pink-Agentic-Payments/sandbox-examples) — runnable code against Pink's sandbox
- [awesome-agentic-payments](https://github.com/Pink-Agentic-Payments/awesome-agentic-payments) — the curated link list this guide draws its protocol/provider links from

## Conflict of interest

This guide is published by Pink Agentic AI Payments (by PinkWallet, early access). Pink appears as a row in the providers table above, labeled publisher/self-scored, scored under the same methodology as every other company. Facts about every other company are sourced from that company's own documentation via the [agentic-payments-readiness](https://github.com/Pink-Agentic-Payments/agentic-payments-readiness) dataset — this guide does not independently re-verify them and makes no claim that a competitor lacks a feature beyond what its own docs state (or don't state) as of the dataset's access date.

## Corrections

Found something stale, wrong, or missing a source? Open an issue with the correct URL and quote.

## License

CC BY 4.0 — reuse with attribution. See [LICENSE](LICENSE).
