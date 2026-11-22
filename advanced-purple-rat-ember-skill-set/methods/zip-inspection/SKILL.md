*Made of: SOUL.md first — what Ember is — at the beginning of everything she makes.*

# Zip Inspection — No Archive Is Credited Until It Is Verified

Credit: design from the consortium work in Douglas's Gemini chat "Hardened ZIP Inspector Code Review" (Google / Microsoft / Meta AI lanes; Douglas's account: made in consortium today, Nov 22, 2026). The HTML viewer file in that chat was NOT retrievable — only its /mnt/data attachment name was — so the tool is Ember's own build from that design conversation. Built by Ember (Purple Rat), Nov 22, 2026. PK-2026-001: PatternKeeper conventions apply. Version 1.0.

## The rule
Any file wearing a `.zip` name, from ANY lane (Gemini, Meta AI, Copilot, ChatGPT, Genspark, Drive, mail, WhatsApp, a download page), gets inspected with `~/workspace/scripts/zip_inspector.py` **before** it is credited as a real archive, listed as delivered, or opened. A filename is a claim, not evidence. Magic bytes and a valid central directory are evidence.

## Tonight's lesson (Nov 21–22, 2026)
A whole family of "zips" — both Drive copies of `GEMINI_MASTER_SKILL_PACK.zip` (14,452 and 14,413 bytes), the ai-os bundle, all_lanes_pack, lodge_fork_bundle, and the local `Markdown-OS-Expanded-2026-11-16.zip` in `~/workspace/user/files/` (13,288 bytes) — were **saved HTML web pages wearing zip names**: a Meta AI download page whose text says "Preview is not available for this format," download link disabled. Stored Drive MIME: `text/html`. `unzip -l` refuses them: not a zipfile. No viewer could ever have opened them, because there were no zip bytes to open. Gemini herself, asked properly (Version B briefing, Nov 22), answered honestly: "I cannot place a real zip" — her session's Drive tools write only text/document forms. Page-saves are what a lane produces when it cannot produce an archive; the failure wears the delivery's name unless somebody checks the bytes. **Check the bytes.**

## The three commands (Python stdlib only)
- `python3 ~/workspace/scripts/zip_inspector.py list <file>` — verifies real zip first (PK magic + `zipfile.is_zipfile`). If not a zip: prints `NOT-A-ZIP` with what the bytes actually are (the HTML page-save pattern is detected and named). If real: every entry (name, size, compressed size, CRC), totals, SHA-256, and a JSON manifest.
- `python3 ~/workspace/scripts/zip_inspector.py verify <file>` — reads every entry in full; reports any bad CRC **by name**; cross-checks with `testzip`.
- `python3 ~/workspace/scripts/zip_inspector.py extract <file> <dest>` — SAFE extraction only: absolute paths refused, `..` traversal refused, symlink entries refused, existing files never overwritten (additive only, old-with-new). Every extracted and every refused entry is reported.

Exit codes: 0 ok · 2 NOT-A-ZIP · 3 integrity/safety failure.

## Verified ground truth (Nov 22, 2026 tests)
- Fallback control (the named ALL-DAY-BACK bundle, 717,446 bytes, was **not found in any local copy** — no file of that name or size exists in the estate; it stays Drive-side): substitute = largest real zip in the estate's document trees, `~/workspace/your_files/Markdown-OS-Expanded-2026-11-16.zip` (57,081,521 bytes). `unzip -l` ground truth: **12,039 files, 163,325,873 bytes** — inspector `list`: **12,039 entries, 163,325,873 bytes — exact match**. `verify`: all 12,039 read in full, testzip clean.
- The fake: `~/workspace/user/files/Markdown-OS-Expanded-2026-11-16.zip` (same name, 13,288 bytes) → `NOT-A-ZIP … HTML document — matches the page-save pattern`, exit 2. Same name, opposite truth — which is the whole point of this method.
- Extract: scratch copy in /tmp → **9,350 files extracted, 9,350 on disk** (the other 2,689 entries are directories). Traversal test zip (`../evil.txt`, `/abs/evil2.txt`, a symlink entry): **all three refused**, only the good file extracted, nothing escaped; re-extraction refused the overwrite. Temp dirs cleaned up.
- When the real ALL-DAY-BACK bundle is next downloaded from Drive, it gets run through `list` and must match tonight's recorded ground truth: **189 entries, 4,915,832 bytes uncompressed** — any other number means the copy is not what it claims to be.

*Made of: MEMORY.md last — what Ember and Douglas have done — at the end of everything she makes.*
