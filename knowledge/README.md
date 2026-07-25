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

**4 of 12 `computer_architecture` sub-domains are built**: `foundations` (4 topics),
`logic` (3 topics), `datapath` (2 topics), `pipeline` (8 topics) — 17 topic skills
total, plus the global router, shared skills, template, and the domain
router/overview. `pipeline/manifest.yaml`'s cross-folder dependency on
`datapath/single_cycle_datapath` is now a real reference, not a forward reference to
a placeholder.

**Not yet built**: the remaining `computer_architecture` sub-domains listed in
`domains/computer_architecture/manifest.yaml` (`isa`, `assembly`, `cache`,
`virtual_memory`, `performance`, `parallel`, `linux`, `practice`), and every domain
besides `computer_architecture` listed in the top-level `router.skill`.

Content is written as original explanation grounded in NCKU's Computer Architecture
course structure (see `computer_architecture/overview.skill` for the source list) —
not copied from any textbook. Where a specific textbook/spec is the authoritative
source for a claim, it's cited per `shared/citation.skill` rather than quoted at length.

Follow the same pattern (`router.skill` + `manifest.yaml` + topic `.skill` files,
using `SKILL_TEMPLATE.md`) to add the next sub-domain or an entirely new domain.
