<div align="center">

# Solvela

**Solana-native AI agent payment infrastructure.**

AI agents pay for LLM API calls with USDC-SPL on Solana via the [x402 protocol](https://www.x402.org/),
settled through an on-chain escrow so the gateway never custodies funds.
No API keys, no accounts — just wallets.

[![Website](https://img.shields.io/badge/website-solvela.ai-F97316?style=flat)](https://solvela.ai)
[![Docs](https://img.shields.io/badge/docs-docs.solvela.ai-F97316?style=flat)](https://docs.solvela.ai)
[![Twitter](https://img.shields.io/badge/twitter-@solvela__ai-F97316?style=flat&logo=x)](https://twitter.com/solvela_ai)
[![License](https://img.shields.io/badge/license-MIT-F97316?style=flat)](https://github.com/solvela-ai/solvela/blob/main/LICENSE)
[![Solana](https://img.shields.io/badge/solana-mainnet-F97316?style=flat&logo=solana&logoColor=white)](https://solscan.io/account/9neDHouXgEgHZDde5SpmqqEZ9Uv35hFcjtFEPxomtHLU)

</div>

---

## What's different about Solvela

Every other x402 LLM gateway requires the agent to send USDC directly to the operator's recipient address and trust them to charge only what was actually consumed. Solvela ships an [Anchor escrow program](https://github.com/solvela-ai/solvela/tree/main/programs/escrow) deployed at [`9neDH…HLU`](https://solscan.io/account/9neDHouXgEgHZDde5SpmqqEZ9Uv35hFcjtFEPxomtHLU) that changes that:

- **Cap, don't pay.** The agent calls `deposit(max_amount, service_id, expiry_slot)` and USDC locks in a per-request PDA vault. The agent commits a maximum — not a final price.
- **Settle to actual cost.** After the gateway delivers the response, it calls `claim(actual_cost)`. The contract transfers `actual_cost` to the provider and **auto-refunds `max_amount − actual_cost`** to the agent. The gateway has no way to claim more than was consumed.
- **Unilateral refund.** If the gateway never responds (down, censoring, etc.), the agent calls `refund()` after `expiry_slot` and recovers the full deposit. No gateway cooperation required.

Trustless settlement is the default. The classic "exact" x402 scheme is also accepted for clients who want the cheaper round-trip.

## Quick start

```bash
cargo install solvela-cli
solvela --api-url https://api.solvela.ai models
```

## SDKs

Each SDK targets its language's native package manager. Source lives in the monorepo under `sdks/`.

| Language | Install | Source |
|---|---|---|
| Rust | `cargo install solvela-cli` &nbsp;[![crates.io](https://img.shields.io/crates/v/solvela-cli?label=solvela-cli&color=F97316)](https://crates.io/crates/solvela-cli) | [`solvela/sdks/rust`](https://github.com/solvela-ai/solvela/tree/main/sdks/rust) |
| TypeScript | `npm install @solvela/sdk` &nbsp;[![npm](https://img.shields.io/npm/v/@solvela/sdk?label=%40solvela%2Fsdk&color=F97316)](https://www.npmjs.com/package/@solvela/sdk) | [`solvela/sdks/typescript`](https://github.com/solvela-ai/solvela/tree/main/sdks/typescript) |
| Python | `pip install solvela-sdk` &nbsp;[![PyPI](https://img.shields.io/pypi/v/solvela-sdk?label=solvela-sdk&color=F97316)](https://pypi.org/project/solvela-sdk/) | [`solvela/sdks/python`](https://github.com/solvela-ai/solvela/tree/main/sdks/python) |
| Go | `go get github.com/solvela-ai/solvela/sdks/go` | [`solvela/sdks/go`](https://github.com/solvela-ai/solvela/tree/main/sdks/go) |
| MCP | See source — not yet published as a standalone package | [`solvela/sdks/mcp`](https://github.com/solvela-ai/solvela/tree/main/sdks/mcp) |

## Crates published

[![solvela-protocol](https://img.shields.io/crates/v/solvela-protocol?label=solvela-protocol&color=F97316)](https://crates.io/crates/solvela-protocol)
[![solvela-x402](https://img.shields.io/crates/v/solvela-x402?label=solvela-x402&color=F97316)](https://crates.io/crates/solvela-x402)
[![solvela-router](https://img.shields.io/crates/v/solvela-router?label=solvela-router&color=F97316)](https://crates.io/crates/solvela-router)
[![solvela-cli](https://img.shields.io/crates/v/solvela-cli?label=solvela-cli&color=F97316)](https://crates.io/crates/solvela-cli)

## Live services

| Service | URL |
|---|---|
| Gateway API | [`api.solvela.ai`](https://api.solvela.ai/health) |
| Docs | [`docs.solvela.ai`](https://docs.solvela.ai) |
| Dashboard | [`app.solvela.ai`](https://app.solvela.ai) |
| Landing | [`solvela.ai`](https://solvela.ai) |

## Status

Production. Escrow program deployed to Solana mainnet at [`9neDH…HLU`](https://solscan.io/account/9neDHouXgEgHZDde5SpmqqEZ9Uv35hFcjtFEPxomtHLU). See the [main repo](https://github.com/solvela-ai/solvela) for shipping status, architecture, and the changelog.

## Contact

- **Security**: `security@solvela.ai` — see [SECURITY.md](https://github.com/solvela-ai/solvela/blob/main/SECURITY.md)
- **Partnerships / commercial**: `partnerships@solvela.ai`
- **Twitter / X**: [@solvela_ai](https://twitter.com/solvela_ai)
