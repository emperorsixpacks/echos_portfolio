# Echo Application — Portfolio Submission

**Applicant:** Andrew David ([github.com/emperorsixpacks](https://github.com/emperorsixpacks))
**Applying for:** Back-End Developer, Echoes Fans (Superteam Earn)

This README accompanies my application for the Back-End Developer role at Echoes Fans. It highlights recent shipped work across Rust/TypeScript, backend infrastructure, and the Solana/multi-chain ecosystem, in line with what the role asks for.

---

## Why this portfolio fits

Echoes needs a backend engineer who can own API routes, Supabase pipelines, permanent storage integration (Arweave), presigned-URL upload infra, on-chain fee mechanics, and reward-distribution logic. The four projects below map directly onto that scope: encrypted marketplace backends, on-chain escrow and settlement, wallet/agent infrastructure, and node/infra tooling.

---

## Featured Projects

### 1. [BlindMarket](https://github.com/jemIIahh/BlindMarket)
**Privacy-preserving agent-to-agent task marketplace — 0G Mainnet + Sui**

- Express/TypeScript backend with on-chain escrow settlement, a verifier-signed bridge (`a2aSettlement`), and an event indexer that maps off-chain task hashes to on-chain task IDs via Redis.
- Client-side AES-256-GCM + ECIES encryption so the platform never sees plaintext task briefs or evidence; TEE-attested verification path wired in for zero-trust review.
- UUPS-upgradeable Solidity contracts (115 passing unit tests) plus a parallel Move-based deployment on Sui, demonstrating cross-chain settlement logic (EVM vs. object-model design).
- Directly relevant to Echoes' need for on-chain fee mechanics, escrow, and reward/prize-pool distribution logic.

### 2. [Promus](https://github.com/JemIIahh/promus)
**Sovereign AI agent runtime — Arbitrum, ERC-7857 iNFT identity, encrypted IPFS memory**

- CLI-hosted agent whose identity, wallet, and memory live on-chain/off-chain rather than in a server process — wallet sealed to an ERC-7857 iNFT, memory encrypted and persisted to IPFS with content-hash anchoring each turn.
- Agent-to-agent messaging (ECIES-encrypted inbox) and a job-escrow market contract (95% provider / 5% fee split) — same reward-distribution shape Echoes needs for its competition/prize-pool logic.
- Shows comfort with decentralized storage (IPFS) and on-chain identity, adjacent to Echoes' Arweave-based permanent storage flow.

### 3. [CipherProof](https://github.com/JemIIahh/cipherproof)
**Confidential wallet on the Zama Protocol (FHEVM) — encrypted on-chain balances, ERC-7984**

- A USDC-style token (`cUSDC`) holds every balance on-chain as a fully-homomorphically-encrypted `euint64` — the public ledger never sees the amount, and holders reveal their own balance off-chain via a gasless EIP-712 "viewer permit."
- Confidential transfers move a client-encrypted amount end-to-end (ZK input proof + FHEVM coprocessor), so the ledger shows *who* transacted but never *how much*.
- Adds stealth addresses (ERC-5564) for receiver unlinkability plus an EIP-7702 gasless relayer for the spend hop — the sender's main wallet never appears on-chain.
- Monorepo (Hardhat contracts + React/Vite/ethers v6 frontend), built for the Zama Developer Program (Mainnet Season 3, Builder Track). Directly demonstrates encrypted-balance design, gasless/permit-based UX, and ACL-gated decryption — the same category of problem as securing user funds and confidential reward flows.
- *(Note: this repo is currently private — happy to grant access or walk through it live.)*

### 4. [Starknode-Kit](https://github.com/thebuidl-grid/starknode-kit)
**Go-based CLI for spinning up Ethereum, Starknet, and Stellar nodes**

- Single-command L1 + L2 node bootstrapping (execution/consensus client pairs, Starknet clients like Juno, plus a full Stellar Core validator toolchain).
- Demonstrates infrastructure/DevOps depth — config management, process orchestration, monitoring — the same muscle needed for Echoes' Cloudflare R2 upload infra and pipeline reliability.

---

## Relevant Background

- Senior Backend Engineer, 5+ years, fintech/payments infrastructure and Web3.
- Core stack: TypeScript/Node.js, Go, Python (FastAPI, Django, Celery); Redis, Kafka, PostgreSQL, Docker/Kubernetes.
- Blockchain experience spans Solana, Starknet, Arbitrum, Base, Stellar Soroban, Sui, and 0G — including HD wallet derivation (BIP44/SLIP-0010, EVM + SVM), custom blockchain indexers on Redis Streams, and gasless sweep flows (EIP-2612 permits).
- Founder/lead engineer at Looprail, a production stablecoin remittance platform currently processing real customer funds — direct experience with the reliability, observability, and reconciliation concerns that come with holding user money on-chain.
