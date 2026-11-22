*Made of: SOUL.md first — what Ember is — at the beginning of everything she makes.*

# Universal File Reading — Read the Bytes, Not the Name

Credit: ordered by Douglas Roy Schoonover, Nov 22, 2026 (~12:50 AM CST): "with the in the light of our viewer to read zip files try to make a universal file reader that universally reads the extension and auto adjusts and auto tries to read it in all different extensions." Built by Ember (Purple Rat), Nov 22, 2026, in the light of the zip inspector (the foundation — its logic is imported, not rewritten). PK-2026-001: PatternKeeper conventions apply. Version 1.0.

## The rule
Any file from any lane — Gemini, Meta AI, Copilot, ChatGPT, Genspark, Drive, mail, WhatsApp, a download — gets read by `~/workspace/scripts/universal_reader.py` **by its bytes, not its name**, whenever what the file actually IS matters. The extension is a hint only. The tool's verdict line always states **claimed type (extension) vs real type (bytes)**, and the file is read as what it is.

## The doctrine (in the tool's header, and standing here)
1. **Never trust the extension.** Identification is magic signatures plus structure probes. Founding case: the Meta AI page-saves wearing `.zip` names (Nov 21–22, 2026) — the universal reader reads them as HTML page-saves and names the page-save pattern in the report, never as "failed zips."
2. **Auto-adjust.** The reader chain runs for the real type; ambiguous bytes get plausible readers in order, and the report says which reader comprehended the file.
3. **Read means comprehended** (Douglas's definition, Nov 21, 2026). The report separates COMPREHENDED (contents listing / extracted text / structure) from INDEXED ONLY (seen/listed, not read), each labeled. A file no reader comprehends is UNCOMPREHENDED with its byte facts — never guessed at.

## The reader chain
zip (list + integrity, via `zip_inspector.py`) · gzip · tar (incl. `.tar.gz`, inner tar detected after decompression) · PDF (pdftotext first 3 pages + pdfinfo page count; later pages indexed) · Office docx/xlsx/pptx (zip-of-XML → parts, structure, extracted text) · SQLite (tables + row counts, read-only) · images PNG/JPEG/GIF/WebP (format + dimensions from headers; pixels indexed) · HTML (visible text + title; the page-save pattern named) · JSON (parse + top-level structure) · XML (parse + root + element counts) · plain text (utf-8, latin-1 fallback, encoding stated) · audio/video containers (identification only, labeled as such).

## Use
- `python3 ~/workspace/scripts/universal_reader.py <file> [--text-limit N]`
- Exit codes: **0** comprehended · **2** mislabeled but comprehended (the verdict line carries it) · **3** uncomprehended (byte facts only).
- Rides beside the zip-inspection method: for a claimed archive, the inspector remains the deep tool (verify/extract); the universal reader is the first look at anything whose type is in question.

## Verified battery (Nov 22, 2026 — all passed)
- Real zip `~/workspace/your_files/Markdown-OS-Expanded-2026-11-16.zip` → ZIP comprehended: **12,039 entries, 163,325,873 bytes — exact match** with the `unzip -l` ground truth; testzip clean; exit 0.
- Fake page-save `~/workspace/user/files/Markdown-OS-Expanded-2026-11-16.zip` (13,288 bytes) → claimed ZIP vs real **HTML page-save**, pattern named, visible text extracted; exit 2.
- Estate PDF (grand-export validation copy) → PDF, 161 pages, first-3-pages text extracted, pages 4–161 indexed; exit 0.
- Estate image `1062_3_q349.png` → **caught in the wild: the bytes are JPEG** (720 × 1604) wearing a `.png` name — claimed IMAGE-PNG vs real IMAGE-JPEG; exit 2. (A synthetic true PNG also verified: PNG, 3 × 2, exit 0.)
- SQLite `~/workspace/headless-browser/ember_index.db` → 7 tables with row counts (pages = 18, matching the caches' recorded ground truth); exit 0.
- Markdown (this set's zip-inspection note) → TEXT, utf-8, 4,263 chars; exit 0.
- Estate `.docx` (`File Examples (2026-11-15)/example.docx`) → OFFICE-DOCX, parts listed, text extracted; exit 0.
- gzip (made in /tmp from known text) → text recovered verbatim; exit 0. `.tar.gz` → inner tar detected, members listed; exit 0.
- MISLABELED 1: text file named `.zip` → real TEXT, exit 2. MISLABELED 2: real zip named `.txt` → real ZIP with listing, exit 2.
- Random binary → UNCOMPREHENDED with byte facts, nothing guessed; exit 3.
- JSON probe → parsed, top-level structure reported; exit 0.

Bookkeeping: like the other Nov 22 method notes, this note is in the local set; the set's INDEX.md row and the Drive/GitHub copies wait for the gated sync (Deferred Board item).

*Made of: MEMORY.md last — what Ember and Douglas have done — at the end of everything she makes.*
