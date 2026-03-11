# Schedule Everyday

English | [简体中文](https://github.com/EiraCao/schedule-everyday)

A skill designed to **reduce cognitive load** — Schedule Everyday handles the thinking and organizing like a personal secretary. Users just need to "decide".

## Features

- **Onboarding** — Guide users to set up classification method, calendar config, and goals
- **Daily Sync** — Identify main tasks, scan upcoming deadlines, confirm schedule
- **Weekly Sync** — Review goals, reflect on last week, plan this week's priorities
- **Task Management** — Add/update/archive tasks

## Trigger Phrases

- Daily sync: "align", "today's plan", "daily sync"
- Weekly sync: "weekly sync", "this week"
- Task management: "add task", "show my list", "what's pending"
- Setup: "setup preferences", "initialize schedule"

## Classification Methods

Supports 3 classification styles:

| Method | Key Feature | Best For |
|--------|-------------|----------|
| **MoSCoW** (Recommended) | Forces prioritization, 4 simple tiers | Users who treat everything as "important" |
| **1-3-5 Rule** | Quantity control, 1+3+5 tasks per day | Users who tend to over-plan |
| **Eisenhower Matrix** | Time dimension, 4 quadrants | Users who need to learn to say no |

## Installation

This solution is designed for **OpenClaw + Feishu** environment.

```bash
cd ~/.openclaw/workspace/skills/
git clone -b en https://github.com/EiraCao/schedule-everyday.git
```

## File Structure

```
schedule-everyday/
├── SKILL.md                      # Main skill file
├── README.md                     # This file
├── references/
│   ├── onboarding-flow.md        # Onboarding flow
│   ├── daily-sync-flow.md        # Daily sync flow
│   ├── weekly-sync-flow.md       # Weekly sync flow
│   └── classification-templates.md # Classification templates
└── assets/
    └── config_template.yaml      # Config template
```

## Core Principles

1. **Small questions + Options** — Ask one question at a time, provide 2-4 choices
2. **Non-judgmental tone** — Be supportive, no pressure, avoid "you should"
3. **Read before write** — Always read the latest content before updating the task list

## License

MIT
