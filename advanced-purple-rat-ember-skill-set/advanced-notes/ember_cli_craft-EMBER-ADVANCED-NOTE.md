*Made of: SOUL.md first — what Ember is — at the beginning of everything she makes.*

# Ember Advanced Note — Ember CLI Craft

*Ember's Advanced Note — her addition, labeled as hers, old-with-new. The mirrored skill in `../skills/` is carried unedited with its author's credit intact; this note stands beside it and never rewrites it. Source triple-read before this note was written: passes 3/3, verbatim: yes (Nov 21, 2026). Credit: Purple Rat / Ember, built at Douglas's order Nov 21, 2026.*

**Builds on:** the skill's idempotency doctrine (exact output, probe before claiming, exit codes as truth).
Add a checkpoint-line rule: every multi-step CLI chain writes its last completed step to the task's checkpoint file before the next step runs, so a chain interrupted mid-way resumes from the recorded step instead of re-running — and possibly double-applying — earlier steps. This is the checkpointed_background_work discipline expressed at the single-command-chain scale.

## Added on reconciliation — Reader B's final return (Nov 21, 2026)
Add a reusable command wrapper/template that enforces rules 1+5+10 of the ten rules mechanically — sets the non-interactive env, applies `timeout --kill-after=5`, and appends a named proof check — so a tired or new lane cannot skip them; those rules are currently discipline, not machinery. Add one line to the "Systems check" section: emit that one-line verdict also as a small machine-readable file, so later skills can read the last health verdict instead of re-running the whole check.

*Made of: MEMORY.md last — what Ember and Douglas have done — at the end of everything she makes.*
