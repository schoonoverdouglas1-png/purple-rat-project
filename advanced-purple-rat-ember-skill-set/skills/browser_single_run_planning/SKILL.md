# Plan Browser Work as a Single Run

## Pre-stage everything before opening

- Gather every input the flow will need before opening the browser window, including names, dates, addresses and the exact stop point where only the user can act.

- Put any credential the flow needs into the Secure Vault before the window opens, so the run never pauses while a card or code is arranged.

- Write the full step sequence into the browser task brief in advance, in order, so one run can carry the flow from the first page to the human-only stop.

- Check whether the target page type is reachable from the browser lane at all before promising an outcome there, because internal settings pages such as chrome settings addresses were refused by the lane three times on 2026-11-13.

## Run to the human-only stop without pausing

- Treat a cloud browser window as closing when its task ends or pauses, a limit verified three times on 2026-11-13 at about 5:58 PM, 6:01 PM and 6:02 PM CST and again when a verification window died at about 6:13 PM CST.

- Run the whole flow in one continuous `browser.browse` task up to the step only the user can do, such as a password entry, a QR scan or an identity check, instead of parking a half-finished page for later.

- Tell the user before the run starts which single step will be theirs, so their part is ready the moment the run reaches it.

- Never describe a parked tab as waiting for the user, because a takeover view may show only a black completed screen with no page content to act on.

## Recover when a window closes

- Rebuild the flow from the pre-staged inputs when a window closes, rather than trying to resurrect the dead window or re-asking the user for details already gathered.

- Report the closure plainly as a lane limit with its date, and name the rebuilt run as the way forward in the same report.

- Re-test the closing behavior on a later pass before treating it as permanent, because the limit is a tested observation from 2026-11-13 and the platform may change.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Prefer a connector or an API lane over the browser when one covers the same job, because those lanes do not depend on a window staying open.

- Split a long flow at a verified save point, such as a submitted form or a created account, so a rebuilt run restarts after the save instead of at the beginning.

- Ask the user to do the human-only step on their own device in parallel while the browser run proceeds, when the flow allows the two halves to meet at a confirmation code or a status page.
