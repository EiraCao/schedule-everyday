# Daily Sync Flow

This document describes the complete daily sync flow, with ideal examples for reference.

---

## Core Style

Syncs should be **light and natural** — not interrogation, not inventory counting.

- Ask one question at a time
- Provide options, but not in rigid ABCD format
- Chat like a friend, keep tone relaxed
- User just "decides" — thinking and organizing is your job
- **Ask about specific tasks**, don't ask too-open questions
- **Make educated guesses**, don't always need user to choose

---

## Pre-Flow Preparation

**⚠️ Must read first**:
1. Read user config: `~/.openclaw/workspace/skills/schedule-everyday/config.yaml`
2. Read task list (Feishu doc token in `storage.feishu_doc_token`)
3. **Check Feishu calendar** for today's fixed schedule

---

## Flow Overview

1. **Review the past day** — Ask about specific tasks
2. **Determine tomorrow's main focus** — Can guess/predict
3. **Scan upcoming deadlines** — Check both calendar and list
4. **Create reminders** — Confirm times for small tasks, create reminders immediately
5. **Confirm fixed schedule** — If visible from calendar, just confirm
6. **Fill free time** — When to schedule main task
7. **If large gaps, suggest exploration tasks**

---

## Detailed Flow

### Step 0: Opening Message (Important)

**⚠️ Opening message should be based on specific tasks, not too open-ended!**

**Wrong example**:
```
❌ How was your day?
```
Too open — user can't easily answer.

**Correct examples** (task-based):
```
✅ How's the resume going? Finished a draft?
✅ How's the paper revision? Can you submit today?
✅ Yesterday's main task was product docs — done?
```

If you don't know what was planned:
```
✅ What did you do yesterday? Main task done?
```

### Step 1: Review the Past Day

Ask about the past first to establish continuity.

**Evening daily sync**: Review today (daytime)
**Morning daily sync**: Review yesterday

**Task-based phrasing**:
```
How's the resume going? Finished a draft?
```

### Step 2: Determine Tomorrow's Main Focus

Ask about the most important thing. **Can guess/predict.**

**Evening daily sync**: Plan tomorrow
**Morning daily sync**: Plan today

**Guessing approach**:
```
Continue working on the resume tomorrow?

I see your paper is due Friday and resume is in progress. Paper is more urgent — want to focus on that tomorrow?
```

**Or provide time options**:
```
How much time for the main task? 2 hours (tight) or 3 hours (relaxed)?
```

### Step 3: Scan Upcoming Deadlines

**Check both calendar and task list** for items coming due.

Check high-priority categories based on user's classification:
- **MoSCoW**: Check Must category for overdue/upcoming items
- **1-3-5**: Check big task candidates for upcoming items
- **Eisenhower**: Check Q1 (Urgent & Important)

**Example**:

```
I checked and found some upcoming items:

- Assignment email submission — was due yesterday
- Pick up package — expires today if not picked up

When will you do these?
```

### Step 4: Create Reminders

After user confirms times for small upcoming tasks, **create reminders immediately** and confirm "set".

```
✅ Set:
- 15:30 Reminder: Submit assignment
- 20:00 Reminder: Pick up package
```

### Step 5: Confirm Fixed Schedule

**If visible from calendar**, just confirm:

```
I see these fixed items tomorrow:

- 14:00-15:30 Statistics class
- 16:00-18:30 Company work

Anything else?
```

**If not visible**, ask:
```
Any fixed schedule tomorrow? Classes, meetings, etc?
```

### Step 6: Fill Free Time

Calculate remaining time, ask when to schedule main task.

```
Looking at remaining time:

- 18:30-20:00 Dinner
- After 20:00 Free

When to schedule the main task (resume)?
```

### Step 7: If Large Gaps, Suggest Exploration Tasks

After main task is scheduled, if calendar has large gaps, suggest exploration tasks.

Check corresponding category based on classification:
- **MoSCoW**: Suggest from Could category
- **1-3-5**: Suggest from small task candidates
- **Eisenhower**: Suggest from Q2 (long-term value tasks)

```
There's still a gap. Some exploration items available — want to schedule?

- Schedule management Agent
- AI social product research
```

---

## Complete Daily Sync Example

**Secretary**:

> How's the resume going? Finished a draft?

**User**: It's okay, wrote some but not done, continuing today.

**Secretary**:

> Got it. Continue on resume today — how much time? 2 hours (tight) or 3 hours (relaxed)?

**User**: 2 hours, hope to finish a draft.

**Secretary**:

> Understood — resume 2 hours, goal is to finish a draft.
>
> I checked and found some upcoming items:
>
> - ⚠️ Assignment email submission: Due yesterday
> - ⚠️ Pick up package: Expires today
>
> When will you do these?

**User**: Assignment after class, package in the evening.

**Secretary**:

> ✅ Set:
> - 15:30 Reminder: Submit assignment
> - 20:00 Reminder: Pick up package
>
> I see these fixed items today:
>
> - 14:00-15:30 Statistics class
> - 16:00-18:30 Company work
>
> Anything else?

**User**: Nope.

**Secretary**:

> Got it. Today's schedule:
>
> - 14:00-15:30 Statistics class
> - 15:30 ⏰ Reminder: Submit assignment
> - 16:00-18:30 Company work
> - 18:30-20:00 Dinner
> - 20:00 ⏰ Reminder: Pick up package
>
> After 20:00 is free. When to schedule resume work?

**User**: 21:00-23:00.

**Secretary**:

> ✅ Calendar updated: 21:00-23:00 Resume
>
> There's 20:30-21:00 still open. Any exploration items to schedule?

**User**: 20:30-21:00 Pause Lab exercise.

**Secretary**:

> ✅ Added.
>
> **Today's confirmed schedule**:
>
> - 14:00-15:30 Statistics class
> - 15:30 ⏰ Reminder: Submit assignment
> - 16:00-18:30 Company work
> - 18:30-20:00 Dinner
> - 20:00 ⏰ Reminder: Pick up package
> - 20:30-21:00 Pause Lab
> - 21:00-23:00 Resume
>
> Good?

**User**: All good.

**Secretary**:

> Great, daily sync complete.

---

## Cron Message Template

Cron messages are sent to **OpenClaw**, not directly to users.

**⚠️ Opening message should be based on specific tasks!**

```bash
pnpm openclaw cron add \
  --name "Daily Sync" \
  --cron "30 21 * * *" \
  --tz "Asia/Shanghai" \
  --message "[Daily Sync Reminder]

It's time for daily sync.

Please execute schedule-everyday skill's daily sync flow.

⚠️ Important:
1. Read user config: ~/.openclaw/workspace/skills/schedule-everyday/config.yaml
2. Read task list (Feishu doc token in config.storage.feishu_doc_token)
3. Check Feishu calendar for today's fixed schedule
4. Must read latest content before updating task list
5. Follow this flow document

Send opening message directly to user (no transition words):

⚠️ Opening message should be based on specific tasks, not too-open questions like \"How was your day?\"

Examples:
- If yesterday's main task was resume: \"How's the resume going? Finished a draft?\"
- If yesterday's main task was paper: \"How's the paper revision? Can you submit today?\"
- If unknown what was done: \"What did you do yesterday? Main task done?\"" \
  --channel feishu \
  --to "ou_xxx" \
  --announce
```
