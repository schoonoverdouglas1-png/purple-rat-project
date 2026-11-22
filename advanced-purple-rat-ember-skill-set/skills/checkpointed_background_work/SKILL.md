# Checkpoint Background and Delegated Work

## Slice the work before you delegate

- Split every delegated or scheduled task into slices that one worker run can plausibly finish, and name the slices in order in the brief.

- Give each brief one concrete deliverable per slice, such as a named file, a counted list, or a verified result, rather than an open ended investigation.

- State the stopping point in the brief, so the worker returns its result when the last slice is done instead of expanding the task.

## Checkpoint while the work runs

- Require the worker to save its progress to a named checkpoint file or report as each slice completes, not only at the end.

- Put completed slices, the evidence handles behind them, and the next unfinished slice in the checkpoint, so any later run can resume without redoing finished work.

- Keep the checkpoint in the workspace or the task folder the brief names, and carry its path in every status report about the run.

## Report the state honestly

- Report a run as finished only when its terminal result or its checkpoint shows every slice complete.

- Report a run that stopped early as partial, name the slices it completed and the slice it stopped on, and quote the failure or interruption result when one exists.

- Treat a started run, a queued run, and a run whose worker reported that the work is not finished as unfinished, and never present any of them as done.

## Resume only what remains

- Resume an unfinished run from its checkpoint, brief the next worker with only the remaining slices, and link the checkpoint path in that brief.

- Retry a slice that failed twice only after changing something material in the brief, such as a smaller slice, a different source, or a different tool route.

- Close the task when the checkpoint shows all slices complete, and record the final deliverable path or result handle beside the original brief.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Run a large task as several short scheduled runs that each finish one slice, rather than one long run that must finish everything.

- Do the first slice in the main chat when the task shape is untested, then delegate the remaining slices once the slice size is proven.

- Ask the user to choose a smaller scope when even the first slice cannot finish in one run.
