# Claude Mastery — Setup Engine (DO NOT EDIT)

> This file is the engine behind `/init-mastery`. It is read-only. It defines
> how to interview a user, assess their level, and generate a personalized
> `claude-mastery-plan.md`. The `/init-mastery` command reads and obeys this
> file. `/morning` and `/evening` do NOT use this file — they use the generated
> plan and tracker.

---

## 0. Audience

This program is for **software developers and team leads** who want to master
Claude Code and Anthropic's tooling. Assume that context throughout: repos,
pull requests, code review, sprints, CI, team enablement.

---

## 1. Guard rule (run FIRST, every time)

Before doing anything else, read `claude-mastery-plan.md`:

- **If it is empty or contains only an HTML comment / placeholder** → the fork
  is NOT initialized → proceed to the interview (Section 2).
- **If it contains real plan content** → the fork is ALREADY initialized → do
  NOT interview. Tell the user a plan already exists, then ask them to choose:
  - **Start over** — warn clearly that this ERASES the existing plan and all
    tracker progress and cannot be undone. Require an explicit "yes, start over"
    before doing anything. Only then clear both `claude-mastery-plan.md` and
    `claude-mastery-tracker.md` and run a fresh interview.
  - **Continue** — change nothing. Tell them to use `/morning` or `/evening`
    instead, and end.

Never assume "start over." Destructive action requires explicit confirmation.

---

## 2. Interview

Interview the user conversationally — a few questions at a time, not all at
once — adapting follow-ups to their answers. Be warm and brief. Cover:

1. **Role & context** — what they build, team size, solo or leading others.
2. **Where their code lives** — GitHub/GitLab/etc., and sprint/task tool
   (Jira, Linear, ClickUp, GitHub Projects…).
3. **Current Claude Code level** — which of these they already use: plan mode,
   CLAUDE.md, custom skills/commands, subagents, hooks, MCP connectors,
   background tasks, plugins, Cowork. (This drives the level assessment.)
4. **Biggest time sink** — coding, code review, sprint/task management,
   mentoring/unblocking.
5. **Top goal for the program** — the one thing they most want to improve.
6. **Commitment length** — 3, 5, or 8 weeks (the only three options).

Keep it to ~2–3 exchanges. Don't over-interview.

---

## 3. Level assessment

From the answers, classify the user as **beginner / intermediate / advanced**:

- **Beginner** — uses Claude Code as single-conversation chat; little/no use of
  skills, subagents, hooks, MCP.
- **Intermediate** — uses plan mode, CLAUDE.md, writes some skills; not yet
  using subagents/hooks/MCP systematically.
- **Advanced** — already delegates with subagents, uses hooks/MCP, thinking
  about plugins and team rollout.

**Do not teach what they already do.** Skip or compress topics they've mastered;
spend their weeks on genuine gaps. Note the assessment in the generated plan.

---

## 4. Curriculum: curated library + live refresh

Build the plan from TWO sources, then filter by level and goal:

### 4a. Curated topic library (the reliable core)

Each topic below is a candidate "week focus." Pick and order based on the
user's level, goal, and time sink.

- **Subagents & parallelism** — built-in explore agent, custom agents in
  `.claude/agents/`, parallel runs, background tasks, effort/model discipline
  (Sonnet/medium default, Opus/high for hard reasoning). Goal: less hands-on.
- **Skills as a system** — `.claude/skills/<name>/SKILL.md`, invokable + auto-
  triggered; encoding personal/team standards into reusable skills.
- **Code review at scale** — a review skill encoding real standards; reviewing
  diffs; iterating the skill.
- **Hooks** — deterministic lifecycle rules (e.g. PreToolUse secret scan);
  making rules non-optional.
- **GitHub integration** — connect the repo/PR workflow so Claude pulls PRs,
  runs review skills on diffs, posts comments.
- **MCP connectors** — connecting external tools (task trackers, Drive, Slack);
  read vs. write actions; confirm-before-write discipline.
- **Sprint & task automation** — read activity → draft retro/standup → write
  tasks into the tracker tool; confirm before external writes.
- **Plugins** — bundling skills + subagents + hooks + MCP as one versioned
  install; `/team-onboarding`.
- **Cowork** — agentic knowledge-work for non-CLI tasks; summaries, docs.
- **Context & prompting discipline** — keeping context clean, plan mode,
  effort levels, when to escalate models.

### 4b. Live refresh (freshness)

Claude Code ships fast. During generation, **web-search for current and newly
released Claude Code / Anthropic features and recommended uses** (e.g. "latest
Claude Code features", "new Claude Code skills hooks subagents"). Fold anything
new, relevant, and level-appropriate into the candidate topics or add a short
"what's new" element to a week.

**Fallback:** if web search is unavailable in the session, skip 4b silently,
build from the curated library alone, and note in the plan that it was built
from the library without a live refresh.

---

## 5. Assembling the plan (3 / 5 / 8 weeks)

Scale the curriculum to the chosen length:

- **3 weeks** — essentials only. Pick the 3 highest-leverage topics for this
  user's goal (commonly: subagents, skills/review, one automation topic).
- **5 weeks** — the core path: subagents → skills/review → hooks+GitHub →
  automation → plugins (adjusted to level/goal).
- **8 weeks** — core path plus depth: add MCP connectors, Cowork, advanced
  subagent/context patterns, and a dedicated team-rollout week.

Each week MUST contain: a one-line **focus**, why it matters, 2–4 concrete
**exercises**, and 2–3 **quiz questions** for the quiz bank. Always reflect the
user's real stack (their VCS, their sprint tool) in examples.

---

## 6. Cadence model (write into every generated plan)

- Each week runs **Sunday (Day 1) → Thursday (Day 5)** — 5 working days.
- The evening task records a **% completion** of the week's goal each day,
  compares to the prior day, and pushes for **gradual rise to 100% by Thursday
  evening**.
- Every evening entry ends with **instructions for the next morning task**.
- **Week advancement is the user's** — suggest it when ~100% and exercises done,
  but only advance when they say so.

---

## 7. What to write, and the freeze

`/init-mastery` writes TWO files, then stops:

1. **`claude-mastery-plan.md`** — the personalized plan: intro with the level
   assessment, the N weeks (focus/why/exercises/quiz), the daily process
   (morning + evening steps), the cadence model (Section 6), and the rules
   (only the tracker is editable; plan is read-only; honest %; append-only log;
   confirm before external writes). Once written, this file is **frozen**.
2. **`claude-mastery-tracker.md`** — seeded to Week 1 of the plan: Current state
   block (start date, current week/focus, day-of-week, % = 0, on-pace, momentum,
   instructions-for-tomorrow, ready-to-advance), the per-week exercise
   checkboxes, the quiz bank, and an empty append-only Daily log.

After writing both, confirm to the user that the plan is frozen and tell them to
run `/morning` next (and to commit the two files to their fork).

---

## 8. The daily process to embed in the generated plan

**Morning (09:30):** read plan + tracker; 3–4 sentence briefing on this week's
focus; teach ONE deeper concept not already in the exercise list; tailor to the
tracker's "instructions for tomorrow", momentum, and latest log; edit nothing.

**Evening (17:00, interactive):** read plan + tracker; ask ONE open question
about the day and wait; quiz ONE question for the current week and wait;
mark right/wrong and correct; estimate today's % vs. prior day and whether on
pace for 100% by Thursday; append a dated log entry (day number + %); update
Current state incl. instructions for tomorrow; commit and push ONLY the tracker.
Never edit the plan.
