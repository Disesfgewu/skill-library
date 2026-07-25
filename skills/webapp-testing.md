---
name: webapp-testing
description: Toolkit for interacting with and testing local web applications using
  Playwright. Supports verifying frontend functionality, debugging UI behavior, capturing
  browser screenshots, and viewing browser logs.
version: 1.0.0
author: Anthropic / disesfgewuAgent
tags:
- testing
- playwright
- e2e
- qa
---

# Web Application Testing

To test local web applications, write native Python Playwright scripts. No bundled helper scripts ship with this skill — write the server-lifecycle glue and the Playwright logic yourself (below) rather than relying on an external script.

## Decision Tree: Choosing Your Approach

```
User task → Is it static HTML?
    ├─ Yes → Read HTML file directly to identify selectors
    │         ├─ Success → Write Playwright script using selectors
    │         └─ Fails/Incomplete → Treat as dynamic (below)
    │
    └─ No (dynamic webapp) → Is the server already running?
        ├─ No → Start the dev/prod server yourself (see below), wait for its
        │        port to accept connections, then run a simplified Playwright script
        │
        └─ Yes → Reconnaissance-then-action:
            1. Navigate and wait for networkidle
            2. Take screenshot or inspect DOM
            3. Identify selectors from rendered state
            4. Execute actions with discovered selectors
```

## Managing the server lifecycle yourself

When the target app isn't already running, start it as a background subprocess, poll the port until it accepts connections, run the Playwright automation, then terminate the subprocess — don't leave orphaned dev servers running:

```python
import socket, subprocess, time

def wait_for_port(port, host="localhost", timeout=30):
    deadline = time.time() + timeout
    while time.time() < deadline:
        try:
            with socket.create_connection((host, port), timeout=1):
                return True
        except OSError:
            time.sleep(0.5)
    raise TimeoutError(f"port {port} did not open within {timeout}s")

server = subprocess.Popen("npm run dev", shell=True)
try:
    wait_for_port(5173)
    # ... run your Playwright automation against http://localhost:5173 ...
finally:
    server.terminate()
    server.wait(timeout=10)
```

For multiple servers (e.g. backend + frontend), start each `subprocess.Popen`, `wait_for_port` on each, then terminate both in `finally`.

To create an automation script, include only Playwright logic once the server is confirmed up:
```python
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.chromium.launch(headless=True) # Always launch chromium in headless mode
    page = browser.new_page()
    page.goto('http://localhost:5173') # Server already running and ready
    page.wait_for_load_state('networkidle') # CRITICAL: Wait for JS to execute
    # ... your automation logic
    browser.close()
```

## Reconnaissance-Then-Action Pattern

1. **Inspect rendered DOM**:
   ```python
   page.screenshot(path='/tmp/inspect.png', full_page=True)
   content = page.content()
   page.locator('button').all()
   ```

2. **Identify selectors** from inspection results

3. **Execute actions** using discovered selectors

## Common Pitfall

❌ **Don't** inspect the DOM before waiting for `networkidle` on dynamic apps
✅ **Do** wait for `page.wait_for_load_state('networkidle')` before inspection

## Best Practices

- Use `sync_playwright()` for synchronous scripts
- Always close the browser (and terminate any subprocess server you started) when done
- Use descriptive selectors: `text=`, `role=`, CSS selectors, or IDs
- Add appropriate waits: `page.wait_for_selector()` or `page.wait_for_timeout()`
- For element discovery, use `page.locator(...).all()` combined with a screenshot and `page.content()` rather than guessing selectors blind
- For static HTML, `page.goto('file:///absolute/path/to/file.html')` works without a server
- To capture console logs, register a listener before navigating: `page.on("console", lambda msg: print(msg.type, msg.text))`
