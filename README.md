# PeerHire

A decentralised freelance marketplace prototype: a React front end, a Hono API
and a Foundry contract suite for escrow and reputation on Base.

PeerHire explores how blockchain escrow and AI assistance could make freelance
work more trustworthy. Clients and freelancers sign in with JWT auth, connect a
Coinbase wallet on Base and work through a full marketplace interface covering
jobs, proposals, contracts, payments and messaging. The Solidity suite models
escrow, milestones, disputes, reputation and platform governance.

- **Marketplace front end.** Vite, React, TypeScript and shadcn/ui pages for
  jobs, proposals, contracts, payments, dashboards and messaging.
- **Wallet connection.** Coinbase Wallet SDK signs messages against Base RPC.
- **Contract suite.** Foundry project with escrow, job registry, milestone,
  dispute, reputation, governance and verification contracts plus Forge tests.
- **Auth API.** Hono and MongoDB backend with bcrypt passwords, JWT sessions,
  role checks (client and freelancer) and a demo mode.
- **AI assistant (prototype).** An in-app chat widget that simulates Groq
  replies; the screen-recording page is a stub for work verification.

## Run it

You need Bun, Foundry and a MongoDB instance. Clone with submodules so the
Foundry libraries come down too:

```bash
git clone --recurse-submodules https://github.com/jayptl-me/hackhazards25_peer_hire.git
cd hackhazards25_peer_hire
```

### Backend (port 3000)

```bash
cd backend
bun install
cp .env.example .env
# set MONGODB_URI and JWT_SECRET, and point FRONTEND_URL at
# http://localhost:5173 so the Vite dev server passes CORS
bun run dev
```

### Frontend

```bash
cd frontend
bun install
cp .env.example .env   # VITE_API_URL already points at http://localhost:3000
bun run dev
```

### Smart contracts

```bash
cd smart_contracts
forge build
forge test
```

Deployment notes live in `smart_contracts/DEPLOYMENT_GUIDE.md`; the backend API
routes are documented in `backend/README.md`.

## License

Licensed under the Apache License, Version 2.0. See `LICENSE` and `NOTICE`.
