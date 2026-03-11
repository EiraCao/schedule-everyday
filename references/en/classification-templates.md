# Classification Templates Explained

This document introduces 3 task classification templates and their application in daily/weekly sync.

---

## Template A: MoSCoW (Recommended)

### Use Cases

Suitable for users who need forced prioritization, especially:
- Users who treat everything as "important"
- Need clear priority judgment
- Want simple, intuitive classification

### Structure

```
Tasks
├── Must (Must do)
│   └── Serious consequences if not done
│   └── Must complete today
├── Should (Should do)
│   └── Benefits if done
│   └── Try to complete today
├── Could (Could do)
│   └── Do if time permits
│   └── No problem if not done
└── Won't (Won't do)
    └── Not doing for now
    └── Put in Someday/Maybe
```

### Daily Sync Logic

```
1. Scan Must category, confirm today's Must items
2. Focus on Must tasks as today's main line
3. After Must complete, handle Should, do Could if time
4. Won't tasks automatically filtered

Reminder mechanism:
- More than 5 Must tasks → "Today might be overloaded"
- No Must tasks → "No main task today?"
```

### Weekly Sync Logic

```
When cleaning task pool:
- Check Could/Won't categories
- Long-untouched Could → Ask user if still interested
- Won't can be periodically cleaned
```

### Task List Format

```markdown
## Must (Must do)

| Task | Deadline | Status | Notes |
|------|----------|--------|-------|
| Thesis draft | Today | Todo |  |

## Should (Should do)

| Task | Status | Notes |
|------|--------|-------|
| Interview prep | Todo | This week |

## Could (Could do)

| Task | Notes |
|------|-------|
| Organize bookshelf | If time permits |

## Won't (Won't do)

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

## Template B: 1-3-5 Rule

### Use Cases

Suitable for users who need to control workload, especially:
- Users who tend to over-plan
- Need clear daily task quantity limits
- Want automatic time estimation

### Structure

```
Daily task allocation:
├── Big tasks × 1 (3-4 hours)
│   └── Requires deep focus
│   └── Most important task of the day
├── Medium tasks × 3 (1-2 hours)
│   └── Requires some time
│   └── May have deadlines
└── Small tasks × 5 (<1 hour)
    └── Quick to complete
    └── Errands, message replies, etc.

Total ~8 hours
```

### Daily Sync Logic

```
1. Select today's 1+3+5 tasks from task pool
2. First choose big task (most important today)
3. Then choose medium tasks (3 items)
4. Finally choose small tasks (5 items)
5. Hard quantity constraint — complete and win

Reminder mechanism:
- More than 1 big task → "Can you really complete this many big tasks today?"
- More than 9 total tasks → "Today might be overloaded"
```

### Weekly Sync Logic

```
When cleaning task pool:
- Check items untouched for a while
- Too many big task candidates → Help user split or prioritize
- Small task accumulation → Batch processing suggestions
```

### Task List Format

```markdown
## Task Pool

### Big Task Candidates (3-4h)

| Task | Status | Notes |
|------|--------|-------|
| Complete product plan | Todo | Needs deep focus |

### Medium Task Candidates (1-2h)

| Task | Status | Notes |
|------|--------|-------|
| Write weekly report | Todo |  |
| Interview prep | Todo |  |

### Small Task Candidates (<1h)

| Task | Notes |
|------|-------|
| Reply to email |  |
| Schedule dentist |  |

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

### Use Cases

Suitable for users who need to introduce time dimension, especially:
- Overwhelmed by urgent matters
- Need to learn to say no
- Want to cultivate long-term perspective

### Structure

```
Tasks
├── Q1 Urgent & Important (Do First)
│   └── Handle immediately
│   └── Usually crises, deadlines
├── Q2 Not Urgent but Important (Schedule)
│   └── Schedule time blocks
│   └── Where excel-type goals live
│   └── Main source of main tasks
├── Q3 Urgent Not Important (Delegate)
│   └── Delegate or handle quickly
│   └── Warning: Don't let these consume too much time
└── Q4 Not Urgent Not Important (Eliminate)
    └── Consider deleting
    └── Or put in Someday/Maybe
```

### Daily Sync Logic

```
1. Q1 (Urgent & Important): Prioritize
2. Q2 (Not Urgent but Important): Main task candidates, schedule time blocks
3. Q3 (Urgent Not Important): Check if over-attended
4. Q4 (Not Urgent Not Important): Suggest delete or put in someday

Long-term: Help user spend more time in Q2
```

### Weekly Sync Logic

```
When cleaning task pool:
- Check Q3/Q4 categories
- Many Q3 → Help user identify what to refuse
- Q4 can be periodically cleaned
- Check if Q2 gets enough attention
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
| Schedule management system | 10h/week | In progress |

## Q3 Urgent Not Important

| Task | Deadline | Handling |
|------|----------|----------|
| Labor education class | 3.12 | Complete by Wed |

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
| Q3 Urgent Not Important | Orange | -30720 |
| Q4 Not Urgent Not Important | Gray | -6511959 |

---

## Classification Template Selection Guide

| If you are... | Recommended template |
|---------------|---------------------|
| Everything seems "important" | MoSCoW |
| Tend to over-plan | 1-3-5 Rule |
| Need to learn to say no | Eisenhower Matrix |
| Have your own preferred method | Customize |

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
