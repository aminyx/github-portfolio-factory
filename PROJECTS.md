# Project registry

30 planned projects across 6 categories, selected from the research in [docs/RESEARCH.md](docs/RESEARCH.md). Each demonstrates a distinct capability; no two prove the same thing. Ordered by build priority inside each category. Flagship = built first, to the highest bar, candidate for pinning.

Status: `planned` → `building` → `published` → `done` (done = CI green on GitHub + quality gates passed).

## AI / LLM

| # | Project | What it proves | Stack | Status |
|---|---|---|---|---|
| 1 | `citeseek` ⭐ | RAG done seriously: hybrid retrieval (vector+BM25, RRF), reranking, verifiable citations, retrieval eval (Recall@K, MRR) gating CI | Python, FastAPI, Postgres+pgvector, provider-agnostic LLM layer (Anthropic/OpenAI/Ollama/mock) | done |
| 2 | `triagent` ⭐ | Hand-rolled agent loop: tool use, parallel calls, error results, budgets; seeded-incident eval scorecard | Python, provider-agnostic loop, offline incident lab | done |
| 3 | `evalgate` | LLM regression testing as a product: versioned datasets, judge calibration, CI gate action | Python, SQLite run history, judge kappa | done |
| 4 | `mcp-devdb` | MCP protocol literacy + security model: read-only DB introspection server with allowlist and query budgets | TypeScript, MCP SDK, Postgres/SQLite | done |
| 5 | `paperparse` | Structured extraction pipeline: strict schemas, per-field confidence, review queue, gold-set accuracy | Python, FastAPI, Pydantic, React review UI | planned |
| 6 | `docmind` | Full-stack AI product: tenant-scoped RAG chat with streaming citations and isolation writeup | Next.js 16, Vercel AI SDK, pgvector, Drizzle, better-auth | planned |
| 7 | `diffsentry` | AI with measured precision: niche PR reviewer (Dockerfiles) that tracks its own false-positive rate | Go, GitHub API, structured outputs | planned |

## Full-stack / SaaS

| # | Project | What it proves | Stack | Status |
|---|---|---|---|---|
| 8 | `teamboard` ⭐ | Multi-tenant SaaS: organizations, server-side RBAC, invitations, audit log, real-time kanban over SSE, seat billing | Next.js 16, Drizzle, Postgres, better-auth, Tailwind v4 | done |
| 9 | `keymint` | API-key platform: per-key rate limits, usage metering, analytics dashboard | Hono on Cloudflare Workers, Upstash Redis, Next.js dashboard | planned |
| 10 | `sketchsync` | Real-time collaboration: CRDT whiteboard, presence, offline merge | Vite+React, Yjs, WebSocket server, Turso | planned |
| 11 | `statuskit` | Background jobs + time-series: status pages, multi-region checks, incident workflow | Next.js 16, cron workers, Drizzle, Resend | planned |
| 12 | `slotly` | Hard domain logic: scheduling with timezones/DST, calendar sync | Next.js 16, Prisma 7 (second ORM deliberately), Postgres | planned |
| 13 | `crowdpoll` ⭐ | Live fan-out: audience Q&A with anonymous sessions, upvotes, live results over SSE | Next.js 16, Drizzle, better-auth, SSE | done |

## Backend / distributed systems

| # | Project | What it proves | Stack | Status |
|---|---|---|---|---|
| 14 | `threshold` ⭐ | API gateway internals: token-bucket + sliding-window rate limiting, circuit breaker, hedged retries, RateLimit headers (IETF draft), OTel, k6 numbers | Go, stdlib net/http, Redis, OpenTelemetry | done |
| 15 | `ledgerline` ⭐ | Money correctness: double-entry ledger, idempotency keys, payment state machine, chaos provider, reconciliation reports | Go, Postgres, pgx, NATS JetStream outbox | done |
| 16 | `keyforge` ⭐ | Auth provider side: OAuth2/OIDC + PKCE per RFC 9700, passkeys, refresh-token families with reuse detection | Go, Postgres, WebAuthn, RS256 JWKS | done |
| 17 | `sagaworks` | Distributed consistency: outbox + CDC (Debezium→Redpanda), choreography vs orchestration sagas, DLQ with replay CLI | Go + NestJS 11, Postgres, Redpanda | planned |
| 18 | `vaultic` ⭐ | Systems Rust: S3-compatible storage gateway — SigV4 (AWS-vector-verified), multipart, presigned URLs, content-addressed dedup | Rust, Axum, Tokio, SQLx, Postgres | done |
| 19 | `pulsewire` | WebSockets at scale: cross-node NATS fan-out, backpressure eviction, resume-without-gaps, presence, load-tested | Go, NATS JetStream, Prometheus | done |
| 20 | `queuecraft` | Delivery semantics: job queue with visibility timeouts, at-least-once + idempotency, DLQ, dashboard | Rust, Redis Lua / Postgres SKIP LOCKED | planned |

## DevOps / platform

| # | Project | What it proves | Stack | Status |
|---|---|---|---|---|
| 21 | `keyless-ci` | Supply-chain security: OIDC-only pipeline, SHA-pinned actions, cosign + SLSA attestations, tj-actions writeup | GitHub Actions, cosign, SLSA, GHCR | done |
| 22 | `observalab` | Observability depth: OTel Collector → Prometheus 3 + Loki 3.6 + Tempo + Grafana 13, scripted failure scenarios with postmortems | Docker Compose lab, k6 | planned |
| 23 | `gitops-box` | GitOps: one-command k3s/kind bootstrap, Flux, SOPS+Age secrets, PR-driven env promotion | k3d/kind, Flux 2.9, Kustomize | planned |
| 24 | `pr-preview-operator` | Platform engineering: ephemeral env per PR with bot-commented URLs and GC on close | ArgoCD ApplicationSets, k3s, GHCR | planned |

## Mobile

| # | Project | What it proves | Stack | Status |
|---|---|---|---|---|
| 25 | `spendlog` | Offline-first mobile: local DB, sync queue, conflict matrix, optimistic UI | Flutter 3.47, Riverpod 3, Drift | planned |
| 26 | `vitalview` | Native Android depth: Health Connect, Glance widget, WorkManager, baseline profiles with measured startup | Kotlin 2.4, Compose 1.12, Navigation 3 | planned |

## Open-source developer tools

| # | Project | What it proves | Stack | Status |
|---|---|---|---|---|
| 27 | `repo-signal` ⭐ | Adoptable CLI: scores any repo against the 2026 quality checklist (README, CI, tests, license, topics), npx-runnable | TypeScript, Node 24, vitest | done |
| 28 | `actions-lock` | Security tooling: audits workflows for unpinned actions, pins to SHAs, detects repointed tags | Go single binary | done |
| 29 | `readme-arch` | AST tooling: generates mermaid architecture diagrams from real import graphs, README injection | TypeScript, ts-morph | planned |
| 30 | `agent-spend` | Local-first utility: normalizes AI-tool usage logs into per-project spend reports | TypeScript, SQLite | planned |

## Existing assets (kept, improved later)

| Repo | Role |
|---|---|
| `Cybersec` | Flagship education project — already live, substantial |
| `aminyx.top` | Portfolio website — Phase 8 improves it (project sections, case studies) |
| `aminyx` (profile) | Profile README — refreshed in Phase 9 with real featured projects |
| `aminyxlink`, `SOMONVPN` | Private real products — referenced in profile |
| `cyber`, `wykrmaso` | Empty; to be hidden/repurposed in Phase 9 |

## Quality rule

Quality over count. A project ships only when it passes the gates in [ARCHITECTURE.md](ARCHITECTURE.md); if a later idea proves stronger than a planned one, the weaker entry is replaced and this registry updated. Per current research, 6 excellent pinned repos decide the profile — the flagships (⭐) get the deepest investment.
