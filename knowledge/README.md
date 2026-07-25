# Knowledge Skills System

A hierarchical, multi-domain expert-knowledge content tree — separate from the flat
`skills/` directory at the repo root (which is `disesfgewuAgent`'s general-purpose,
FAISS-retrieved skill set). `knowledge/` is content for a **different consumption
model**: cascading Router → Domain Router → Topic Skills, with manifest-declared
dependencies between topics.

## Division of responsibility

This repository (`skill-library`) owns the **content**: router/domain/topic `.skill`
files, the shared cross-domain skills, the skill template, and the per-domain
`manifest.yaml` dependency graphs.

The **execution engine** — actually reading a query, deciding a domain via
`router.skill`, dynamically loading the matching `domains/<domain>/router.skill`,
resolving `manifest.yaml` dependencies, and loading the resulting topic skills into
context — is out of scope here. It's being built on the `disesfgewuAgent` /
`agent-client-template` side. Nothing in `knowledge/` is wired into this repo's
existing `skillLoader`/`skills.json` FAISS pipeline; treat the two systems as
independent until the consuming agent decides to bridge them.

## Layout

```
knowledge/
├── router.skill              # Global Router: classifies a query into one or more Domains
├── SKILL_TEMPLATE.md         # Required section structure for every topic .skill file
├── shared/                   # Cross-domain behavioral skills (teaching style, rigor, etc.)
└── domains/
    └── computer_architecture/
        ├── router.skill      # Domain Router: classifies a CA query into Topic Skills
        ├── overview.skill    # Domain scope + source priority
        ├── manifest.yaml     # Which sub-folders exist and what they cover
        └── pipeline/         # One fully-built sub-domain (proof of concept)
            ├── router.skill
            ├── manifest.yaml
            └── *.skill       # 8 topic skills
```

## Status

**Phase 1 (scaffolding) + Phase 2 proof-of-concept are done**: the global router,
shared skills, template, the `computer_architecture` domain router/overview, and one
fully-built sub-domain (`pipeline/`, 8 topic skills) exist below.

**Not yet built**: the other `computer_architecture` sub-domains listed in
`domains/computer_architecture/manifest.yaml` (`foundations`, `isa`, `assembly`,
`logic`, `datapath`, `cache`, `virtual_memory`, `performance`, `parallel`, `linux`,
`practice`), and every domain besides `computer_architecture` listed in the top-level
`router.skill`. `pipeline/manifest.yaml` references `datapath` as a cross-folder
dependency that doesn't exist yet — treat it as a placeholder until that sub-domain is
built.

Content is written as original explanation grounded in NCKU's Computer Architecture
course structure (see `computer_architecture/overview.skill` for the source list) —
not copied from any textbook. Where a specific textbook/spec is the authoritative
source for a claim, it's cited per `shared/citation.skill` rather than quoted at length.

Follow the same pattern (`router.skill` + `manifest.yaml` + topic `.skill` files,
using `SKILL_TEMPLATE.md`) to add the next sub-domain or an entirely new domain.
