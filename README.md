# skill-library

An open-source skills library for AI agents, curated for `disesfgewuAgent` and compatible agent frameworks.

## Directory Structure

- `skills/`: Contains modular Markdown skill definitions (`.md`) formatted with YAML frontmatter.
- `registry.json`: Skill index mapping skill names to relative file paths and descriptions.
- `skills.json`: Backward-compatible skill index.

## Included Official Skills (Converted from Anthropic Claude Skills)

1. `algorithmic-art` - Create algorithmic and generative visual art in HTML/canvas/p5.js.
2. `brand-guidelines` - Enforce company or product visual and brand identity guidelines.
3. `canvas-design` - Create rich graphic, poster, and canvas designs.
4. `claude-api` - Integrate and invoke Anthropic Claude APIs and SDKs.
5. `doc-coauthoring` - Co-author, refine, and edit long-form written documents.
6. `docx` - Create, edit, and manipulate Microsoft Word (`.docx`) documents.
7. `frontend-design` - Build responsive, visually impressive web components and pages.
8. `internal-comms` - Draft polished internal company communications, emails, and announcements.
9. `mcp-builder` - Design and implement Model Context Protocol (MCP) servers.
10. `pdf` - Process, analyze, and extract content from PDF files.
11. `pptx` - Generate and format Microsoft PowerPoint (`.pptx`) presentations.
12. `skill-creator` - Author and structure new skills for AI agents.
13. `slack-gif-creator` - Generate animated GIFs optimized for Slack and messaging apps.
14. `theme-factory` - Generate harmonious CSS color themes and design systems.
15. `web-artifacts-builder` - Construct interactive web apps and React components.
16. `webapp-testing` - End-to-end web application testing using Playwright.
17. `xlsx` - Generate and analyze Microsoft Excel (`.xlsx`) spreadsheets with openpyxl.

## Usage with `disesfgewuAgent`

```python
from disesfgewuAgent import AgentClient

client = AgentClient(
    apiConfig=api_config,
    skillSource="Disesfgewu/skill-library",
)
```
