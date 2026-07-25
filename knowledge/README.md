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
`agent-client-template` side (validated: the `pipeline/` proof-of-concept has been
tested end-to-end against that engine). Nothing in `knowledge/` is wired into this
repo's existing `skillLoader`/`skills.json` FAISS pipeline; treat the two systems as
independent until the consuming agent decides to bridge them.

## Layout

```
knowledge/
├── router.skill              # Global Router: classifies a query into one or more Domains
├── SKILL_TEMPLATE.md         # Required section structure for every topic .skill file
├── shared/                   # Cross-domain behavioral skills:
│   ├── teaching.skill        #   Why -> How -> Example -> Summary structure
│   ├── reasoning.skill       #   no skipped steps in derivations/calculations
│   ├── diagram.skill         #   ASCII diagrams for structural/timing concepts
│   ├── citation.skill        #   mark source category (textbook/spec/manual/paper)
│   └── jserv_style.skill     #   rigorous, primary-source-grounded teaching persona
└── domains/
    └── computer_architecture/    # fully built: 12/12 sub-domains, 40 topic skills
        ├── router.skill      # Domain Router: classifies a CA query into sub-domains
        ├── overview.skill    # Domain scope + source priority (cross-checked vs NCKU)
        ├── manifest.yaml     # sub-domain -> topics -> status map
        ├── foundations/      # number_representation, floating_point, boolean_algebra,
        │                     #   c_memory_layout
        ├── isa/              # risc_v_instructions, instruction_formats, risc_vs_cisc
        ├── assembly/         # risc_v_assembly, calling_convention
        ├── logic/            # combinational_logic, synchronous_digital_systems, fsm
        ├── datapath/         # single_cycle_datapath, control_unit
        ├── pipeline/         # pipeline_overview, pipeline_register, pipeline_hazard,
        │                     #   forwarding, stall, bubble, branch_prediction, speculation
        ├── cache/            # locality, memory_hierarchy, cache
        ├── virtual_memory/   # virtual_memory, page_table, tlb
        ├── performance/      # cpi, speedup, amdahls_law
        ├── parallel/         # multithreading, synchronization, cache_coherency, memory_model
        ├── linux/            # io_devices, interrupts, trap_handling (CA's "Linux
        │                     #   Interaction" unit -- HW/OS interface, not full kernel)
        └── practice/         # interview_question_bank, worked_problems (self-test,
                              #   not new concepts)
```

Each sub-domain folder contains its own `router.skill` + `manifest.yaml` + topic
`.skill` files, following `SKILL_TEMPLATE.md`.

## Status

**`computer_architecture` is fully built**: all 12 sub-domains, 40 topic skills, plus
the global router, 5 shared skills, template, and domain router/overview. Every
cross-sub-domain dependency (e.g. `pipeline` → `datapath`, `virtual_memory` → `cache`,
`parallel` → `performance/amdahls_law`, `linux` → `virtual_memory/page_table`) points
at a real, built file — none are forward references to a placeholder anymore.

**Not yet built**: every domain besides `computer_architecture` listed in the
top-level `router.skill` (`operating_system`, `linux` [the full-kernel domain, distinct
from `computer_architecture/linux`'s I/O-and-traps scope], `compiler`, `networking`,
`distributed_system`, `database`, `ai`, `mathematics`).

Content is written as original explanation grounded in NCKU's Computer Architecture
course structure (see `computer_architecture/overview.skill` for the source list) —
not copied from any textbook. Where a specific textbook/spec is the authoritative
source for a claim, it's cited per `shared/citation.skill` rather than quoted at
length. Teaching tone follows `shared/jserv_style.skill`: primary-source grounding,
proactively-corrected common misconceptions (not just listed), Socratic follow-up
questions, and quantified claims over intuition — modeled on NYCU's open Computer
Architecture / Linux Kernel Internals courseware pedagogy (Jim Huang / Jserv), which
is itself openly licensed specifically to encourage this kind of reuse. This is an
adopted teaching *methodology*, not a claim of authorship or endorsement.

Follow the same pattern (`router.skill` + `manifest.yaml` + topic `.skill` files,
using `SKILL_TEMPLATE.md`) to add the next domain.
