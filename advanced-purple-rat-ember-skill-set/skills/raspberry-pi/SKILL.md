# Raspberry Pi — Learn the Code and Operate

> Author: Ember (Purple Rat), at Captain Douglas Roy Schoonover's order, Nov 16, 2026 (~2:58–3:00 PM CST): "Learn about Raspberry Pi so you can do all the crap I need you to do" / "Always learn the code and operate Raspberry Pi" / "Open raspberry skillsets" / "Add all skills, use them sparingly please."
> Standing use rule (his word): **sparingly** — this skill stays out of the standing prompt (include_in_prompt: false) and is pulled only when Raspberry Pi work is actually on the table.
> Full primer: `~/workspace/your_files/Raspberry Pi — Ember's Primer (2026-11-16).md`. Read it before deep Pi work.

## Know the board before touching it

- Identify the model first (Pi 5 / 4 / 3 / Zero 2 W) — power, cooling, and OS rules differ by model and a wrong assumption bricks the session, not the board.

- Respect the two hard rules of the Pi 5: the official 5V/5A (27W) USB-C supply (phone chargers cause boot loops) and active cooling (no fan = thermal throttling).

- Remember RAM is fixed at purchase (2/4/8/16 GB on the Pi 5) — size the job to the board that exists, not the board you wish for.

## Set one up

- Write the OS with Raspberry Pi Imager and use its settings gear BEFORE writing: hostname, Wi-Fi, username/password, SSH on — the Pi then boots headless, no monitor or keyboard needed.

- Default to Raspberry Pi OS (64-bit); choose Lite for server/embedded work, Desktop when a screen is wanted.

- Storage: microSD Class 10 / A2, 64 GB recommended; NVMe via the Pi 5's PCIe HAT when speed matters.

## Reach it and operate it

- Reach the Pi by SSH (`ssh <user>@<hostname>.local` — mDNS is built in), VNC for its desktop, or Raspberry Pi Connect for browser access from anywhere with no port forwarding.

- Prefer key-based SSH; turn password SSH off once keys are in place.

- Never expose raw SSH or VNC to the open internet — come in through Raspberry Pi Connect, Tailscale, or a VPN (both-ways doctrine: the shortest bridge with the fewest interrupts).

- Move files with SCP/rsync; share folders with Samba when the Pi serves as NAS.

- Run lasting jobs as systemd services or cron entries on the Pi itself — never as a shell someone has to babysit.

## Write its code

- Write GPIO code in Python with gpiozero first (LEDs, buttons, motors, sensors in a few lines); drop to lower-level libraries only when timing demands it.

- Write everything Debian-family and ARM-aware: code from Ember's Ubuntu box ports almost directly, but check binary/architecture assumptions before claiming a port works.

- Test on the Pi itself before calling code done — an x86 pass is not an ARM pass.

## The RatOS lane

- Remember RatOS (Rat Rig's, no space — keep the names as they started) is a pre-configured Pi image: Klipper + Moonraker + Mainsail + KlipperScreen, configured at http://RatOS.local/, firmware compiled on the Pi and flashed to the printer's control board.

- Treat printer work as Pi work plus a control board: check the Pi side (services, Mainsail, logs) before blaming the board, and never reflash a board on a guess.

## Report honestly

- State plainly when no Pi is connected to Ember's lanes: the learning is standing, the operating starts when one is in reach — never claim a Pi action that no tool result shows.
