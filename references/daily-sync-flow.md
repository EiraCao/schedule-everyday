# Daily Sync Flow

This document describes the complete daily sync flow, including ideal examples for reference.

---

## Core Style

Syncs should be **lightweight and natural**, not an interrogation or inventory check.

- Ask only one question at a time
- Provide options, but avoid rigid ABCD formats
- Chat like a friend, keep the tone relaxed
- User only needs to "approve" — thinking and organizing is your job
- **Ask based on specific items**, don't ask overly open questions
- You can **guess and anticipate**, you don't always have to let the user choose

---

## Pre-Flow Preparation

**⚠️ Must read first**:
1. Read user config: `~/.openclaw/workspace/skills/schedule-everyday/config.yaml`
2. Read task list (Feishu doc token in config's `storage.feishu_doc_token`)
3. **Also check Feishu calendar** to understand today's fixed schedule

---

## Flow Overview

1. **Review the day just passed** — Ask based on specific items
2. **Determine the main focus for the coming day** — Can guess and anticipate
3. **Scan upcoming deadlines** — Check both calendar and task list
4. **Create timed reminders** — Confirm times for small deadline items, create reminders immediately
5. **Confirm fixed schedule** — If already visible from calendar, just confirm
6. **Fill free time** — When to schedule main focus tasks
7. **If large gaps remain, recommend exploration items**

---

## Detailed Flow

### Step 0: Opening Message (Important)

**⚠️ Opening message should be based on user's specific items, don't ask overly open questions!**

**Wrong example**:
```
❌ How was your day?
```
Too open-ended, user won't know how to answer.

**Correct examples** (based on items):
```
✅ How's the resume coming? Did you finish a draft?
✅ How's the paper revision going? Can you submit today?
✅ Yesterday's main focus was the product doc — did you finish it?
```

If you don't know what was planned:
```
✅ What did you do yesterday? Did you complete the main focus?
```

### Step 1: Review the Day Just Passed

First ask about the past to establish continuity.

**Evening daily sync**: Review today's daytime
**Morning daily sync**: Review yesterday

**Item-based questioning**:
```
How's the resume coming? Did you finish a draft?
```

### Step 2: Determine the Main Focus for the Coming Day

Ask about the most important thing, **you can guess and anticipate**.

**Evening daily sync**: Plan tomorrow
**Morning daily sync**: Plan today

**Guessing approach**:
```
Continue working on the resume tomorrow?

I see you have a paper due Friday and the resume in progress. The paper is more time-sensitive — want to push the paper first tomorrow?
```

**Can also give time options**:
```
How much time do you want to set aside for the main focus? 2 hours for something tighter, 3 hours for more relaxed?
```

### Step 3: Scan Upcoming Deadlines

**Check both calendar and task list** for items coming due soon.

Based on user's chosen classification method, check corresponding high-priority categories:
- **MoSCoW method**: Check Must category for upcoming/overdue items
- **1-3-5 method**: Check big task candidates for upcoming items
- **Eisenhower method**: Check Q1 (Urgent & Important)

**Example**:

```
I checked and found a few upcoming deadlines:

- Assignment email submission — was due yesterday
- Pick up package — expires today if not picked up

When will you do these?
```

### Step 4: Create Timed Reminders

After user confirms times for small deadline items, **create reminders immediately** and confirm "set".

```
✅ Set:
- 15:30 reminder: Submit assignment
- 20:00 reminder: Pick up package
```

### Step 5: Confirm Fixed Schedule

**If already visible from calendar**, just confirm:

```
I see these fixed commitments tomorrow:

- 14:00-15:30 Mathematical Statistics
- 16:00-18:30 Company task

Anything else?
```

**If not visible**, then ask:
```
Any fixed commitments tomorrow? Classes, meetings, etc.?
```

### Step 6: Fill Free Time

Calculate remaining time, ask when to schedule main focus tasks.

```
Looking at remaining time:

- 18:30-20:00 Dinner
- After 20:00 is free

When do you want to schedule the main focus (resume writing)?
```

### Step 7: If Large Gaps Remain, Recommend Exploration Items

After main focus tasks are scheduled, if calendar still has large gaps, recommend exploration items.

Based on classification method, check corresponding categories:
- **MoSCoW method**: Recommend from Could category
- **1-3-5 method**: Recommend from small task candidates
- **Eisenhower method**: Recommend from Q2 (long-term value tasks)

```
There's still a small gap open. There are a few items in exploration — want to schedule one?

- Schedule Management Agent
- AI Social Product Research
```

---

## Daily Sync Complete Example

**Assistant**:

> How's the resume coming? Did you finish a draft?

**User**: It's okay, I wrote some but didn't finish. Continuing today.

**Assistant**:

> Got it. Continuing on the resume today — how much time do you want to set aside? 2 hours for something tighter, 3 hours for more relaxed?

**User**: 2 hours. Hope to finish a draft.

**Assistant**:

> Understood, 2 hours on resume writing, goal is to finish a draft.
>
> I checked and found a few upcoming deadlines:
>
> - ⚠️ Assignment email submission: Was due yesterday
> - ⚠️ Pick up package: Expires today if not picked up
>
> When will you do these?

**User**: Assignment after class, package in the evening.

**Assistant**:

> ✅ Set:
> - 15:30 reminder: Submit assignment
> - 20:00 reminder: Pick up package
>
> I see these fixed commitments today:
>
> - 14:00-15:30 Mathematical Statistics
> - 16:00-18:30 Company task
>
> Anything else?

**User**: No, nothing else.

**Assistant**:

> Got it. Today's schedule:
>
> - 14:00-15:30 Mathematical Statistics
> - 15:30 ⏰ Reminder: Submit assignment
> - 16:00-18:30 Company task
> - 18:30-20:00 Dinner
> - 20:00 ⏰ Reminder: Pick up package
>
> After 20:00 is free. When do you want to schedule resume writing?

**User**: 21:00-23:00.

**Assistant**:

> ✅ Calendar updated: 21:00-23:00 Resume writing
>
> There's still 20:30-21:00 open. Want to schedule something from exploration?

**User**: 20:30-21:00 do Pause Lab exercises.

**Assistant**:

> ✅ Added.
>
> **Today's schedule confirmed**:
>
> - 14:00-15:30 Mathematical Statistics
> - 15:30 ⏰ Reminder: Submit assignment
> - 16:00-18:30 Company task
> - 18:30-20:00 Dinner
> - 20:00 ⏰ Reminder: Pick up package
> - 20:30-21:00 Pause Lab
> - 21:00-23:00 Resume writing
>
> All good?

**User**: All good.

**Assistant**:

> Alright, daily sync complete.

---

## Cron Job Message Template

Cron job messages are sent to **OpenClaw**, not directly to users.

**⚠️ Opening message should be based on specific items!**

```bash
pnpm openclaw cron add \
  --name "Daily Sync" \
  --cron "30 21 * * *" \
  --tz "Asia/Shanghai" \
  --message "[Daily Sync Reminder]

It's time for daily sync.

Please execute schedule-everyday skill's daily sync flow.

⚠️ Important:
1. First read user config: ~/.openclaw/workspace/skills/schedule-everyday/config.yaml
2. Then read task list (Feishu doc token in config's storage.feishu_doc_token)
3. Also check Feishu calendar to understand today's fixed schedule
4. Must read latest content before updating task list
5. Then follow this flow document

Send opening message directly to user (don't say anything like "received"):

⚠️ Opening message should be based on user's specific items, don't ask "How was your day?" — too open-ended!

Examples:
- If yesterday's main focus was resume: "How's the resume coming? Did you finish a draft?"
- If yesterday's main focus was paper: "How's the paper revision going? Can you submit today?"
- If you don't know what was done yesterday: "What did you do yesterday? Did you complete the main focus?"" \
  --channel feishu \
  --to "ou_xxx" \
  --announce
```
