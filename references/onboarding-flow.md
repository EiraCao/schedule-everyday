# Onboarding Flow

## Triggers

1. **First-time use**: Config file doesn't exist
2. **User request**: User says any of these phrases:
   - "setup preferences"
   - "configure schedule"
   - "initialize"
   - "reset"

---

## Flow Overview

```
Step 1: Collect recent tasks → Create document
Step 2: Choose classification method
Step 3: Set daily/weekly sync times
Step 4: Calendar color setup
Step 5: Medium/long-term goals
Step 6: Confirm → Create cron jobs + Test calendar write
Step 7: Complete
```

---

## Detailed Flow

### Step 1: Collect Recent Tasks

**Question**:
```
Tell me a few things you've been working on lately. Just say whatever comes to mind.
(This task list will be maintained long-term, add and archive anytime)
```

**Processing**:
- Organize user's input
- Extract key items
- Prepare for classification display
- **Immediately create document** (see "Document Creation" section)
- Grant user full_access permission

---

### Step 2: Choose Classification Method

**Question**:
```
I offer a few classification methods. You can see how your items would look under each:

(⚠️ Below is just a preview — you decide the final category for each item)

【Method A】MoSCoW (Recommended)
- [Item 1] → Must (Must do)
- [Item 2] → Should (Should do)
- [Item 3] → Could (Could do)
...
Feature: Forces trade-offs, simple and intuitive

【Method B】1-3-5 Rule
- [Item 1] → Big task
- [Item 2] → Medium task
- [Item 3] → Small task
...
Feature: Quantity control, 1 big + 3 medium + 5 small per day

【Method C】Eisenhower Matrix
- [Item 1] → Q1 Urgent & Important
- [Item 2] → Q2 Not Urgent but Important
...
Feature: Introduces time dimension

Which one do you prefer?
```

**Key points**:
- Clarify this is just a preview; user can adjust each item's category
- Provide recommendation
- User can also customize categories

---

### Step 3: Daily/Weekly Sync Times

**Question**:
```
At a fixed time each day, I'll check in with you to review the past day and plan the coming day, helping you focus on main tasks and reminding you of upcoming deadlines.

Same idea for weekly — a fixed time each week to review and plan.

What time for daily sync?
- A. 8:00 AM (plan the day)
- B. 9:00 PM (plan tomorrow)
- C. Let me specify

What time for weekly sync?
- A. Sunday evening
- B. Monday morning
- C. Let me specify

(If you really don't want a certain sync, just tell me)
```

**Key points**:
- Don't ask "if needed" — default to yes
- Downplay the "skip" option (mention in parentheses)
- After confirming time, **don't create cron jobs yet** — wait until Step 6

---

### Step 4: Calendar Color Setup

**Explanation**:
```
After daily and weekly sync, I'll write the schedule to your calendar for easy viewing.

For calendar colors, based on what you mentioned earlier, I recommend categorizing by "domain":
```

**Question** (based on user's items, example below):
```
- Work → 🔴 Red
- Study → 🟣 Purple
- Content → 🩵 Cyan
- Exercise → 🟠 Orange
- Errands → ⚫ Gray

Does this color scheme work? Any adjustments?
(Can also categorize by priority, use default blue, or skip calendar entirely — just let me know)
```

**Key points**:
- Default to calendar sync, don't ask "if needed"
- Colors by **domain/project** (work, study, etc.), not by priority
- Recommend based on user's earlier items
- Downplay other options

---

### Step 5: Medium/Long-term Goals

**Question**:
```
Tell me your medium and long-term goals.

This ensures you spend time on your main goals. Weekly sync will check if you're drifting.

Goals will appear in your task list, so you can see if what you're doing connects to your goals.

If you don't have clear goals yet, just mention what you're focusing on and possible long-term goals. I'll help extract them.

Say as much or as little as you want — can adjust anytime.

What goals do you have? Which are more important? (say "this one's important" to mark)
```

**Processing**:
- User might say many things
- Extract 2-4 medium/long-term goals
- Mark goals user says are "important" with `*`

---

### Step 6: Confirm Goals

**Display**:
```
I extracted these goals (* marks important ones):

1. *[Goal 1]
2. *[Goal 2]
3. [Goal 3]

Does this look right? Feel free to edit directly.
(Goals can be changed anytime in conversation, don't worry)

---

After confirmation, I'll:
1. Create daily and weekly sync cron jobs
2. Test calendar write

Please wait a moment...
```

### **Post-Step6 Confirmation Actions**: (see following sections for details)

1. **Test calendar write**
2. **Create Feishu document**
3. **Create cron jobs** (daily + weekly sync)
4. **Update config file**

**Calendar write methods**:

**Method 1 (Default)**: OpenClaw creates events on its own calendar, user subscribes
1. Create test event on OpenClaw calendar
2. Grant user **edit permission** (not just view permission)
3. Tell user: Check "OpenClaw" in Feishu calendar sidebar under "Subscribed Calendars"
4. User can now view and edit these events

**Method 2**: Write directly to user's calendar (requires authorization)
- Requires user to pre-authorize OpenClaw to access their calendar
- More complex configuration, generally not recommended

**Failure handling**:
- If calendar write fails → Tell user "Calendar write failed, please check Feishu app calendar permission configuration"
- Continue with other flows, don't block entire onboarding due to calendar failure

---

### Step 7: Complete

**Display**:
```
✅ Setup complete!

- Classification: [User's choice]
- Daily sync: Every day at xx:xx ✅ Cron job created
- Weekly sync: Every [day] at xx:xx ✅ Cron job created
- Calendar: ✅ Test write successful
  - Check "OpenClaw" in Feishu calendar sidebar
- Task list: [Document link] ✅ Full access granted

💡 Tip: Pin the task list in chat for easy access
(Top of chat → Add tab → Select task list)

Let me know if anything needs changing.

Whenever you have something to add, just tell me — I'll update the task list.
```

---

## Test Feishu Calendar Write
- Create a test event on OpenClaw calendar
- Grant user **edit permission** (not just view permission) for OpenClaw calendar
- Tell user: Check "OpenClaw" in Feishu calendar sidebar under "Subscribed Calendars". On mobile, tap the calendar icon in the top right corner of the calendar view.

**Calendar write methods**:

**Method 1 (Recommended)**: OpenClaw creates events on its own calendar, user subscribes
- Grant user edit permission (not just view permission)
- User subscribes to OpenClaw calendar in Feishu sidebar

**Method 2**: Write directly to user's calendar (requires authorization)
- Requires user to pre-authorize OpenClaw to access their calendar
- More complex configuration, generally not recommended

**Failure handling**:
- If calendar write fails → Tell user "Calendar write failed, please check Feishu app calendar permission configuration"
- Continue with other flows, don't block entire onboarding due to calendar failure

---

## Document Creation

After Step 1, immediately create the document:

### Steps

```
1. Call feishu-doc create action (only creates empty document)
2. After getting doc_token, call append or write action to write content
3. After content written successfully, call feishu-perm to grant user full_access
4. Return document link to user
```

Note: For table operations, use `write_table_cells` to rewrite entire table content (add/delete rows not available).

### Failure Handling

| Situation | Action |
|-----------|--------|
| feishu-doc unavailable | Tell user "Cannot create document, check feishu skill config" |
| Content write failed | Tell user "Document created but content write failed, please edit manually" |
| Permission setting failed | Tell user "Document created, please manually request edit permission" |

---

## Creating Cron Jobs

After Step 6 confirmation, use OpenClaw cron to create jobs.

### Important Notes

Cron messages are sent to **OpenClaw**, not directly to users. OpenClaw receives the message and needs to:

1. Know which sync flow to execute
2. Follow the corresponding flow document
3. Send opening message directly to user (no "received" transition words)

### Daily Sync Cron Template

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
4. Follow schedule-everyday skill's references/daily-sync-flow.md

Send opening message directly (no transition words):

Opening message should be specific to user's tasks, not too open-ended.
Example: \"How's the resume going? Finished a draft?\" or \"What's the plan for today? I see you have a paper due Friday and resume in progress.\"" \
  --channel feishu \
  --to "ou_xxx" \
  --announce
```

### Weekly Sync Cron Template

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
3. Check Feishu calendar for this week's fixed schedule
4. Follow schedule-everyday skill's references/weekly-sync-flow.md

Send opening message directly (no transition words):

📅 Weekly sync time.

Check medium-term goals — how's progress?

[Display goals table from config.goals field]" \
  --channel feishu \
  --to "ou_xxx" \
  --announce
```

---

## Config Save

### Config File Path

`~/.openclaw/workspace/skills/schedule-everyday/config.yaml`

### Resume Mechanism

Update `onboarding_status` after each key step:

```yaml
onboarding_status: "pending_step3"  # or pending_step4 / pending_step5 / completed
```

### Final Config

```yaml
version: "1.0"
created_at: "YYYY-MM-DD"
onboarding_status: "completed"

classification: "moscow"  # moscow / 1-3-5 / eisenhower

daily_sync:
  enabled: true
  time: "21:30"

weekly_sync:
  enabled: true
  day: "sunday"
  time: "19:00"

calendar:
  enabled: true
  color_by: "domain"  # domain / priority / none
  color_mapping:
    "Work": -562844
    "Study": -7120138
    "Content": -16722247
    "Exercise": -30720
    "Errands": -6511959

goals:
  - name: "Goal 1"
    important: true
  - name: "Goal 2"
    important: false

storage:
  feishu_doc_token: "xxx"
  feishu_calendar_id: "openclaw"
  local_path: "~/.openclaw/workspace/skills/schedule-everyday/tasks.md"
```
