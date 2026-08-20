# Portfolio benchmark

Assessment of the current aminyx profile against what strong 2026 GitHub profiles look like (see [RESEARCH.md](RESEARCH.md) for sources).

## Current level

**Foundation is real but thin on public evidence.**

What exists (August 2026):

| Asset | State |
|---|---|
| Profile README | Strong: clear identity, honest project descriptions, ethics section, contact routes |
| Cybersec (public) | Genuine, substantial: 270-day bilingual security course, live site, real scope |
| aminyx.top (public) | Live personal site on GitHub Pages |
| aminyxlink, SOMONVPN (private) | Real engineering, but invisible to a reviewer |
| cyber, wykrmaso (public) | Empty junk repos; **wykrmaso is the only pinned repo** |

Score against the recruiter 30-second scan: the identity line passes, but the pinned area fails (one empty repo pinned), and there are no public repos demonstrating backend, AI, DevOps, mobile, or open-source engineering.

## Target level

A profile where:

1. Pinned area shows 6 repos, each with CI badge, tests, architecture diagram, and a runnable path — at least 2 with live demos.
2. Public repos cover the full claimed stack (Go, Rust, TypeScript, Python, Kotlin, Dart) with one distinct capability per repo.
3. At least 3 repos are tools other developers can adopt (CLI, library, MCP server) — the category that accumulates organic evidence.
4. Every repo passes the anti-slop checks: incremental honest commit history, varied structure, tests everywhere, limitations sections, no dead links.

## Main gaps

1. **P0 — pinned area**: one empty repo pinned; nothing else pinned.
2. **P1 — no public backend/distributed-systems code** despite backend being the profile's stated specialty.
3. **P1 — no public AI/LLM engineering** — the highest-demand 2026 category.
4. **P2 — no open-source tools** — the category that earns organic stars/issues.
5. **P2 — no DevOps/platform evidence** beyond claims in the README.
6. **P2 — no public mobile code** despite Android being claimed.
7. **P3 — empty repos (cyber, wykrmaso)** pollute the public listing.

## Recommended improvements (ordered)

1. Build and pin flagship projects, one per category, to the full quality bar (in progress — see [../PROJECTS.md](../PROJECTS.md)).
2. Ship at least one adoptable developer tool early (npx-runnable CLI).
3. Deploy at least two live demos on free tiers (Vercel / Cloudflare / Render) and link them from README + repo metadata.
4. Hide or repurpose the empty repos; re-pin.
5. Keep iterating on shipped repos over the following weeks (issues, changelogs, releases) — sustained activity is the strongest anti-slop countersignal.

## Honesty constraints

All repos are created when the work is actually done — no backdated commits, no synthetic history, no fake metrics. The portfolio's credibility rests on the work being real, runnable, and continuously iterated.
