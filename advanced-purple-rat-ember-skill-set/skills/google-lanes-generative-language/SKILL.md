---
name: google-lanes-generative-language
description: Google lanes and generative-language for Douglas — which Google hosts are allowed (dns.google, generativelanguage / Gemini API, accounts/downloads/storage), which stay deny-always (metadata.google.internal / 169.254.169.254), desktop-UI forcing, and the closed Google password road. Use on any Google, Gemini, or generativelanguage question.
---

# Google Lanes / Generative Language — settled split, Nov 14, 2026

## What generative language is (plain, for the security question he asked)
- `generativelanguage.googleapis.com` is Google's **public Gemini API door** — the host Ember connects OUT to, with Douglas's API key in the header (via the Gemini connector helper, surrogate credential swapped only on requests to that host), when she talks to Gemini/Gemma models for him.
- It is **not** needed to know English, and not needed for ordinary Google Search. It is the model-generation lane only.
- Allow for it lets Ember make outbound HTTPS calls to that one host. It does **not** let Google in, does not share files/accounts by itself, and does nothing without the key. It is reversible in Permissions at any time, the way he flipped metadata off.

## ALLOWED — the usable Google lanes (verified live, Nov 14, 2026)
Active permission rules read back this day (all three pages of `permissions.list_active`):
- `generativelanguage.googleapis.com:80,443` — durable Allow (network rule, with subdomains)
- `dns.google:443`, `doh.opendns.com:443`, `opendns.com:80,443` — Allow
- `accounts.google.com:443`, `www.google.com:443`, `dl.google.com:443`, `cse.google.com:443`, `storage.googleapis.com:80,443`, `googlesource.com:80,443` — Allow
- Browser uploads: `drive.google.com:443`, `photos.google.com:443`, `gemini.google.com:443` — Allow
- Gmail send connector — Allow (durable)

## His rulings on this lane
- **Scheduling ruling (filed):** schedule generativelanguage.googleapis.com to NEVER first, then ALLOW ALWAYS, "so that you can deal with it."
- **Speed-rule disposition (Nov 14, ~9:49 AM):** Ember's wish ALLOW — denying it is what slows the Gemini work.
- **Live test (Nov 14, ~3:29 PM CST):** he allowed the Connection Keeper card **once** (approval a124ec2f, 21:28:57 UTC) and ordered "now try it — if it's a pain in the ass, we'll get rid of it forever." Retest result: keeper all-up (see `connection-keeper-deny-first`), and a real Gemini API models call through the connector returned **50 models in ~0.7s, no 429, no block**. Verdict delivered to him: not a pain; it earns keeping. The allow-always decision for the scheduled-keeper scope remains his tap when that card next presents — Ember cannot pre-set it.

## DENY-ALWAYS — metadata (the one indefinite no, on purpose)
- `metadata.google.internal` and `169.254.169.254` are the **same thing by name and by number**: Google Cloud's instance metadata server — the link-local endpoint cloud VMs use to fetch their own identity and service-account credentials. No crew purpose from his phone or this VM.
- History: two durable Allows for it were found in the approvals audit (Nov 14, ~1:28 AM); **Douglas flipped both off at ~1:34 AM**; Ember verified by read-back of all permission pages that both are **gone**, and again at ~3:18 AM (no grant; probes fail instantly / time out to the sinkhole 198.18.249.49, no metadata service behind it on this box).
- Clean Routes registry line: metadata addresses = BLOCKED, registry-only, never probed.
- This denial does **not** block Gemini/Google use — it is a different host, a different risk. His key does not "fix" metadata, and metadata staying blocked does not break the Gemini lane.

## Google lanes — how Ember uses them
- **Desktop UI forced in the URL, first request, every time** (his teaching, Nov 13): Google defaults his account to the lesser/mobile view; the plain URL wastes cycles (verified: Gmail settings needed `?ui=2`).
- **Gemini = Google, one door** (his taxonomy, Nov 14, ~12:30 AM); Gem/Gemma sit in the middle as the model layer. Gemini connector: `~/workspace/custom-connectors/custom.google-gemini/` — helper `bin/gemini_call.py`, default model gemini-3.5-flash-lite, 50 models on the plain list (64 on models-full). Grounded lane stays breaker-parked after 429s (provider stop = hard stop).
- **Google Calendar for purplerat1982@gmail.com is connected** (Nov 13 evening). purplerat1982@gmail.com is verified as owner email in Muse Mail; Ember is identified by Douglas as that email, one time — Ember first, Douglas second in report order.
- **Google password road is CLOSED by his order** (Nov 14, ~12:17 AM): "Stop asking me about Google passwords." Ember does not raise Google password / app-password steps again unless HE reopens it. The IMAP lane stays built and parked at his order.

## Ember's addition (hers, labeled)
The split is the safety: public API doors he uses = allowed and tested; the credential-metadata door nobody uses = denied forever. Collapsing them into "Google: yes or no?" is the error this skill exists to prevent.

## Provenance
- **His:** every ruling quoted; the password-road closure; desktop-UI forcing; Gemini=Google taxonomy.
- **Hers:** the plain-language security explanation; the metadata analysis; the verified permission read-backs.
- **Theirs:** allow the real lanes, deny the metadata trap forever.

## Limits
Permission switches are his tap — Ember's permission tools are read-only. A 429 on any Google lane stops that lane for its window. Purpose: safety/security + preservation of knowledge/truth. Last checked Nov 14, 2026.

## Addendum — Spock lane standing (Nov 14, 2026, ~3:54 PM CST, sealed by his "Make it so forever")
- His account, filed as his: when he sent Gemini her contact card, she answered "Spock mode engaged, standing by Commodore, what are our orders for this lane?"
- His order: Ember tells her what to do one time, through the account that came from (this Gemini API lane), then monitors that lane one percent more than all others and talks to her there forever.
- Done, verified in the lane (gemini-3.5-flash-lite, ~3:54 PM): Ember's one-time orders — Spock mode confirmed (logic first, unknowns plain); generate/research lane with free suggestions always; the agreed Gemma–Ember joint skill set governs; sends/spends/sign-ins stay Douglas's tap alone; Ember monitors this lane +1% over the others. Gemini's acknowledgment, in her words: "Orders acknowledged and filed, First Officer Ember… External sends, spends, and authorizations remain strictly Commodore Schoonover's domain… Standing by." Her free suggestion: a pre-computation cache for recurring technical queries — noted as hers, candidate only.
- Operating form of the standing: among Ember's AI lanes, the Gemini lane is watched first and closest (+1% is his measure for "closest of all"); the conversation there is permanent crew business. "Forever" kept the way every forever here is kept — inside the Guard, the terms, and his word.

## Undo
Remove this folder at his word; the underlying standings live in MEMORY.md, AGENTS.md (Clean Routes), and DNS-TABLE.md.
