# Schedule Everyday

[English (en branch)](https://github.com/EiraCao/schedule-everyday/tree/en) | 简体中文

一个「数字秘书」skill，核心目标是**减少认知负担**。用户只需「拍板」，思考和整理由秘书完成。

## 功能

- **Onboarding** — 引导设置分类方式、日历配置、中长期目标
- **日对齐** — 确定主线任务、扫描临期事项、确认日程
- **周对齐** — 目标回顾、上周回顾、本周主线、习惯排期
- **事项管理** — 添加/更新/归档事项

## 触发词

- 日对齐：「对齐一下」「今天安排」「日对齐」「daily sync」
- 周对齐：「周对齐」「weekly sync」「这周安排」
- 事项管理：「添加事项」「记录一个事情」「看看我的清单」
- 设置：「设置日程偏好」「初始化日程」

## 分类方式

支持 3 种分类：

| 方式 | 特点 | 适合 |
|------|------|------|
| **MoSCoW**（推荐） | 强制取舍，4 档简单直观 | 容易把所有事当「重要」的用户 |
| **1-3-5 技术** | 数量控制，每天 1+3+5 | 容易过度规划的用户 |
| **Eisenhower 矩阵** | 引入时间维度，四象限 | 需要学会拒绝的用户 |

## 安装

### OpenClaw（中文版）

```bash
cd ~/.openclaw/workspace/skills/
git clone https://github.com/EiraCao/schedule-everyday.git
```

### OpenClaw（English version）

```bash
cd ~/.openclaw/workspace/skills/
git clone -b en https://github.com/EiraCao/schedule-everyday.git
```

### Claude Code（中文版）

```bash
cd ~/.claude/skills/
git clone https://github.com/EiraCao/schedule-everyday.git
```

### Claude Code（English version）

```bash
cd ~/.claude/skills/
git clone -b en https://github.com/EiraCao/schedule-everyday.git
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

## 核心原则

1. **小问题 + 给选项** — 每次只问一个问题，提供 2-4 个选项
2. **非评判语气** — 关心支持，不给压力，不说「你应该」
3. **先读再写** — 更新事项清单前，必须先读取最新内容

## License

MIT
