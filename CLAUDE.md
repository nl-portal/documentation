# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

This is the GitBook-based documentation site for NL Portal. It contains only Markdown files — there is no build system, compiled code, or test suite. The documentation is primarily written in Dutch.

## Structure

- **`SUMMARY.md`** — The GitBook table of contents. Every `.md` file (except `SUMMARY.md` itself and files under `release-notes/template/`) **must** be referenced here, or GitBook will not render it.
- **`fundamentals/`** — Architecture, authentication, integrations, design patterns
- **`configuratie/`** — Setup guides, deployment, theming, token exchange
- **`features/`** — Feature-specific documentation
- **`release-notes/`** — Per-version release notes, organized by major version (e.g. `3.x.x/3.0.0/`)
- **`support-en-resources/`** — Best practices, community, repositories
- **`product-management/`** — Governance and roadmap
- **`contributing/`** — Contributing guidelines

## Key Constraint: SUMMARY.md Must Stay in Sync

Whenever you add a new `.md` file, you **must** add it to `SUMMARY.md`. To verify nothing is missing, run:

```bash
./check_summary.sh
```

This script reports any `.md` file not referenced in `SUMMARY.md` and prints the correct link syntax to paste in.

## Release Notes Convention

New release notes go in `release-notes/<major>.x.x/<version>/release-notes.md`. Use `release-notes/template/release-notes.md` as the template. Sections:

- **Nieuwe Functionaliteit** / **Functionaliteiten**
- **Bugfixes**
- **Breaking changes**
- **Verwijderingen en afschrijvingen** (removals/deprecations)
- **Bekende problemen** (known issues)

After creating a release notes file, add it to `SUMMARY.md` and to the overview page at `release-notes/release-notes.md`.
