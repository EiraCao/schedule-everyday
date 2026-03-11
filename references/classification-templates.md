# Classification Templates Explained

This document introduces 3 task classification templates and their application in daily/weekly syncs.

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

## Classification Template Selection Guide

| If you are... | Recommended template |
|---------------|---------------------|
| Treating everything as "important" | MoSCoW |
| Tending to over-plan | 1-3-5 Technique |
| Needing to learn to say no | Eisenhower Matrix |
| Having your own preferred method | Custom |

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
