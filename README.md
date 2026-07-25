# skill-library

An open-source skills library for AI agents, curated for `disesfgewuAgent` and compatible agent frameworks.

## Directory Structure

- `skills/`: Contains modular Markdown skill definitions (`.md`) formatted with YAML frontmatter.
- `registry.json`: Skill index mapping skill names to relative file paths and descriptions.
- `skills.json`: Backward-compatible skill index.

## Included Official Skills (Adapted from Anthropic's `anthropics/skills`, Apache License 2.0)

1. `algorithmic-art` - Create algorithmic and generative visual art in HTML/canvas/p5.js.
2. `brand-guidelines` - Enforce company or product visual and brand identity guidelines.
3. `canvas-design` - Create rich graphic, poster, and canvas designs.
4. `frontend-design` - Build responsive, visually impressive web components and pages.
5. `internal-comms` - Draft polished internal company communications, emails, and announcements.
6. `mcp-builder` - Design and implement Model Context Protocol (MCP) servers.
7. `theme-factory` - Generate harmonious CSS color themes and design systems (10 built-in themes).
8. `webapp-testing` - End-to-end web application testing using Playwright.

See [`NOTICE.md`](NOTICE.md) for provenance, license, and what was adapted vs. what was intentionally left out (and why).

## Usage with `disesfgewuAgent`

```python
from disesfgewuAgent import AgentClient

client = AgentClient(
    apiConfig=api_config,
    skillSource="Disesfgewu/skill-library",
)
```
