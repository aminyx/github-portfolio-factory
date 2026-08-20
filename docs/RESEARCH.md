# Research notes — August 2026

Findings from a multi-source survey (official docs, GitHub trending, hiring guides, platform docs) that drive the project list and stack choices. Versions below were verified in August 2026.

## What hiring actually rewards in 2026

- Recruiter first-pass scan is 15–90 seconds: profile identity line, 2–4 pinned repos, and those repos' READMEs. Code quality matters only after that filter passes.
- "Production signals" beat novelty: eval harnesses, tracing, failure handling, cost tracking, load-test numbers, deployment. A well-instrumented ordinary system outranks a novel sloppy one.
- Real-user evidence is the top tier: deployed demos, issues from strangers, merged PRs into real projects.
- An explicit **Limitations / Trade-offs** section in a README now reads as engineering judgment; unbacked performance claims read as inflation.
- AI-slop tells reviewers actively check for: fleets of near-identical CRUD repos, one giant initial commit, uniform naming/README structure across repos, zero tests, nothing deployed, claims without baselines. Public detector tools exist. The countersignal is genuine iteration: fix commits, refactors, issue-driven changes over time.

## AI / LLM engineering

- ~70% of AI candidates show a wrapper chatbot; differentiators are retrieval quality measurement, regression tests in CI, observability, graceful degradation.
- RAG settled pattern: hybrid retrieval (dense HNSW + BM25, RRF fusion) → cross-encoder rerank → 3–10 chunks. When RAG fails, retrieval is the cause ~73% of the time — report Recall@K / MRR, not just generation vibes.
- Anthropic API: structured outputs via `output_config.format` / `messages.parse()`; strict tool use (`strict: true`); adaptive thinking replaces `budget_tokens`; native citations on document blocks return `cited_text` + locations; Batches API at 50% cost.
- pgvector 0.8 is the default vector store up to ~5–10M vectors (hybrid tsvector + vector in one SQL query); Qdrant beyond that. BGE-M3 is the best self-hosted embedder; Ollama v0.32 makes a fully offline RAG stack credible.
- Hand-rolled agent loops (`while stop_reason == "tool_use"`) read better in a portfolio than framework glue; Pydantic AI v2 is the lightweight framework default, LangGraph for durable graphs.
- Eval tooling: RAGAS, DeepEval (pytest-native), promptfoo; tracing via Langfuse (MIT, self-hostable). An eval gate in CI is a rare, checkable signal.
- MCP: ~9.6K servers in the official registry, 41% of surveyed orgs run MCP in production. A tested MCP server with a written security model is a legitimate deliverable.

## Full-stack / T3

- Next.js 16.3 (Cache Components / `"use cache"`, Turbopack default, `middleware.ts` → `proxy.ts`; params/cookies async-only). React 19.2; React Compiler stable, opt-in.
- Drizzle overtook Prisma in downloads (v1.0 RC); Prisma 7 (TS/WASM engine) is the credible alternative — knowing both is a plus.
- Tailwind v4 (CSS-first config) + shadcn/ui is the default UI stack; React 19 removed `forwardRef` patterns; sonner for toasts.
- Auth: better-auth v1.6 is the 2026 default for self-hosted TS apps (organizations, passkeys, RBAC plugins). Auth.js v5 is maintenance mode.
- tRPC v11 via `@trpc/tanstack-react-query`; Server Actions for internal mutations; OpenAPI generation for public surfaces.
- Real-time moved to sync engines (Liveblocks OSS, Electric SQL, Yjs over Durable Objects). A real-time collaborative feature is the most-cited "beyond tutorial" differentiator.
- Impressive SaaS checklist: multi-tenant orgs, RBAC, billing lifecycle with webhooks, one real-time feature, one properly-done AI feature, background jobs, observability, tests + CI.

## Backend / distributed systems

- Go 1.26 (Green Tea GC default, recursive generic constraints). Idiomatic 2026 Go: stdlib `net/http` 1.22+ routing, `log/slog`, sqlc; cargo-culting golang-standards/project-layout is a negative signal.
- Rust services: Axum 0.8 (+ Tokio/Tower/SQLx); note 0.8 path params are `/{id}`, not `/:id`.
- Kafka 4.x is KRaft-only (ZooKeeper mention dates a project); Redpanda for light compose demos; NATS JetStream is the portfolio sweet spot (single binary).
- MinIO OSS archived April 2026 → SeaweedFS / Garage are the self-hosted S3 alternatives; an S3-compatible storage project is unusually timely.
- RPC: ConnectRPC (connect-go) + buf (lint + breaking-change CI) replaced bare grpc-go as the modern default.
- Auth: RFC 9700 (OAuth 2.0 Security BCP); refresh-token rotation with token families + reuse detection; passkeys are table stakes.
- Payments patterns interviewers probe: idempotency keys under unique constraints before calling the processor, append-only double-entry ledger (balance = SUM, never a column), reversal entries not UPDATEs, reconciliation against provider settlement files, transactional outbox, sagas.
- Rate limiting: IETF RateLimit header fields (draft-11, 2026) replaced `X-RateLimit-*`.
- OTLP export is the baseline expectation for any service; k6 load-test numbers + failure-mode docs are the named differentiators.

## DevOps / platform

- Hiring shifted from certs to working repos. Highest-signal pieces: GitOps bootstrap that reproduces from an empty machine, Terraform/OpenTofu module library with secure defaults, a Kubernetes operator, a real CLI tool.
- GitHub Actions security is a first-class topic post tj-actions (23K repos compromised): SHA-pinning (only ~4% do it fully), `permissions: read` default, OIDC federation instead of stored cloud secrets, cosign + SLSA attestations, immutable releases.
- Observability: Prometheus 3.14 (native OTLP), Grafana 13, Loki 3.6. **Promtail is EOL (March 2026)** — ship logs via OTel Collector or Alloy.
- GitOps: ArgoCD 3.5 vs Flux 2.9 — both mature; deep knowledge of one beats shallow both.
- Compose-only DevOps reads junior; k3s/kind for anything claiming orchestration skill.

## Mobile

- Flutter 3.47: Impeller default everywhere; Material/Cupertino decoupling into `material_ui`/`cupertino_ui` packages. Riverpod 3 (Notifier/AsyncNotifier) is the state default; Drift + PowerSync is the consensus offline-first stack.
- Kotlin 2.4 (context parameters stable); AGP 9.x has Kotlin built-in (no separate plugin); Compose BOM 2026.08 = Compose 1.12, compileSdk 37; Navigation 3 stable and the Compose-first choice.
- Recruiters cite: offline-first with sync queue + conflict resolution, real-time features, measured performance (baseline profiles, macrobenchmark), accessibility.
- CI: subosito/flutter-action@v2 with cache; emulator tests via reactivecircus/android-emulator-runner (KVM on ubuntu runners); pin runner images.

## Deployment matrix (free tiers, verified August 2026)

| Platform | Free tier reality | Fits |
|---|---|---|
| Vercel Hobby | Generous; non-commercial clause; no WebSockets; no Docker | Next.js SSR demos |
| Cloudflare Workers | 100k req/day, 10ms CPU; D1/KV/R2/Durable Objects free; Workers AI 10k neurons/day; Containers are paid-only | Edge APIs, WebSockets via DO, static |
| GitHub Pages | Static only | Docs, static demos |
| Render | Only free Docker host; 15-min spin-down, ~30–60s cold start; free Postgres expires after 30 days (avoid) | Dockerized API demos with cold-start note |
| Fly.io | No free tier for new accounts | — |
| Railway | $5 one-time trial only | — |
| Neon | Best free Postgres: 100 projects, per-project compute budget, scale-to-zero | Many small demo DBs |
| Turso | 100 SQLite DBs, always-responsive | Per-demo SQLite |
| Supabase | 2 projects; pauses after 7 days idle (needs keep-alive ping) | Auth/realtime demos |
| Upstash | 500k Redis commands/mo | Rate limiting, queues |
| Netlify | 300-credit hard cap | Light static/SSR |
| Deno Deploy (EA) | 1M req/mo, WebSockets | Edge full-stack |

Recommended demo stack: Vercel or Cloudflare Workers + Neon/Turso + Upstash; Render (with cold-start note) for Docker; GitHub Pages for static.
