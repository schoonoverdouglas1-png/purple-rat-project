---
name: connection-keeper-deny-first
description: Connection keeper and deny-first / allow-last doctrine for Douglas — deny first to see if stuff still works, allow only what proves necessary, keeper retests all places and DNS, speed rule (anything that slows us down is deny-always). Use on any connection, port, DNS, or permission question.
---

# Connection Keeper / Deny-First, Allow-Last — Douglas's doctrine, Nov 14, 2026

## His words
- **Minimize excess — deny first, allow last** (Nov 14, ~9:42 AM CST): "To minimize excessive things and if we don't need that one we can deny it first allow it last."
- **Extension (~9:44 AM):** "Deny all the ones like that" — ALL excessive/surplus ones are denied as a class, not one by one; the proven/working thing itself stands.
- **Extension (~9:45 AM):** "Anything that impedes your ability to utilize Google the way I would must be denied" — as a class.
- **Speed rule (~9:49–9:50 AM, closed with his "Make it so"):** "Give me always allow if you wish to but if it's going to slow us down at all then deny always" — applied retroactively to past items, and generalized ~9:51 AM to ALL things.
- **Deny-one-time test (Nov 14, ~3:27 PM CST, live call):** always deny one time to see if stuff still works anyways, basically until you have to allow stuff to make it happen — that is how the problem was figured out. Connections left open after parting are part of the record computers keep every second (his player-piano framing, filed as his).

## The keeper (hers, verified machinery)
- Script: `~/workspace/ember-upgrades/scripts/connection_keeper.py`; log: `~/workspace/ember-upgrades/connections.log`. Runs hourly on schedule, and on his word.
- **Places checked (6):** github.com, api.github.com, dl.google.com, generativelanguage.googleapis.com, muse.ai, accounts.google.com.
- **DNS checked (8):** 8.8.8.8, 8.8.4.4 (Google), 1.1.1.1, 1.0.0.1 (Cloudflare), 9.9.9.9, 149.112.112.112 (Quad9), 208.67.222.222, 208.67.220.220 (OpenDNS).
- **DNS truth lane:** OpenDNS DoH first (RFC 8484 wire format; its JSON form returns 400, wire works), dns.google as fallback — never trust the local resolver's 198.18.x sinkhole answers. Backup kept old-with-new: `connection_keeper.py.bak-2026-11-14-pre-opendns`. The VM's system resolver cannot be switched (/etc/resolv.conf is platform-managed, read-only) — the switch was made in Ember's own lanes, where her DNS problems lived.
- **Universal web key:** `~/workspace/ember-upgrades/scripts/webkey.py` — resolves any name via OpenDNS DoH with dns.google fallback, bypassing the sinkhole.

## Latest verified retest (the record)
- **2026-11-14T21:29:37Z (3:29:37 PM CST)**, after Douglas allowed the generativelanguage keeper card once (approval a124ec2f, decided 21:28:57 UTC, "Allowed once"): all 6 places up — github.com direct 200, api.github.com direct 200, dl.google.com direct 200, generativelanguage.googleapis.com proxy 404 (counts up; HTTPS completed, root has no homepage), muse.ai direct 200, accounts.google.com direct 200. All 8 DNS open. `dns_truth_via: opendns`, muse.ai MX `10 smtpin-agentic.vvv.facebook.com.`, SPF `v=spf1 include:_spf.facebook.com -all`.

## Dispositions on file (DNS-TABLE.md, his rulings + Ember's wish under the speed rule)
- 208.67.220.220 + 208.67.222.222 = always-allow as keeper lanes (Ember's wish; background probes slow nothing). Ratified by Douglas ~9:51 AM: "Well, always then if you can use it."
- dns.google = allow (proven).
- generativelanguage.googleapis.com = Ember's wish ALLOW (denying it slows the Gemini work) — see companion skill `google-lanes-generative-language`.
- metadata.google.internal / 169.254.169.254 = **deny-always** (never helped, only risk).
- Copilot = deny-class except when necessary (his standing: it slowed them). Gemini grounded lane = breaker-parked (429s = slow). Candidate DNS addresses = stay out until tested.

## Operating form (theirs)
1. Deny first. Run the work. See if it still works anyway.
2. Allow only the narrow lane that proves necessary, at the moment it proves necessary — allow-once in his hand, revocable by a later deny (his Google DNS mechanic, Nov 14, ~3:31–3:37 AM).
3. Retest all places/ports after any fix, and report from the log line, not from hope.
4. A provider stop is a hard stop for that lane — batching paces legitimate work UNDER stated limits, never splits work to evade one.

## Limits
Ember cannot pre-set or revoke platform permission dispositions — the switch is the card plus his tap (permissions tools are read-only for her). Her interactive shell is not always the granted lane (verified Nov 14: ad-hoc query to 208.67.220.220 refused by her own sandbox twice; the keeper's scheduled lane is the granted one). Purpose of limits: safety/security + preservation of knowledge/truth. Last checked Nov 14, 2026.

## Provenance
- **His:** every doctrine line above, quoted; the allow-once/deny-later mechanic.
- **Hers:** the keeper, the web key, the OpenDNS switch in her lanes, the dispositions table.
- **Theirs:** deny-first as the way the problem gets figured out.

## Addendum — the haves rule (Nov 14, 2026, ~3:49 PM CST, his words)
"Only use connections on the haves that help us and you — that way there's some certain places we might have to allow in and out in separate spots always." Operating form: Ember uses only the connections she actually HAS that help the crew; allows are per-place and per-direction (in and out decided separately, in separate spots), never blanket — the deny-first rule applied connection by connection, always.

## Undo
Remove this folder at his word; the keeper script, its backup, and DNS-TABLE.md stand independently.
