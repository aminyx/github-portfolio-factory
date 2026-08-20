# Engineering conventions

Rules that apply to every repository in the portfolio. Individual projects may extend these, never silently violate them.

## Repository layout

- One project = one repository, named in kebab-case after what it does (`ws-hub`, not `project7`).
- `main` is the default branch and is always green.
- Required files: `README.md`, `LICENSE`, `.gitignore`, `.env.example` (if config exists), `CHANGELOG.md` (once there is a release).
- No build artifacts, `node_modules`, editor junk, or secrets in history. `.gitignore` is written before the first commit.

## Commits

Conventional commits: `feat:`, `fix:`, `refactor:`, `docs:`, `test:`, `chore:`, `ci:`.
Each commit is a coherent unit of real work. No bulk "initial commit" dumps of finished apps: scaffolding, features, tests, and docs land as separate meaningful commits.

## Quality gates (per project, before it is marked done)

1. Formatter and linter pass with zero errors.
2. Typecheck passes (TS `tsc --noEmit`, Python `mypy`/`pyright` where configured, Go `go vet`).
3. Tests pass locally and in CI. Every project has tests for its core logic, not just a smoke test.
4. Build succeeds (`next build`, `go build ./...`, `docker build` where applicable).
5. README complete per template, with real screenshots for UI projects.
6. CI workflow green on GitHub before status flips to done.

## Stack defaults

| Concern | Default | Use something else when |
|---|---|---|
| Web frontend | Next.js (App Router) + TypeScript + Tailwind | Vite + React for SPAs, plain HTML for static |
| API in TS | tRPC (internal), REST + OpenAPI (public) | GraphQL only if the project is about GraphQL |
| ORM | Drizzle | Prisma when the project showcases Prisma |
| Go services | stdlib `net/http` + chi where routing grows | Framework only with a reason |
| Python services | FastAPI + Pydantic v2, managed by uv | — |
| Databases | Postgres first; SQLite for zero-infra tools; Redis for cache/queues; Mongo where document model fits | Vector: pgvector / sqlite-vec |
| Auth | Session or JWT hand-rolled in auth-focused projects; better-auth in product-focused ones | — |
| Containers | Multi-stage Dockerfile, non-root user, healthcheck | — |
| CI | GitHub Actions from `templates/workflows/` | — |

## Security baseline

- Secrets only via environment variables; `.env` is gitignored, `.env.example` documents every variable.
- Input validation at every boundary (zod / Pydantic / go-playground/validator).
- Password hashing: argon2id. Tokens: short-lived access + rotating refresh.
- Rate limiting on public write endpoints.
- CORS explicit, never `*` with credentials.
- Dependency audit in CI (`npm audit` / `govulncheck` / `pip-audit`) — advisory, pinned versions.

## AI project baseline

Every AI project must show engineering, not just an API call:

- Provider-agnostic LLM layer: Anthropic / OpenAI / Ollama / deterministic mock, selected by env.
- The mock provider makes the full test suite and CI run offline with zero keys.
- Streaming, retries with backoff, timeouts, token usage tracking as standard.
- Where retrieval or generation quality matters: a small eval dataset and a script that reports metrics.

## Definition of done

A project is done when a stranger can clone it, follow the README, run it, run the tests, and see CI green on GitHub — with no verbal explanation needed.
