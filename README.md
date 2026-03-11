# Schedule Everyday

简体中文 | [English](https://github.com/EiraCao/schedule-everyday/tree/en)

> "忙了一天，但好像什么都没做完？""总觉得有件事忘了，但想不起来是什么？"

这是一个「数字秘书」skill，核心目标是**减少认知负担**。
- **① 长期维护一个飞书内的事项清单文档**，随时记录整理你的任何事项或灵感；
- **② 每天和每周主动找你对齐**，帮你把精力放到主线目标上，对临期事项设置定时提醒、自动同步飞书日历。
建议使用 OpenClaw + 飞书，如果用 Claude Code 需要想办法连接飞书，否则看不到自己的全部事项清单文档。

## 功能
- **Onboarding** — 5 分钟完成初始化，按照你的偏好自由选择事项分类方式、每日对齐/每周对齐的时间、日历颜色方案等。
- **日对齐** — — 每天固定时间（如早上 8:30 或晚上 21:30）主动扫描日历和事项清单，向你确认主线任务、提醒临期事项、并同步飞书日历。
- **周对齐** — 每周日/一回顾上周完成度，帮助你把精力放在实现中长期目标的事项上，规划主线任务、确保给重要事项预留了事件、排入固定习惯（运动、阅读等）。
- **事项管理** — 添加/更新/归档事项。“把球打出去”，任何突然的ddl、班群的提醒、主任的要求，或者自己的灵感，随时丢给，就会自动记录到；支持升级/降级优先级、归档已完成事项。

## 不同的优先级分类方式

支持 3 种分类：

| 方式 | 适合这样的你 | 核心感觉 |
|------|------------|----------|
| **MoSCoW** | 容易把所有事都当"重要" | 强制取舍：Must 不做会死，Should 做了更好，Could 有空再说 |
| **1-3-5 技术** | 容易列 20 条待办然后崩溃 | 数量硬约束：每天 1 个大石头 + 3 个中任务 + 5 个小琐事，完成就赢了 |
| **Eisenhower 矩阵** | 总被别人的急事打断 | 区分"紧急"和"重要"：帮你把更多时间花在真正重要的事上（Q2） |
也可以自由选择任务的优先级划分方式。

## 安装

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

## 文件结构

```
schedule-everyday/
├── SKILL.md                      # Skill 主文件
├── README.md                     # 中文文档（本文件）
├── references/
│   ├── onboarding-flow.md        # Onboarding 流程
│   ├── daily-sync-flow.md        # 日对齐流程
│   ├── weekly-sync-flow.md       # 周对齐流程
│   └── classification-templates.md # 分类模板
└── assets/
    └── config_template.yaml      # 配置模板
```

## License

MIT
