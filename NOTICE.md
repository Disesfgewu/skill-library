# Third-Party Notices

The 8 skills under `skills/` are adapted from [`anthropics/skills`](https://github.com/anthropics/skills)
(`skills/<name>/SKILL.md` in that repo), each individually licensed there under the
**Apache License 2.0** (see each skill folder's `LICENSE.txt` in the upstream repo).
This repository is licensed overall under GPLv3 ([`LICENSE`](LICENSE)); the Apache-2.0
provenance of these 8 files is preserved here per Apache-2.0 §4 (GPLv3 is one-way
compatible with including Apache-2.0 licensed work).

Adapted skills:

- `algorithmic-art`, `brand-guidelines`, `canvas-design`, `frontend-design`,
  `internal-comms`, `mcp-builder`, `theme-factory`, `webapp-testing`

## What "adapted" means

Anthropic's originals are multi-file skill folders (`SKILL.md` + `scripts/`, `reference/`,
`examples/`, `themes/`, etc.). This library's format — matching `disesfgewuAgent`'s
`skillLoader` — is a single flat `.md` file per skill with no companion resources loaded
at runtime. Where an original skill's instructions depended on a companion file:

- **`internal-comms`** and **`theme-factory`**: the companion content (4 communication-type
  guides; 10 theme color/font specs) was small enough to inline directly into the skill body.
  Functionally equivalent to the original.
- **`mcp-builder`**, **`webapp-testing`**, **`canvas-design`**, **`algorithmic-art`**: dead
  references to bundled scripts/templates/reference docs (e.g. `scripts/with_server.py`,
  `templates/viewer.html`, `./reference/*.md`, `./canvas-fonts`) were rewritten as inline
  equivalent guidance (write the glue code yourself, fetch docs live via WebFetch, use
  system/downloaded fonts, etc.) rather than pointing at files that don't exist here.
- **`frontend-design`**, **`brand-guidelines`**: no companion-file dependency; unchanged
  other than frontmatter reformatting.

## What was intentionally left out

- **`docx`, `pdf`, `pptx`, `xlsx`** — Anthropic's own document-creation skills. Per
  `anthropics/skills`' README and each folder's `LICENSE.txt`, these four are explicitly
  **source-available, not open source** ("may not extract... reproduce... or create
  derivative works"). Not eligible for redistribution here.
- **`doc-coauthoring`** — no `LICENSE.txt` in the upstream folder; license status unclear,
  so not redistributed.
- **`skill-creator`** — Apache-2.0, but `disesfgewuAgent` already ships its own
  purpose-built `skill-creator` skill (tailored to this project's registry/CP-grounding
  format); adding Anthropic's generic version here would collide/compete with it.
- **`slack-gif-creator`**, **`web-artifacts-builder`** — Apache-2.0, but depend on
  substantial bundled code (a Python `core/` package with GIF-optimization and easing
  logic; shell scripts scaffolding a Vite+Tailwind+shadcn project) that wasn't
  faithfully reproducible as inline prose without either fabricating an unverified
  reimplementation or pulling in a lot of original engineering work. Left out rather
  than shipped half-working; happy to properly port these later if wanted.
- **`claude-api`** — wasn't in the curated list this batch was sourced from and its
  content didn't match `anthropics/skills`' actual `claude-api` skill; dropped for
  unclear provenance.

## Everything else

Any other skill you add to `skills/` and don't attribute here is assumed to be your own
work or otherwise cleared for inclusion by you.
