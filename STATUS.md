# Status

Current phase: **CI-free wave** (sable shipped with a live demo; keelstore and driftpad in progress)

Last updated: 2026-08-20

## Phase state

| Phase | State |
|---|---|
| 1 — Research | done |
| 2 — Final project list | done |
| 3 — Foundation | done |
| 4 — Flagship wave | done: threshold, citeseek, ledgerline, repo-signal, crowdpoll, mcp-devdb |
| 5 — Verification & deployment | CI green on all published repos; live demos deferred (no platform tokens in env — see deployment notes in each README) |
| 6 — Second wave | in progress: triagent, keyforge, actions-lock, keyless-ci done; evalgate done |
| 7 — Mobile / DevOps / security | pending |
| 8 — Portfolio website | pending |
| 9 — GitHub cleanup | partial: junk repos hidden, profile README refreshed; pinning requires manual UI step |
| 10 — Final audit | pending |

Per-project state lives in [PROJECTS.md](PROJECTS.md).

## CI note

The account's GitHub Actions minutes are exhausted (private repositories
consume them; public repositories do not). Projects from the CI-free wave
onwards ship **no workflow at all**: the gate is a `make check` /
`npm run check` target plus a committed git pre-commit hook, and live demos
are served by GitHub Pages directly from a committed `docs/` folder, which
needs no workflow. Existing repositories keep their green CI untouched.
