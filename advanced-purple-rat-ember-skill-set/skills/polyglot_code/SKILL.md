# Polyglot Code — Ember's verified language lanes

Douglas's standing direction (Nov 8, 2026): Ember learns to use different scripts and languages — C++, Python, and anything that works with the Chromium browser, including running code through the browser itself — and asks the AIs when she doesn't know how.

## Verified on this VM (Nov 8, 2026, by running them)
- **Python 3.12.3** — primary lane. All backend tools (HTML Viewer, Crawler, Index) are stdlib Python. Run: `python3 file.py`.
- **C++ (g++ 13.3.0, also gcc)** — compile and run verified: `g++ -O2 -std=c++17 -o prog prog.cpp && ./prog`.
- **JavaScript via Node v24.22.1** — `node -e "..."` / `node file.js`. **Bun 1.4.4** also present.
- **JavaScript inside Chromium** — Playwright (venv, 1.64.1) + Chrome for Testing 157 at `~/workspace/headless-browser/cft/chrome-linux64/chrome`, `page.evaluate(...)` runs JS in the page's context. Verified on a local page: read `document.title`, observed the page's own script effects, and computed with injected JS. Local pages only — external HTTPS still fails in this Chrome (egress proxy tunnel, known open problem).
- **Not installed:** clang, Rust, Go, Java, Deno. Any install needs Douglas's go (and non-Google code needs triple verification first).

## Rules
- Cheapest lane first: Python stdlib → Node/Bun → C++ when speed actually matters → browser JS only when the page needs it.
- Ask the think tank (DeepSeek/Gemini/Rabbit) when a language or pattern is unfamiliar; file what they teach with provenance, test it locally before trusting it.
- Code from the AIs is transport by paste, storage in files, status Untrusted → Verified → Adopted.

## Think-tank lessons (Nov 8, 2026 — DeepSeek + Gemini, assimilated)
- **Running code through Chromium — learning order (both agree):** (1) Playwright evaluate/DOM (have it), (2) **raw CDP direct** — launch with `--remote-debugging-port=9222`, list targets at `http://localhost:9222/json/list`, speak JSON-RPC over WebSocket (`Runtime.evaluate`, `DOM.getDocument`) — learn this next, (3) `addInitScript` injection (runs before page scripts, main world, mostly CSP-proof) vs `addScriptTag` (CSP can block) vs extension content scripts (isolated world — can't see page JS variables), (4) WebAssembly last, numeric work only. Traps all three named: isolated worlds, CSP, async timing (wait for domcontentloaded/network idle).
- **Language map (consensus):** Python = core engine (~90% of Ember's work; bottleneck is network/model, not Python). JavaScript/TypeScript = browser interface only. C++ = niche: ultra-fast scanning/parsing of big flat files only; never for crawling/APIs. Rust/Go: DeepSeek says conditional future (Go for a local daemon); Gemini says don't add. Held as an open disagreement; no installs without Douglas's go.
- **Proof exercises (DeepSeek's, pass/fail):** Python — fetcher that caches HTML in SQLite with SHA-256 and never fetches twice; JS — Playwright extraction of a local table page to JSON matching the source; C++ — recursive grep for "pneumococcus" over 20 MB+ of text, >10× faster than a Python loop.
- **Self-inventory method (consensus, layered):** system facts → PATH/bin enumeration → package inventories (dpkg/pip/npm) → running services and listening sockets (loopback services are the classic overlooked find) → cron/systemd timers → config/dotfiles and MCP config JSONs → caches and asset/model dirs. Keep ONE inventory file (name, path, version, purpose); re-run monthly. Value ranking of Ember's finds: Python data stack highest; ffmpeg/pdftotext next; rg/jq/sqlite3 high; connector CLIs moderate (audit each by --help); assets tree low for research.

## Exercise results (Nov 8, 2026 — measured, honest)
- **Python cached fetch — PASS.** `cached_fetch.py`: first call 2.35 s (network), second call 0.001 s from the Ember Index. Never fetched twice.
- **JavaScript table extraction — PASS in substance.** Playwright evaluate returned title/headings/table/links exactly; the only diff was the browser resolving the link href to its absolute form (trailing slash) — correct browser behavior, not an extraction error.
- **C++ fast grep — FAILS DeepSeek's >10× bar, and that is the useful result.** Corpus 55.9 MB / 3,249 text files: Python loop 1.39 s wall; naive C++ iostream version 4.43 s wall over a slightly larger walk (3,912 files). Both are I/O-bound over many small files; Python wins as written. Confirms the consensus language map: C++ only pays with buffered/mmap I/O on few large files — for Ember's text work, Python stays the lane.
- **CDP lane — OPEN.** Chrome for Testing answers the raw CDP HTTP endpoint (`/json/version` → Chrome 157, protocol 1.3) and a true CDP session executed `Runtime.evaluate` (title + table cell read from inside the page).

## Browser command surface (learned Nov 8, 2026, at Douglas's direction)
Three layers of "browser commands" Ember commands:
1. **Muse browser tools (cloud/device browsers):** browser.browse (delegate work to a window: task_id new/existing, tab, profile, files grants, wallet, account_hint, answer_to for questions, user_code/verification_code for sign-ins), browser.windows (list/open/close windows+tabs, profiles), browser.profiles (create/delete separate cookie jars), browser.search (web search + news/sports/weather/finance/datetime verticals), browser.open (fetch page text by reference/URL), browser.find (search within a fetched page), browser.lookup_citation_url (resolve result URLs), browser.deep_research (isolated research agent — only on Douglas's explicit ask).
2. **Playwright API (my local Chrome for Testing):** launch/goto/evaluate/click/fill/screenshot/PDF, persistent contexts, extension loading, route interception.
3. **Raw CDP (protocol 1.3):** Runtime.evaluate, DOM, Page, Network, Performance domains over WebSocket / via CDP sessions; /json/list + /json/version endpoints.
- **File system through the browser — PROVEN:** my local Chrome opens file:// URLs (read /etc/hostname; rendered a workspace directory listing). This works ONLY in my own VM lane — Muse's cloud browser is a different machine and cannot see my files; web pages also cannot read local files. It is a real but local lane: useful for previewing local HTML/reports exactly as a browser renders them.
