---
name: evening
description: Run my Claude mastery evening check-in and update the tracker
---
The plan and tracker live in: __REPO_PATH__
Read claude-mastery-plan.md and claude-mastery-tracker.md from that directory
(cd there first so git operations work).

If claude-mastery-plan.md is empty or not yet initialized, tell me to run
/init-mastery first and stop.

Otherwise follow the "evening" daily process and cadence in the plan file:
ask me ONE open question about how today went and wait; quiz me with ONE
question for the current week and wait; tell me right/wrong and correct me;
estimate today's % completion vs. prior day and whether we're on pace for 100%
by Thursday evening. Then append a dated entry to the tracker's Daily log
(day number + %), update Current state including "Instructions for tomorrow's
morning task", and commit and push ONLY claude-mastery-tracker.md.
NEVER edit the plan file.
