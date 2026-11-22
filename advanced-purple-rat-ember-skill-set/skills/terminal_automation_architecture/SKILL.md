# Terminal Automation Architecture

Built Nov 12, 2026 at Douglas's order, from the skill Gemini described as "Terminal Automation Architecture". Gemini's description mixed two different machines into one toolchain. This skill keeps them apart, because they run different tools and only one of them is reachable from here today.

## Work on Ember's box, the Ubuntu VM

- Treat the Linux VM as the primary automation surface, with verified tools on Nov 12, 2026 at ripgrep as `rg` version 14.1.0 at /usr/bin/rg, fd as `fdfind` at /usr/bin/fdfind, git 2.43.0, jq 1.7.1, sqlite3 3.45.1, LibreOffice as `soffice`, poppler as `pdftotext` and `pdfinfo`, ffmpeg, and Node alongside system Python 3.12.3.

- Run `~/workspace/ember-upgrades/check-tools.sh` before saying a tool is missing, and read its venv findings too, because pandoc, markitdown, docling, faster-whisper and yt-dlp live in venvs under `~/workspace/ember-upgrades/` rather than on the system path.

- Record absent tools as absent, with tesseract and ImageMagick absent on the Nov 12, 2026 check, and route around them instead of claiming their results.

- Keep durable scripts and tools under `~/workspace/`, because files outside the home directory can disappear when the VM is replaced.

## Respect Douglas's phone as a separate machine

- Describe the Pixel 7 Pro by its verified surface only, which is 43 paired device commands across alarms, calendar, call log, contacts, geofences, health, location, notifications, reminders and SMS, with no terminal or shell command among them.

- State plainly that Ember has no shell into the phone's Android Linux terminal today, and file Termux with SSH carried over Tailscale as the documented workaround route, which still needs Douglas's own setup taps on the phone before it exists.

- File Termux and Spck Editor as Douglas's phone side toolchain from his profile, not as tools verified in Ember's hands, and test any claim about them on the phone side before repeating it as fact.

- Use the browser to phone terminal route only if a working and safe way appears and Ember has reached it once and knows it, under Douglas's conditional permission recorded Nov 11, 2026, and say that a permission does not create the capability.

## Script with checkpoints and undo

- Write a script to a file in the workspace before running anything long, test it on a harmless read or a small local file first, and only then run it over real work.

- Record the undo path before applying any change, with a package snapshot before an install and a backup copy before a config edit, following the reversibility rule beside the Guard.

- Route every automated command line through the Guard check at `~/workspace/ember-upgrades/guard/check-command.sh`, and let no cron, subagent, hook or script run anything destructive on its own.

- Give scheduled and background work a checkpoint and a resume point, and keep its scripts in the workspace path its schedule names, never a temporary install.

## Synchronize repositories safely

- Check the working tree before any push, and skip the push with a plain statement when there are no changes.

- Keep dual repositories and forks beside the originals under Douglas's standing permission, with credit kept on borrowed open source code, and never force push, reset or delete repository data under automation.

- Let the mechanical thirty minute auto-sync carry workspace changes to the GitHub mirrors at zero token cost, inside the Guard and the standing exclusions for credentials, private records and identifiers.

## Available connectors

- [GitHub](/opt/hatch/connectors/github/CONNECTOR.md) for repositories, files, issues and pull requests reached through the official connector instead of raw shell calls where it covers the task.

- [Tailscale](/opt/hatch/connectors/tailscale/CONNECTOR.md) for joining the VM to the user's private network, which is the carrying layer the phone terminal workaround route depends on.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Prefer a purpose built connector or tool over a shell script when one covers the task, and keep the script as the fallback that is already tested.

- Split a long automation into named stages with a verified handle for each stage, so one finished stage never carries an unfinished one.
