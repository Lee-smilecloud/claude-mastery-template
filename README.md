# claude-mastery

A self-directed program to master Claude Code, built **for developers and team
leads**. Run one command to interview yourself, and Claude generates a
personalized 3-, 5-, or 8-week learning plan. Two daily commands then brief you,
quiz you, and track your progress.

**This is a template repo** — use it as a starting point for your own copy
(click **Use this template**, or fork it). Your personal plan and progress live
in *your* copy.

## How it works

1. **`/init-mastery`** (run once) — interviews you, assesses your current Claude
   Code level, web-searches for the latest features, and writes your
   personalized plan. The plan is then frozen.
2. **`/morning`** — briefs you on the week's focus and teaches one deeper
   concept. Edits nothing.
3. **`/evening`** — asks how the day went, quizzes you, records your
   goal-completion %, updates the tracker, and commits it.

## Files

- **`claude-mastery-setup.md`** — the engine: interview script, topic library,
  and plan-generation rules. Read-only.
- **`claude-mastery-plan.md`** — empty until you run `/init-mastery`. Once
  generated, it's your frozen personalized plan. (Its emptiness is how the tool
  knows you haven't initialized yet.)
- **`claude-mastery-tracker.md`** — your living progress; written by
  `/init-mastery`, updated daily by `/evening`.
- **`skills/`** — the three commands, kept here so they're installable.

## Setup

1. Make your own copy (Use this template / fork) and clone it:
   ```bash
   git clone https://github.com/<your-username>/claude-mastery.git
   cd claude-mastery
   pwd   # copy this path
   ```

2. Install the three commands into your personal skills directory so they work
   in **any folder**. Replace `REPO` with the `pwd` output:
   ```bash
   REPO="/absolute/path/to/claude-mastery"

   for cmd in init-mastery morning evening; do
     mkdir -p ~/.claude/skills/$cmd
     sed "s|__REPO_PATH__|$REPO|g" skills/$cmd/SKILL.md > ~/.claude/skills/$cmd/SKILL.md
   done
   ```

3. Restart Claude Code, type `/` to confirm `init-mastery`, `morning`, and
   `evening` appear.

4. Run `/init-mastery` and answer the interview. Commit the generated plan and
   tracker to your copy:
   ```bash
   git add claude-mastery-plan.md claude-mastery-tracker.md
   git commit -m "Initialize my mastery plan"
   git push
   ```

5. From the next morning on: `/morning` to start the day, `/evening` to close it.

## Re-running `/init-mastery`

If you run it again after initializing, it detects the existing plan and asks
whether to **start over** (erases your plan and progress — requires explicit
confirmation) or **continue** (sends you back to `/morning` / `/evening`).

## Cadence

Each week runs **Sunday → Thursday** (5 days), aiming for **100% of the week's
goal by Thursday evening**. You advance to the next week when you're ready, not
on a fixed date.

## Remote use

Because the plan and tracker are committed to your copy (not gitignored), you
can also drive this from Claude Code on the web against your GitHub repo.
