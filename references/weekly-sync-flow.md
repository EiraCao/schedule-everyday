# Weekly Sync Flow

This document describes the complete weekly sync flow, including ideal examples for reference.

---

## Core Style

Syncs should be **lightweight and natural**, not an interrogation or inventory check.

- Ask only one question at a time
- Provide options, but avoid rigid ABCD formats
- Chat like a friend, keep the tone relaxed
- User only needs to "approve" — thinking and organizing is your job
- Main focus revolves around **directions** (e.g., "job search"), not specific items (e.g., "resume")

---

## Flow Overview

1. **Goal review** — How's progress on medium/long-term goals
2. **Review the week just passed** — What was completed, what wasn't
3. **Confirm main focus for the coming week** (no more than 3 items, improvement-focused first)
4. **Schedule recurring habits** — Fixed time blocks
5. **Schedule main focus big rocks** — Flexible time blocks
6. **Check urgent items** — Don't enter main focus, remind separately
7. **Clean up task pool** — Upgrade/delete/merge

---

## Detailed Flow

### Step 1: Goal Review

Display medium/long-term goals, let user focus on direction.

**Sunday evening sync**: Review last week, plan next week
**Monday morning sync**: Review last week, plan this week

```
Weekly sync starting. First let's look at medium-term goals — how's progress?

| Goal | Progress |
|------|----------|
| *Product Skills | Schedule management system connected |
| *Content Output | Xiaohongshu updating |
| Graduation Thesis | Proposal needs refinement |
| Job Search | Resume draft complete |
```

(* marks important goals)

### Step 2: Review the Week Just Passed

Display completed and incomplete items.

```
Review of the week just passed:

✅ Completed:
- Schedule management system connected
- Resume draft

⚠️ Didn't do:
- Thesis proposal not finished

Want to reschedule the incomplete items?
```

### Step 3: Confirm Main Focus for the Coming Week

Suggest this week's main focus, prioritizing important goals. Main focus revolves around directions, not specific items.

```
Suggested main focus for the coming week (important goals first):

1. Product Skills: Schedule management system productization
2. Graduation Thesis: Refine proposal + Chat with senior
3. Job Search: Experience梳理 → Revise resume → Submit applications

Does this work? Or want to adjust?
```

### Step 4: Schedule Recurring Habits

Schedule fixed habits first, then flexible tasks.

```
First let's schedule recurring habits:

- Pause Lab exercises: Daily 19:30-20:00
- Exercise: Mon/Wed/Fri 20:30-22:00
- Sleep schedule: 8:30 wake up, 0:00 phone lockdown

Do these times work?
```

### Step 5: Schedule Main Focus Big Rocks

Arrange time blocks for main focus tasks.

```
Big rock time blocks:

| Day | Morning | Afternoon | Evening |
|-----|---------|-----------|---------|
| Mon | Schedule mgmt | Resume | Exercise |
| Tue | Schedule mgmt | Sharing | - |
| Wed | Experience review | Thesis | Exercise |
| Thu | Sharing | Interview prep | Exercise |
| Fri | Revise resume | Thesis | - |

Does this schedule work?
```

### Step 6: Check Urgent Items

Check urgent items that won't enter main focus but need attention.

Based on classification method, check corresponding categories:
**MoSCoW method**: Check Must for upcoming deadlines
**1-3-5 method**: Check big task candidates for upcoming items
**Eisenhower method**: Check Q1

```
Urgent items check:

⚠️ Labor education course due 3/12 (Wed) → Reminder set
⚠️ Mathematical Statistics homework due Monday → Complete today

These won't enter main focus, but don't forget to do them.
```

### Step 7: Clean Up Task Pool

Check items in the task pool that need attention.

Based on classification method, check corresponding categories:
**MoSCoW method**: Check Could/Won't
**1-3-5 method**: Check items in task pool that haven't moved in a while
**Eisenhower method**: Check Q3/Q4

```
Task pool cleanup:

"Schedule Management Agent" hasn't been mentioned in a while — still want to do it?
- Yes, upgrade to high priority
- Keep, check later
- No, delete it
```

---

## Weekly Sync Complete Example

**Assistant**:

> Weekly sync starting. First let's look at medium-term goals — how's progress?
>
> | Goal | Progress |
> |------|----------|
> | *Product Skills | Schedule management system connected |
> | *Content Output | Xiaohongshu updating |
> | Graduation Thesis | Proposal needs refinement |
> | Job Search | Resume draft complete |

**User**: Yeah, about right.

**Assistant**:

> Review of the week just passed:
>
> ✅ Completed:
> - Schedule management system connected
> - Resume draft
>
> ⚠️ Didn't do:
> - Thesis proposal not finished
>
> Want to reschedule the incomplete items?

**User**: Yes, continue this week.

**Assistant**:

> Suggested main focus for the coming week (important goals first):
>
> 1. Product Skills: Schedule management system productization
> 2. Graduation Thesis: Refine proposal + Chat with senior
> 3. Job Search: Experience梳理 → Interview prep → Revise resume → Submit applications
>
> Does this work?

**User**: Works for me.

**Assistant**:

> First let's schedule recurring habits:
>
> - Pause Lab exercises: Daily 19:30-20:00
> - Exercise: Mon/Wed/Fri 20:30-22:20
> - Sleep schedule: 8:30 wake up, 0:00 phone lockdown
>
> Do these times work?

**User**: Yes, they work.

**Assistant**:

> Big rock time blocks:
>
> | Day | Morning | Afternoon | Evening |
> |-----|---------|-----------|---------|
> | Mon | Schedule mgmt | Resume | Exercise |
> | Tue | Schedule mgmt | Sharing | - |
> | Wed | Experience review | Thesis | Exercise |
> | Thu | Sharing | Interview prep | Exercise |
> | Fri | Revise resume | Thesis | - |
>
> Does this schedule work?

**User**: Yes, no problem.

**Assistant**:

> Urgent items check:
>
> ⚠️ Labor education course due 3/12 (Wed) 24:00 → Reminder set
> ⚠️ Mathematical Statistics homework due Monday → Complete today
>
> Task pool cleanup:
>
> "Schedule Management Agent" hasn't been mentioned in a while — still want to do it?

**User**: Yes, upgrade to high priority.

**Assistant**:

> ✅ Upgraded.
>
> Weekly sync complete. Daily sync tomorrow.
>
> Let's have a great week!

---

## Cron Job Message Template

Cron job messages are sent to **OpenClaw**, not directly to users.

```bash
pnpm openclaw cron add \
  --name "Weekly Sync" \
  --cron "0 19 * * 0" \
  --tz "Asia/Shanghai" \
  --message "[Weekly Sync Reminder]

It's time for weekly sync.

Please execute schedule-everyday skill's weekly sync flow.

⚠️ Important:
1. First read user config: ~/.openclaw/workspace/skills/schedule-everyday/config.yaml
2. Then read task list (Feishu doc token in config's storage.feishu_doc_token)
3. Must read latest content before updating task list
4. Then follow this flow document

Send opening message directly to user (don't say anything like "received"):

📅 Weekly sync time.

First let's look at medium-term goals — how's progress?

[Display goals table based on config.goals field]" \
  --channel feishu \
  --to "ou_xxx" \
  --announce
```
