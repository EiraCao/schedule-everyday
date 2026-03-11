# Schedule Everyday

English | [简体中文](./README.md)

A skill designed to **reduce cognitive load**. Users just need to "decide" — Schedule Everyday handles the thinking and organizing like a personal secretary.

## Features

- **Onboarding** — Guide users to set up classification method, calendar config, and goals
- **Daily Sync** — Identify main tasks, scan upcoming deadlines, confirm schedule
- **Weekly Sync** — Review goals, reflect on last week, plan this week's priorities
- **Task Management** — Add/update/archive tasks

## Trigger Phrases

- Daily sync: "align", "today's plan", "daily sync", "日对齐"
- Weekly sync: "weekly sync", "this week", "周对齐"
- Task management: "add task", "show my list", "添加事项"
- Setup: "setup preferences", "initialize", "初始化"

## Classification Methods

Supports 3 classification styles:

| Method | Key Feature | Best For |
|--------|-------------|----------|
| **MoSCoW** (Recommended) | Forces prioritization, 4 simple tiers | Users who treat everything as "important" |
| **1-3-5 Rule** | Quantity control, 1+3+5 tasks per day | Users who tend to over-plan |
| **Eisenhower Matrix** | Time dimension, 4 quadrants | Users who need to learn to say no |

## Installation

### OpenClaw

```bash
cd ~/.openclaw/workspace/skills/
git clone https://github.com/EiraCao/schedule-everyday.git
```

### Claude Code

```bash
cd ~/.claude/skills/
git clone https://github.com/EiraCao/schedule-everyday.git
```

## File Structure

```
schedule-everyday/
├── SKILL.md                      # Main skill file
├── README.md                     # Chinese documentation
├── README.en.md                  # English documentation (this file)
├── references/
│   ├── onboarding-flow.md        # Onboarding flow (Chinese)
│   ├── daily-sync-flow.md        # Daily sync flow (Chinese)
│   ├── weekly-sync-flow.md       # Weekly sync flow (Chinese)
│   └── classification-templates.md
│   └── en/                       # English flow docs
│       ├── onboarding-flow.md
│       ├── daily-sync-flow.md
│       ├── weekly-sync-flow.md
│       └── classification-templates.md
└── assets/
    └── config_template.yaml      # Config template
```

## Core Principles

1. **Small questions + Options** — Ask one question at a time, provide 2-4 choices
2. **Non-judgmental tone** — Be supportive, no pressure, avoid "you should"
3. **Read before write** — Always read the latest content before updating the task list

## License

MIT
