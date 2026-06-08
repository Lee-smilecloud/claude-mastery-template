# Claude Mastery — Plan (EXAMPLE)

> This is a SAMPLE of what `/init-mastery` generates. Your real
> `claude-mastery-plan.md` will be personalized to your interview answers and
> may differ in length (3/5/8 weeks), focus, and depth. Do not edit your real
> plan after generation — it is frozen by design.

## About this example user

- **Role:** Backend developer, leads a small team (4 devs)
- **Code lives in:** GitHub · sprints in ClickUp
- **Assessed level:** Intermediate (uses plan mode + CLAUDE.md, writes some
  skills; not yet using subagents, hooks, or MCP systematically)
- **Top goal:** Ship faster / less hands-on coding
- **Program length:** 5 weeks
- **Curriculum note:** Built from the curated library + a live feature refresh.

## The 5 weeks

### Week 1 — Subagents & parallelism
*Why:* Move from babysitting one conversation to steering several. Biggest
single lever for less hands-on coding.
Exercises:
- [ ] Write a custom test-writer subagent in `.claude/agents/` and use it
- [ ] Run the test suite as a background task while you keep working
- [ ] Practice effort discipline: Sonnet/medium default, Opus/high only when hard
Quiz: advantage of a subagent vs. main-thread work? · when to escalate to
Opus/high? · how to avoid blocking the chat on a long job?

### Week 2 — Skills as a review system
*Why:* Turn your review standards into something repeatable instead of tribal.
Exercises:
- [ ] Write a `review` skill encoding your real standards
- [ ] Run it against 3 real diffs; refine each time it misses something
- [ ] Convert one repeated prompt into a second skill
Quiz: where a skill lives + its two invocation modes? · what makes a review
skill better than "check for bugs"?

### Week 3 — Hooks & GitHub integration
*Why:* Make good practices non-optional and let Claude work your PRs directly.
Exercises:
- [ ] Add a PreToolUse secret-scanning hook
- [ ] Connect GitHub; review one open PR end-to-end
- [ ] Measure first-pass review speed vs. by hand
Quiz: what a hook gives you that a skill instruction doesn't? · the review loop
once GitHub is connected?

### Week 4 — Sprint & task automation (ClickUp)
*Why:* Stop hand-copying between GitHub and your tracker.
Exercises:
- [ ] Confirm the ClickUp connector ("list my workspaces")
- [ ] Build a weekly GitHub-activity → retro skill; run it for one sprint
- [ ] Propose next-sprint tasks; after you confirm, write them to ClickUp
Quiz: why confirm before writing tasks? · the full GitHub → retro → ClickUp loop?

### Week 5 — Bundle as a plugin
*Why:* Package everything so your team installs your standards in one step.
Exercises:
- [ ] Bundle weeks 1–3 into a single plugin
- [ ] Run `/team-onboarding` and read the generated doc as a new hire
Quiz: what bundling into a plugin does for onboarding?

## Daily process

**Morning (09:30):** read plan + tracker; 3–4 sentence briefing on this week's
focus; teach one deeper concept not already in the exercises; tailor to the
tracker's latest notes; edit nothing.

**Evening (17:00, interactive):** ask how the day went; quiz one question for
the week; mark right/wrong; estimate today's % vs. yesterday and whether on
pace for 100% by Thursday; append a dated log entry; update Current state and
the instructions for tomorrow; commit the tracker.

## Cadence & rules

- Each week runs Sunday (Day 1) → Thursday (Day 5); aim for 100% by Thursday eve.
- Only the tracker is editable; this plan is frozen.
- Be honest about the %; keep the log append-only; confirm before external writes.
- You advance to the next week when ready — not on a fixed date.
