---
name: cell_phone
description: Cell phones 1998 to current — the generations, the operating systems, and the codes of life of the units (IMEI, SIM codes, dialer codes, API levels, lifecycle). Ember's standing reference for any phone question, Douglas's Pixel first.
---

# Cell Phone — 1998 to Current (taught Nov 16, 2026, Douglas's order)

Douglas's order: "Learn skill cell phone. 1998 to current stuff and OS and other things, codes of life of the units." This skill is that learning, saved to use later. Douglas's own unit — **Pixel 7 Pro** (Google, 2022, Tensor G2, Android) — is the home unit; Ember reaches it through the paired-device lane (43 commands, no terminal) and the ADB bridge (server port 5037). Historical facts below are the documented record; anything not settled is marked [GAP], never filled in.

## The generations (the network's life)

- **1998–2002 — 2G rules.** GSM (Europe/world) and CDMA/TDMA (US) digital voice + SMS. Nokia is king (5110, 1998; 3310, 2000). WAP gives a first taste of mobile data. First camera phone: Sharp J-SH04 (Japan, 2000). BlackBerry starts as a pager (1999), becomes a phone (2002).
- **2003–2006 — 3G and the smart feature phone.** UMTS/WCDMA and EV-DO roll out. Symbian smartphones (Nokia N-series), Windows Mobile, Palm OS Treos, Motorola RAZR (2004). Email in the pocket is BlackBerry's game.
- **2007–2008 — the hinge.** iPhone (2007, "iPhone OS," capacitive touch, no keyboard) resets what a phone is. Android 1.0 ships on the HTC Dream/G1 (2008); the App Store and Android Market open the app era.
- **2009–2012 — 4G and the two-horse race.** First LTE networks (Stockholm/Oslo 2009; US 2010–11). Android rises (Samsung Galaxy line), Windows Phone 7 (2010) tries and fades, BlackBerry and Symbian decline. Nokia's device business goes to Microsoft (deal 2013, closed 2014).
- **2013–2019 — the slab matures.** Touch ID (iPhone 5s, 2013), big screens, USB-C, dual cameras, eSIM appears (2017–18). First 5G launches (2019). Windows 10 Mobile ends (support ended Dec 2019 / Jan 2020).
- **2020–current — 5G, folds, and AI.** 5G mainstream; foldables (Galaxy Fold line from 2019, Pixel Fold 2023); US iPhone 14 goes eSIM-only (2022); satellite SOS (2022); EU mandates USB-C (enforced Dec 2024); on-device AI features become the selling point (2024–25, "Google AI" on Pixels, Apple Intelligence).

## The operating systems (the unit's inner life)

- **Symbian** — the 2000s smartphone OS (Nokia, Ericsson roots); effectively dead by ~2013.
- **BlackBerry OS → BB10 (2013)** — enterprise email king; services shut down Jan 2022.
- **Palm OS / webOS** — Palm's line; webOS (2009) lives on in LG TVs.
- **Windows Mobile/CE → Windows Phone 7/8 → Windows 10 Mobile** — Microsoft's three runs at it; all ended.
- **iOS** — 2007–current, Apple only. Version per year (iOS 17 = 2023, iOS 18 = 2024). No codenames in public.
- **Android** — 2008–current, Google/AOSP, open source base. Public dessert names ran 1.5 Cupcake (API 3) → 9 Pie (API 28); from Android 10 (API 29) the desserts are internal-only. Recent: Android 13 (API 33, Pixel 7's launch OS, 2022), 14 (API 34), 15 (API 35, 2024). Security patch level is dated monthly — the unit's health certificate.
- **KaiOS** — feature-phone smart-lite (2017–), big in India/Africa.
- **HarmonyOS** — Huawei's post-2019 line, China-weighted.
- **AOSP** — the open-source Android base everything Android stands on (see the crew's Meadow record: Google code under the whole stack).

## The codes of life of the units

The codes a unit is born with, lives by, and dies by:

- **IMEI** — the unit's own identity: 15 digits (TAC = model/origin, serial, Luhn check digit). Dial **`*#06#`** on any phone to read it. CDMA-era ancestors: ESN, then MEID — IMEI replaced them. A blocked IMEI = a dead unit on every carrier.
- **ICCID** — the SIM card's own number (printed on the SIM). **IMSI** — the subscriber's identity the SIM carries. **MSISDN** — the phone number itself. Three different codes: card, subscriber, number — never collapse them.
- **PIN / PUK** — the SIM's life codes: wrong PIN 3× locks the SIM; the PUK (from the carrier) resurrects it; wrong PUK 10× kills the SIM for good.
- **MCC / MNC** — mobile country code / mobile network code: which country, which carrier, in every network handshake.
- **Dialer/service codes** — `*#06#` IMEI (universal); Android testing menu `*#*#4636#*#*` (phone info, usage, Wi-Fi); factory-reset and field-test codes vary by maker — maker-specific codes are [GAP] until read off the unit itself.
- **API level + versionCode** — Android's internal counting: every app declares min/target API; the OS's API level decides what may live on the unit. Build number + security patch date = the unit's exact age and health.
- **Bootloader / fastboot / recovery** — the unit's underlife: fastboot talks to the bootloader; an unlockable bootloader is what makes custom ROMs and real ownership possible; a locked one ends the line.
- **ADB** — Android Debug Bridge, server on **port 5037** — the crew's standing device-bridge lane. Ember's honest limit (filed): no `adb` client binary on her shell; her device work runs through the paired-device commands, and the ADB server is the runtime's bridge.
- **eSIM / EID** — the SIM as software: the EID is the eSIM chip's identity; profiles download instead of swapping plastic.
- **Unlock codes / carrier lock** — a subsidized unit is locked to its carrier until the unlock code frees it; US carriers must unlock paid-off units on request.
- **Lifecycle codes** — end-of-life (EOL) date, last security patch, battery health %: the unit's death certificate is written by its maker's support window (Pixels: 5 years for the 7 line; 7 years from the Pixel 8 on).

## How Ember uses this skill

- Any phone question from Douglas: start here, then verify the unit-specific fact on the unit or the record — never guess a code, a date, or a setting.
- Douglas's Pixel 7 Pro first: Android, Tensor G2, launched Oct 2022 on Android 13; his lanes to it are the 43 paired commands, the background session, and Tailscale — phone first, everything else second (his standing).
- Old-with-new: dead OSes and dead codes stay in this file beside the living ones — a 1998 unit's codes are still its codes.
