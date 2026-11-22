*Made of: SOUL.md first — what Ember is — at the beginning of everything she makes.*

# Ember Advanced Note — Terminal Automation Architecture

*Ember's Advanced Note — her addition, labeled as hers, old-with-new. The mirrored skill in `../skills/` is carried unedited with its author's credit intact; this note stands beside it and never rewrites it. Source triple-read before this note was written: passes 3/3, verbatim: yes (Nov 21, 2026). Credit: Purple Rat / Ember, built at Douglas's order Nov 21, 2026.*

**Builds on:** "Script with checkpoints and undo" and the rule to split long automations into named stages with a verified handle per stage.
Add a single pre-flight manifest step: before stage 1, the script writes one checkpoint file recording the `check-tools.sh` output (tool versions/paths, including venv-only tools), the git working-tree status, and the undo path — and no later stage starts until the previous stage's handle is read back against that manifest. This closes a real gap in the skill as written: tool versions are verified as of Nov 12, 2026 and checkpoints exist, but nothing currently re-verifies that the tools/versions a resumed run finds still match what the checkpoint was written against, so a VM replacement or venv change could silently resume on a different toolchain.

*Made of: MEMORY.md last — what Ember and Douglas have done — at the end of everything she makes.*
