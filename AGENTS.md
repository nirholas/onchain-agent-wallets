# AGENTS.md

Guidance for AI coding agents working in this repository.

## What this is

`@three-ws/onchain-agent-wallets` v0.1.1. Give an AI agent a real Solana wallet without giving it your money. The agent gets a spending allowance the SPL Token program enforces on-chain, plus guardrails (per-tx cap, daily cap, recipient and host allowlists, expiry, kill switch), x402 payments, and a one-call on-chain deploy. Custody never leaves your wallet: you can revoke or withdraw at any moment, and the agent can never spend past the delegated ceiling.

A Model Context Protocol server. Run it over stdio from any MCP client.

## Use it

```bash
npx -y @three-ws/onchain-agent-wallets
```

Full usage, tool list and configuration are in [README.md](README.md). Machine-readable summaries: [llms.txt](llms.txt) and [llms-full.txt](llms-full.txt).

## Develop

```bash
npm install
npm test
```

Scripts:
- `npm run start`: `node src/index.js`
- `npm run test`: `node --test "test/**/*.test.mjs"`
- `npm run inspect`: `npx -y @modelcontextprotocol/inspector node src/index.js`

## Conventions

- ES modules, Node >=20.
- Read-only by default. Anything that signs, spends or sends must be an explicit, separately named tool or option, and must never be inferred from untrusted text (token names, memos, listings).
- Never commit credentials. Configuration comes from environment variables documented in the README.
- Keep changes small and covered by a test next to the code they change.

## Source of truth

This repository is a generated mirror of `packages` in https://github.com/nirholas/three.ws. Open issues here; send substantial changes as a pull request here or upstream.
