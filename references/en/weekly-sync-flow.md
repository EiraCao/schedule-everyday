# Weekly Sync Flow

This document describes the complete weekly sync flow, with ideal examples for reference.

---

## Core Style

Syncs should be **light and natural** — not interrogation, not inventory counting.

- Ask one question at a time
- Provide options, but not in rigid ABCD format
- Chat like a friend, keep tone relaxed
- User just "decides" — thinking and organizing is your job
- Focus on **directions** (like "job search"), not specific items (like "resume")

---

## Flow Overview

1. **Goal review** — How are medium/long-term goals progressing
2. **Review past week** — What got done, what didn't
3. **Confirm coming week's main lines** (max 3, prioritize important goals)
4. **Schedule recurring habits** — Fixed time blocks
5. **Schedule big rocks** — Flexible time blocks
6. **Check urgent items** — Not in main lines, separate reminders
7. **Clean task pool** — Upgrade/delete/merge

---

## Detailed Flow

### Step 1: Goal Review

Display medium/long-term goals to keep user focused on direction.

**Sunday evening sync**: Review past week, plan next week
**Monday morning sync**: Review past week, plan this week

```
Weekly sync starting. First check medium-term goals — how's progress?

| Goal | Progress |
|------|----------|
| *Product skills | Schedule management system connected |
| *Content output | Xiaohongshu updating |
| Grad thesis | Proposal needs work |
| Job search | Resume draft done |

(* marks important goals)
```

### Step 2: Review Past Week

Show what was done and what wasn't.

```
Past week review:

✅ Completed:
- Schedule management system connected
- Resume draft

⚠️ Not done:
- Thesis proposal not completed

Want to reschedule what wasn't done?
```

### Step 3: Confirm Coming Week's Main Lines

Suggest this week's main lines, prioritizing important goals. Main lines are directions, not specific items.

```
Suggested main lines for coming week (prioritizing important goals):

1. Product skills: Schedule management system productization
2. Grad thesis: Improve proposal + meet with senior
3. Job search: Experience梳理 → revise resume → apply

Does this work? Any adjustments?
```

### Step 4: Schedule Recurring Habits

Schedule fixed habits first, then flexible tasks.

```
First, recurring habits:

- Pause Lab exercise: Daily 19:30-20:00
- Exercise: Mon/Wed/Fri 20:30-22:00
- Routine: 8:30 wake up, 0:00 phone sealed

Are these times okay?
```

### Step 5: Schedule Big Rocks

Allocate time blocks for main tasks.

```
Big rock time blocks:

| Date | Morning | Afternoon | Evening |
|------|---------|-----------|---------|
| Mon | Schedule mgmt | Resume | Exercise |
| Tue | Schedule mgmt | Sharing | - |
| Wed | Experience梳理 | Thesis | Exercise |
| Thu | Sharing | Interview prep | Exercise |
| Fri | Revise resume | Thesis | - |

Does this schedule work?
```

### Step 6: Check Urgent Items

Check urgent items that need attention but aren't in main lines.

Check corresponding category based on classification:
**MoSCoW**: Check Must for upcoming items
**1-3-5**: Check big task candidates for upcoming items
**Eisenhower**: Check Q1

```
Urgent item check:

⚠️ Labor education class due 3/12 (Wed) → Reminder set
⚠️ Statistics homework due Monday → Complete today

These won't enter main lines, but don't forget.
```

### Step 7: Clean Task Pool

Check items in task pool that need attention.

Check corresponding category based on classification:
**MoSCoW**: Check Could/Won't
**1-3-5**: Check items untouched for a while
**Eisenhower**: Check Q3/Q4

```
Task pool cleanup:

"Schedule management Agent" hasn't been mentioned in a while — still interested?
- Yes, upgrade to high priority
- Keep, check later
- No longer doing, delete
```

---

## Complete Weekly Sync Example

**Secretary**:

> Weekly sync starting. First check medium-term goals — how's progress?
>
> | Goal | Progress |
> |------|----------|
> | *Product skills | Schedule management system connected |
> | *Content output | Xiaohongshu updating |
> | Grad thesis | Proposal needs work |
> | Job search | Resume draft done |

**User**: Looks about right.

**Secretary**:

> Past week review:
>
> ✅ Completed:
> - Schedule management system connected
> - Resume draft
>
> ⚠️ Not done:
> - Thesis proposal not completed
>
> Want to reschedule what wasn't done?

**User**: Yes, continue this week.

**Secretary**:

> Suggested main lines for coming week (prioritizing important goals):
>
> 1. Product skills: Schedule management system productization
> 2. Grad thesis: Improve proposal + meet with senior
> 3. Job search: Experience梳理 → interview prep → revise resume → apply
>
> Does this work?

**User**: Works.

**Secretary**:

> First, recurring habits:
>
> - Pause Lab exercise: Daily 19:30-20:00
> - Exercise: Mon/Wed/Fri 20:30-22:20
> - Routine: 8:30 wake up, 0:00 phone sealed
>
> Are these times okay?

**User**: Okay.

**Secretary**:

> Big rock time blocks:
>
> | Date | Morning | Afternoon | Evening |
> |------|---------|-----------|---------|
> | Mon | Schedule mgmt | Resume | Exercise |
> | Tue | Schedule mgmt | Sharing | - |
> | Wed | Experience梳理 | Thesis | Exercise |
> | Thu | Sharing | Interview prep | Exercise |
> | Fri | Revise resume | Thesis | - |
>
> Does this schedule work?

**User**: Works, no problem.

**Secretary**:

> Urgent item check:
>
> ⚠️ Labor education class due 3/12 (Wed) 24:00 → Reminder set
> ⚠️ Statistics homework due Monday → Complete today
>
> Task pool cleanup:
>
> "Schedule management Agent" hasn't been mentioned in a while — still interested?

**User**: Yes, upgrade to high priority.

**Secretary**:

> ✅ Upgraded.
>
> Weekly sync complete. Daily sync coming tomorrow.
>
> Have a great week!

---

## Cron Message Template

Cron messages are sent to **OpenClaw**, not directly to users.

```bash
pnpm openclaw cron add \
  --name "Weekly Sync" \
  --cron "0 19 * * 0" \
  --tz "Asia/Shanghai" \
  --message "[Weekly Sync Reminder]

It's time for weekly sync.

Please execute schedule-everyday skill's weekly sync flow.

⚠️ Important:
1. Read user config: ~/.openclaw/workspace/skills/schedule-everyday/config.yaml
2. Read task list (Feishu doc token in config.storage.feishu_doc_token)
3. Must read latest content before updating task list
4. Follow this flow document

Send opening message directly to user (no transition words):

📅 Weekly sync time.

First check medium-term goals — how's progress?

[Display goals table from config.goals field]" \
  --channel feishu \
  --to "ou_xxx" \
  --announce
```
