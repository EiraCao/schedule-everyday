# Classification Templates Explained

This document introduces 4 task classification templates and their application in daily/weekly syncs.

---

## Template A: MoSCoW (Recommended)

### When to Use

Suitable for users who need to force trade-offs, especially:
- Users who tend to treat everything as "important"
- Need clear priority judgment
- Want a simple and intuitive classification method

### Classification Structure

```
Tasks
├── Must (Must do)
│   └── Serious consequences if not done
│   └── Must complete today
├── Should (Should do)
│   └── Beneficial if done
│   └── Try to complete today
├── Could (Could do)
│   └── Do if time permits
│   └── Okay if not done
└── Won't (Won't do)
    └── Not doing for now
    └── Put in Someday/Maybe
```

### Daily Sync Processing Logic

```
1. Scan Must category, confirm today's Must items
2. Focus on Must tasks as the day's main focus
3. After Must is complete, handle Should, do Could if energy remains
4. Won't tasks are automatically filtered

Reminder mechanism:
- More than 5 Must tasks → "Today might be overloaded"
- No Must tasks → "No main focus tasks today?"
```

### Weekly Sync Processing Logic

```
Task pool cleanup:
- Check Could/Won't categories
- Could items untouched for a while → Ask user if still want to do
- Won't can be periodically cleaned
```

### Task List Format

```markdown
## Must (Must do)

| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Thesis draft | Today | Todo | |

## Should (Should do)

| Task | Status | Notes |
|------|--------|-------|
| Interview prep | Todo | This week |

## Could (Could do)

| Task | Notes |
|------|-------|
| Organize bookshelf | If time permits |

## Won't (Not now)

| Task | Notes |
|------|-------|
| Learn Rust | Consider later |
```

### Color Recommendations

| Category | Color | Feishu color value |
|----------|-------|-------------------|
| Must | Red | -562844 |
| Should | Orange | -30720 |
| Could | Green | -13318364 |
| Won't | Gray | -6511959 |

---

## Template B: 1-3-5 Technique

### When to Use

Suitable for users who need to control workload, especially:
- Users who tend to over-plan
- Need clear daily task quantity limits
- Want automatic time estimation

### Classification Structure

```
Daily task allocation:
├── Big task × 1 (3-4 hours)
│   └── Work requiring deep focus
│   └── The day's most important task
├── Medium task × 3 (1-2 hours)
│   └── Items requiring some time
│   └── May have time constraints
└── Small task × 5 (<1 hour)
    └── Quickly completed items
    └── Chores, replying to messages, etc.

Total approximately 8 hours
```

### Daily Sync Processing Logic

```
1. Select today's 1+3+5 tasks from task pool
2. First select big task (the day's most important thing)
3. Then select medium tasks (3 items)
4. Finally select small tasks (5 items)
5. Hard constraint on quantity, finishing means winning

Reminder mechanism:
- More than 1 big task → "Are you sure you can complete this many big tasks today?"
- More than 9 total tasks → "Today might be overloaded"
```

### Weekly Sync Processing Logic

```
Task pool cleanup:
- Check items in task pool that haven't moved in a while
- Too many big task candidates → Help user break down or prioritize
- Small task backlog → Suggest batch processing
```

### Task List Format

```markdown
## Task Pool

### Big Task Candidates (3-4h)

| Task | Status | Notes |
|------|--------|-------|
| Complete product proposal | Todo | Needs deep focus |

### Medium Task Candidates (1-2h)

| Task | Status | Notes |
|------|--------|-------|
| Write weekly report | Todo | |
| Interview prep | Todo | |

### Small Task Candidates (<1h)

| Task | Notes |
|------|-------|
| Reply to emails | |
| Book dentist appointment | |

## Today's Plan

**Big task**: [Task]

**Medium tasks**:
1. [Task]
2. [Task]
3. [Task]

**Small tasks**:
1. [Task]
...
```

### Color Recommendations

| Category | Color | Feishu color value |
|----------|-------|-------------------|
| Big task | Red | -562844 |
| Medium task | Orange | -30720 |
| Small task | Green | -13318364 |

---

## Template C: Eisenhower Matrix

### When to Use

Suitable for users who need to introduce a time dimension, especially:
- Easily overwhelmed by urgent matters
- Need to learn to say no
- Want to develop a long-term perspective

### Classification Structure

```
Tasks
├── Q1 Urgent & Important (Do First)
│   └── Handle immediately
│   └── Usually crises, deadlines
├── Q2 Not Urgent but Important (Schedule)
│   └── Plan time blocks
│   └── This is where improvement-focused goals live
│   └── Main source of main focus tasks
├── Q3 Urgent but Not Important (Delegate)
│   └── Try to delegate or handle quickly
│   └── Warning: Don't let these occupy too much time
└── Q4 Not Important, Not Urgent (Eliminate)
    └── Consider deleting
    └── Or put in Someday/Maybe
```

### Daily Sync Processing Logic

```
1. Q1 (Urgent & Important): Handle first
2. Q2 (Not Urgent but Important): Main focus task candidates, schedule time blocks
3. Q3 (Urgent but Not Important): Check if receiving too much attention
4. Q4 (Not Important, Not Urgent): Suggest deleting or put in someday

Long-term cultivation: Help user spend more time in Q2
```

### Weekly Sync Processing Logic

```
Task pool cleanup:
- Check Q3/Q4 categories
- Lots of Q3 → Help user identify what can be declined
- Q4 can be periodically cleaned
- Check if Q2 is receiving enough attention
```

### Task List Format

```markdown
## Q1 Urgent & Important

| Task | Deadline | Status |
|------|----------|--------|
| Thesis proposal | Today | In progress |

## Q2 Not Urgent but Important

| Task | Suggested time | Status |
|------|----------------|--------|
| Schedule management system | 10 hours/week | In progress |

## Q3 Urgent but Not Important

| Task | Deadline | How to handle |
|------|----------|---------------|
| Labor education course | 3/12 | Complete by Wednesday |

## Q4 / Someday

| Task | Notes |
|------|-------|
| Learn Rust | Want to learn later |
```

### Color Recommendations

| Category | Color | Feishu color value |
|----------|-------|-------------------|
| Q1 Urgent & Important | Red | -562844 |
| Q2 Not Urgent but Important | Purple | -7120138 |
| Q3 Urgent but Not Important | Orange | -30720 |
| Q4 Not Important, Not Urgent | Gray | -6511959 |

---

## Template D: MoSCoW + Exploration

### When to Use

Suitable for users who want to protect creative ideas without pressure, especially:
- Users with many "someday" ideas that don't fit into priorities
- Users who feel overwhelmed by long to-do lists
- Users who want to separate "must deliver" from "exploratory"

### Classification Structure

```
Tasks
├── Must (Must do)
│   └── Serious consequences if not done
├── Should (Should do)
│   └── Beneficial if done
├── Could (Could do)
│   └── Do if time permits
└── Someday / Exploration
    └── No commitment to output
    └── Creative ideas, learning interests
    └── Can be moved to other categories anytime
```

### Key Feature

**Exploration items have no commitment to output**. This protects creative ideas without the pressure of a long to-do list. When you commit to producing something, they can be moved to other categories at any priority level.

### Task List Format

```markdown
## Must (Must do)

| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Thesis draft | Today | Todo | |

## Should (Should do)

| Task | Status | Notes |
|------|--------|-------|
| Interview prep | Todo | |

## Could (Could do)

| Task | Notes |
|------|-------|
| Organize bookshelf | |

## Someday / Exploration

| Task | Notes |
|------|-------|
| Learn Rust | When time permits |
| Start a podcast | Interesting idea |
```

### Color Recommendations

Same as MoSCoW, with Exploration using Gray or Cyan.

---

## Classification Template Selection Guide

| If you are... | Recommended template |
|---------------|---------------------|
| Treating everything as "important" | MoSCoW |
| Tending to over-plan | 1-3-5 Technique |
| Needing to learn to say no | Eisenhower Matrix |
| Having your own preferred method | Custom |

---

## Why These Classification Methods Are Recommended

### MoSCoW Method (First Recommendation)

**Core Advantages**:
- Most simple and intuitive: M/S/C is easy to understand at a glance
- Forces trade-offs: Avoids the trap of "all tasks are high priority"
- Daily sync friendly: Quickly mark each day, focus on M tasks

**Best For**:
- Users who need forced trade-off decisions (tend to treat everything as "important")
- Moderate task volume, 5-15 to-do items per day
- Users easily overwhelmed by trivia, need to focus on main thread

**Example Application**:
User says: "I need to write a paper, learn English, help a friend revise their resume, and there are some small things"

MoSCoW classification:
- M: Write paper (draft due tomorrow, must complete today)
- S: Learn English (daily habit, important but can reduce time today)
- S: Help friend revise resume (promised by Friday)
- C: Some small things (organize desk, reply to non-urgent emails)

### 1-3-5 Technique (Second Recommendation)

**Core Advantages**:
- Quantity control: Forces "9 tasks", avoiding over-planning
- Time awareness: Automatically provides time estimation (3h+4.5h+2.5h≈8h)
- Easy to execute: Just these 9 per day, completing means winning

**Best For**:
- Users who tend to over-plan, list 20+ to-dos daily but can't finish
- Users needing time perception training (inaccurate task duration estimation)

### Eisenhower Matrix (Third Recommendation)

**Core Advantages**:
- Introduces time dimension: "Urgency" is a dimension other methods don't have
- Long-term perspective cultivation: Emphasizes value of Q2 (not urgent but important)
- Rejection training: Helps users identify Q3/Q4 and learn to say no

**Best For**:
- Users easily led around by "urgent" matters
- Users needing to cultivate long-term perspective
- Users with many work interruptions, needing to learn refusal

### How to Choose

| If you are... | Recommended template |
|---------------|---------------------|
| Treating everything as "important" | MoSCoW |
| Tending to over-plan | 1-3-5 Rule |
| Needing to learn to say no | Eisenhower Matrix |

---

## Feishu Calendar Color Reference

| Color | Feishu color value |
|-------|-------------------|
| Red | -562844 |
| Orange | -30720 |
| Green | -13318364 |
| Cyan | -16722247 |
| Purple | -7120138 |
| Gray | -6511959 |
| Blue | -14329888 |
| Yellow | -263804 |
| Pink | -963671 |
| Light yellow | -14838 |
| Pure blue | -1 |
| Light blue | -15417089 |
| Dark blue | -10392859 |
| Magenta | -3066159 |
