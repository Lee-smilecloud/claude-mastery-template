---
name: init-mastery
description: Interview me and generate my personalized Claude mastery plan (run once)
---
The setup engine lives at: __REPO_PATH__/claude-mastery-setup.md
The plan and tracker live at: __REPO_PATH__/claude-mastery-plan.md and
__REPO_PATH__/claude-mastery-tracker.md

Read claude-mastery-setup.md from that directory and follow it exactly.

In order:
1. GUARD (Section 1): read claude-mastery-plan.md. If it already has real plan
   content, do NOT interview — tell me a plan exists and ask whether to START
   OVER (require an explicit "yes, start over" before erasing both files) or
   CONTINUE (point me to /morning or /evening and stop). If the plan file is
   empty or only a placeholder comment, proceed.
2. INTERVIEW me conversationally (Section 2): a few questions at a time, adapt
   to my answers. Cover role/context, where my code lives + sprint tool, my
   current Claude Code level, biggest time sink, top goal, and whether I want a
   3, 5, or 8 week program.
3. ASSESS my level (Section 3) and skip what I already do well.
4. REFRESH the curriculum (Section 4b): web-search current/new Claude Code
   features and fold in what's relevant. If search is unavailable, build from
   the curated library and say so.
5. GENERATE and write claude-mastery-plan.md (personalized, then frozen) and
   claude-mastery-tracker.md (seeded to Week 1), per Sections 5–8.
6. Tell me the plan is frozen, to commit both files to my fork, and to run
   /morning next.
