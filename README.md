# Onchain Community Currency Monorepo

```mermaid
flowchart LR
  A[Community Participants];
  B[(CANA Token)];
  Chain[Blockchain];
  C[Public Auditing];
  D[Bank Reserves BRL];
  E[Wallets];
  A --> B;
  B --> Chain;
  B --> C;
  B --> D;
  E -. "hold/use" .-> B;
```

(A) Community participants mint/redeem (B) Caiana tokens backed by BRL reserves held at (D) the bank. Activity is recorded on the blockchain and can be inspected (C) for transparency. Users hold and use tokens in (E) wallets.

```mermaid
flowchart LR
  A[Wallet A Sender];
  B[Wallet B Recipient];
  C[WhatsApp and CANA];
  Chain[Blockchain];
  A --> Chain;
  Chain --> B;
  C --> Chain;
```

- A: Sender wallet
- B: Recipient wallet
- C: WhatsApp interface and on-chain token actions via the backend
- Blockchain: records token transfers between wallets

This repository contains the code and configuration for Caiana — a community currency system built on Celo — and supporting tooling to launch, operate, and document a bank‑backed, on‑chain local currency.

## What’s Inside

- `frontend/` — Web UI for interacting with the system (if present in your checkout).
- `backend/` — Lightweight backend (Node/Express) with endpoints for auth, admin config, and on-chain utilities.
- `stablecoin/` — Caiana (CANA) stablecoin contracts and tooling (based on Circle’s stablecoin-evm framework). Includes Hardhat/Foundry config, deployment scripts, and docs.
- `communitycurrencylauncher/` — A launcher app to create and manage community currencies, including contracts, backend helpers, and a static frontend.

## Public Links

- Caiana public statement and on‑chain activity (Blockscout):
  https://celo.blockscout.com/address/0x15ffACd88539aFa123AD4707e28f6Bc3A7DBBad7?tab=txs
- Community Currency Launcher (live):
  https://brazil-community-currency.vercel.app/

## Transparency

The amount of Caiana (CANA) minted corresponds to BRL reserves and is evidenced publicly via the Blockscout link above. See `stablecoin/README.md` for details.

## Development Overview

- Prereqs typically include Node.js (LTS), pnpm/yarn/npm, and for contracts Hardhat/Foundry. See subproject READMEs for exact versions and steps.
- Common workflows:
  - Frontend: install, build, and run dev server.
  - Backend: provide `.env` (see examples), then run with Node.
  - Contracts: build/test with Foundry or Hardhat; deploy via provided scripts.

## Security and Secrets

- Do not commit private keys or secrets. Environment files are ignored by `.gitignore` and examples are provided as `.env.example` where applicable.
- If rotating or revoking credentials, update deployment configs and relevant services.

## Repository Structure Notes

- Each subfolder contains its own README and scripts where applicable.
- This repo tracks both application code (UI/API) and on‑chain components for a cohesive, auditable system.
