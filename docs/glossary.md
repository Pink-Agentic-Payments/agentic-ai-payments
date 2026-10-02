# Glossary

Short definitions of terms used throughout this guide. Each links to a longer explainer on Pink Agentic AI Payments' learn library (all checked HTTP 200 on 2026-10-02).

**Agentic payments** — A payment flow where an AI agent, not a human, decides what to buy and when, while a separate policy layer decides whether the payment is allowed to clear. See [agentic-payments](https://pinkwallet.com/agentic/learn/agentic-payments/).

**x402** — An open protocol that uses the HTTP `402 Payment Required` status code to let a server ask for payment inline, with an agent's wallet signing and retrying the request onchain. See [x402](https://pinkwallet.com/agentic/learn/x402/).

**AP2 (Agent Payments Protocol)** — A Google-originated protocol using cryptographically signed "Mandates" as tamper-proof proof of a user's purchase instructions, now stewarded by the FIDO Alliance. See [ap2](https://pinkwallet.com/agentic/learn/ap2/).

**ACP (Agentic Commerce Protocol)** — An open standard, co-developed by Stripe and OpenAI, for connecting buyers, their AI agents, and merchants to complete in-chat purchases. See [agentic-commerce-protocol](https://pinkwallet.com/agentic/learn/agentic-commerce-protocol/).

**Visa Trusted Agent Protocol (TAP)** — A cryptographic message-signing standard (RFC 9421) that lets a merchant verify an AI agent's identity before checkout; it authenticates the agent but does not itself move money. See [visa-trusted-agent-protocol](https://pinkwallet.com/agentic/learn/visa-trusted-agent-protocol/).

**Mastercard Agent Pay** — A Mastercard program for agent-initiated purchases, built on the tokenization already used for mobile contactless and card-on-file payments. See [mastercard-agent-pay](https://pinkwallet.com/agentic/learn/mastercard-agent-pay/).

**MCP (Model Context Protocol)** — An open protocol that lets an AI model or agent connect to external tools and data sources over a standard interface; several payment providers expose an MCP server so an agent can check balances, create orders, or request payments. See [mcp-payments](https://pinkwallet.com/agentic/learn/mcp-payments/).

**Payment MCP server** — An MCP server whose tools create or move payment objects (orders, refunds, payouts, payment links), as opposed to one that only reads data. See [how-ai-agents-pay-through-mcp](https://pinkwallet.com/agentic/learn/how-ai-agents-pay-through-mcp/).

**Spending controls** — The set of mechanisms (budgets, per-payment caps, allowlists, category blocks, human approval, default-block) that limit what an agent is allowed to pay for. See [ai-agent-spending-controls](https://pinkwallet.com/agentic/learn/ai-agent-spending-controls/).

**Per-agent spending limit** — A cap, typically over a time window (day/week/month) or per transaction, applied to one specific agent rather than an entire account. See [how-to-set-per-agent-spending-limits](https://pinkwallet.com/agentic/learn/how-to-set-per-agent-spending-limits/).

**Agent wallet** — A wallet (custodial or self-custodied, fiat or stablecoin) that an AI agent holds and uses to initiate payments, usually scoped by a spending policy. See [ai-agent-wallet](https://pinkwallet.com/agentic/learn/ai-agent-wallet/).

**Virtual card for AI agents** — A single-use or narrowly scoped card number issued for one agent payment, rather than a reusable card number handed to the agent. See [virtual-cards-for-ai-agents](https://pinkwallet.com/agentic/learn/virtual-cards-for-ai-agents/).

**KYA (Know Your Agent)** — Identity verification for an AI agent itself, analogous to KYC for a human or business, used so a seller can confirm which agent (and on whose behalf) is making a request. See [know-your-agent](https://pinkwallet.com/agentic/learn/know-your-agent/).

**Payment MCP servers compared** — A cross-provider comparison of which official MCP servers can actually move money versus only read data. See [payment-mcp-servers-compared](https://pinkwallet.com/agentic/learn/payment-mcp-servers-compared/).

**x402 vs AP2 vs ACP** — A comparison of the three leading software-layer agent payment protocols and which layer of the problem each solves. See [x402-vs-ap2-vs-acp](https://pinkwallet.com/agentic/learn/x402-vs-ap2-vs-acp/).
