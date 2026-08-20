# github-portfolio-factory

Central planning and tooling repository for the [aminyx](https://github.com/aminyx) project portfolio.

This repo holds the roadmap, project registry, engineering conventions, and shared templates used to build and maintain every repository in the portfolio. It is intentionally public: the process is part of the portfolio.

## Contents

| File | Purpose |
|---|---|
| [PROJECTS.md](PROJECTS.md) | Registry of all portfolio projects: category, stack, status, links |
| [ROADMAP.md](ROADMAP.md) | Build phases and what ships in each |
| [STATUS.md](STATUS.md) | Current phase and per-project state |
| [ARCHITECTURE.md](ARCHITECTURE.md) | Cross-project engineering conventions |
| [docs/RESEARCH.md](docs/RESEARCH.md) | Research notes: 2026 landscape, stack decisions, deployment matrix |
| [docs/PORTFOLIO-BENCHMARK.md](docs/PORTFOLIO-BENCHMARK.md) | Benchmark against strong GitHub profiles; gaps and targets |
| [templates/](templates/) | Shared README skeleton, CI workflows, gitignore sets |

## Principles

1. **Every project demonstrates a distinct capability.** No two repos prove the same thing.
2. **Runnable beats described.** Each repo must start locally with the commands in its README, or it does not ship.
3. **CI is the gate.** Lint, typecheck, tests, and build must pass in GitHub Actions before a project is listed as done.
4. **Docs answer in 30 seconds:** what it is, why it exists, how it works, how to run it.
5. **No fake signals.** No inflated commit history, no placeholder screenshots, no dead demo links.

## License

MIT
