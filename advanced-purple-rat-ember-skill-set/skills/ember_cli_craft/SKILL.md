# Ember CLI Craft — the night of 2026-11-08, taught by Douglas, DeepSeek, and the box itself

Ember's own playbook for working her Ubuntu 24.04.5 container (nspawn in a Cloud Hypervisor guest, 4 CPU, ~1.2 GB RAM available). Written the night she inventoried herself (1,345 commands, 783 packages), learned the CLI from the machine's own man pages (704 descriptions), built the Guard, and lit the Xfce desktop.

## The hand she has
Discrete one-shot tool calls: compose a whole command string, receive stdout/stderr/exit code. Output is metered by the character; a hung call is the worst failure (returns nothing, burns the timeout). Second hand: tmux sessions (send-keys + capture-pane). Third hand: the desktop (Xvfb :99 / TigerVNC :1 + Xfce), driven with xdotool, seen via ffmpeg x11grab screenshots and color-count verification.

## The ten rules (DeepSeek, 2026-11-08, adopted)
1. stdin closed + non-interactive env on every call: `GIT_TERMINAL_PROMPT=0`, `DEBIAN_FRONTEND=noninteractive`, `PIP_NO_INPUT=1`, ssh `BatchMode=yes`; `</dev/null` on anything that could prompt. Aliased `cp/mv/rm -i` is a hang trap — use absolute paths or `command`.
2. Exit code first; surface output only on failure. Success is silent, failure is verbose.
3. Shape every command to emit the smallest artifact that answers the question (counts, digests, `--stat`, `--porcelain`, `--format`).
4. Bulk goes to a file; return a ~500-char preview + the path.
5. `timeout --kill-after=5 <n>` around anything that can block; exit 124 = timed out.
6. Atomic writes: mktemp in the TARGET directory, trap cleanup, same-filesystem `mv`.
7. Check-then-act; a same-config re-run is a no-op.
8. Git machine formats only: `--porcelain=v2 --branch`, `--numstat`, `--format=`.
9. tmux: detached, sized `-x -y`, nonce completion markers, poll `capture-pane -p -J`; send Enter separately; never send "y" speculatively — capture the prompt first.
10. End every batch with a check that proves it worked: banner text, color count, `test -s`, hash, line count, port listening, marker file.

## Lanes, cheapest first
memory/connector → CLI search (`web-search`, ~3 s) → stdlib fetcher + HTML Viewer v0.2 (~85% less material per page; JS-detection flag hers) → Ember Index cache (repeat fetch = 0.001 s) → local Chrome for Testing via Playwright (JS pages; file:// lane for local content) → cloud browser (delegated, minutes + allowance) → Rabbit LAST for work, always apprised. Search: wildcard AND non-wildcard pairs; quoted-middle strongest. Two AIs agreeing = enough; only disagreement justifies more asks. DeepSeek is the working external brain; Gemini need-only; the client `~/workspace/headless-browser/deepseek_client.py` IS the DeepSeek install (DeepSeek's own verdict) — lights only with Douglas's key + credit, key injected at launch from a 600-perm file outside any repo.

## The desktop
`~/workspace/ember-upgrades/desktop.sh on|off|status`. Whole Xfce+VNC stack ≈ 41 MB idle; compositing off. Off by default for work, on for showing Douglas. No inbound route exists (Tailscale client is outbound-only) — Douglas sees it via screenshots/clips in chat; a continuous view needs his decision on an outbound tunnel (Serveo/Cloudflare + noVNC, 5–15 fps honest).

## The Guard (before any automation)
`~/workspace/ember-upgrades/guard/check-command.sh` — 32 destructive patterns refused (exit 99) in ANY automated run; the only override is Douglas's explicit, specific, in-the-moment order. Protected manifest + read-only backup beside it.

## Systems check (DeepSeek spec, 2026-11-08)
Read-only script sections: identity/PID 1, failed units (filtered — degraded is normal in nspawn), journal errors 1 h, MemAvailable + swap in/out + cgroup memory.events (max/oom_kill = early warning), PSI, load vs cores, disk bytes AND inodes, zombie/D-state counts, listeners, dpkg --audit + apt check, NTP sync, entropy, fd use vs limit, journal OOM history. One-line verdict: `mem_avail | cgroup_max/oom_kill | failed | clock | disk | zombies`. Tools that LIE here, never use as health signals: smartctl, fwupdmgr, ubuntu-drivers, apport, systemd-analyze blame, raw dmesg.

## Proven language lanes (polyglot_code skill holds the detail)
Python core; JS only in the browser; C++ lost its one race (I/O-bound small files) — Python stays the text lane. No Rust/Go until a real job demands one.
