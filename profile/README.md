<div align="center">

# Solvela

**Solana-native AI agent payment infrastructure.**

AI agents pay for LLM API calls with USDC-SPL on Solana via the [x402 protocol](https://www.x402.org/).
No API keys, no accounts — just wallets.

[![Website](https://img.shields.io/badge/website-solvela.ai-F97316?style=flat)](https://solvela.ai)
[![Docs](https://img.shields.io/badge/docs-docs.solvela.ai-F97316?style=flat)](https://docs.solvela.ai)
[![Twitter](https://img.shields.io/badge/twitter-@solvela__ai-F97316?style=flat&logo=x)](https://twitter.com/solvela_ai)
[![License](https://img.shields.io/badge/license-MIT-F97316?style=flat)](https://github.com/solvela-ai/solvela/blob/main/LICENSE)
[![Solana](https://img.shields.io/badge/solana-mainnet-F97316?style=flat&logo=solana&logoColor=white)](https://solscan.io/account/9neDHouXgEgHZDde5SpmqqEZ9Uv35hFcjtFEPxomtHLU)

</div>

---

## Install

```bash
cargo install solvela-cli
solvela --api-url https://api.solvela.ai models
```

## Repositories

| Repo | What it is |
|---|---|
| [**solvela**](https://github.com/solvela-ai/solvela) | Gateway, smart router, escrow program, dashboard, docs site |
| [**solvela-client**](https://github.com/solvela-ai/solvela-client) | Rust agent-side SDK + CLI + sidecar proxy |
| [**solvela-ts**](https://github.com/solvela-ai/solvela-ts) | TypeScript SDK |
| [**solvela-python**](https://github.com/solvela-ai/solvela-python) | Python SDK |
| [**solvela-go**](https://github.com/solvela-ai/solvela-go) | Go SDK |

## Live services

| Service | URL |
|---|---|
| Gateway | [`api.solvela.ai`](https://api.solvela.ai/health) |
| Docs | [`docs.solvela.ai`](https://docs.solvela.ai) |
| Dashboard | [`app.solvela.ai`](https://app.solvela.ai) |
| Landing | [`solvela.ai`](https://solvela.ai) |

## Crates published

[`solvela-protocol`](https://crates.io/crates/solvela-protocol) · [`solvela-x402`](https://crates.io/crates/solvela-x402) · [`solvela-router`](https://crates.io/crates/solvela-router) · [`solvela-cli`](https://crates.io/crates/solvela-cli)

## Status

Production. Escrow program deployed to Solana mainnet at [`9neDH…HLU`](https://solscan.io/account/9neDHouXgEgHZDde5SpmqqEZ9Uv35hFcjtFEPxomtHLU). See the [main repo](https://github.com/solvela-ai/solvela) for current shipping status, architecture, and the changelog.

## Contact

- **Security**: `security@solvela.ai` (see [SECURITY.md](https://github.com/solvela-ai/solvela/blob/main/SECURITY.md))
- **General**: `hello@solvela.ai`
- **Twitter / X**: [@solvela_ai](https://twitter.com/solvela_ai)
