# 诸天音综系统框架 — Agent 指南

## 项目定位

这是一个以"我"为主视角、由播放量升级系统驱动的 AI 角色内容宇宙。把神话、历史和大众熟知角色沉淀为可复用的角色内容包，再组合成小说剧情、音乐 MV、短视频切片、综艺 Battle 和全民音综事件。

**核心公式**：角色内容包 + 导演系统 + AI 制作能力 + 播放量结算 = 可持续扩展的角色内容宇宙

## 目录结构

```
framework/              ← 框架设计文档（源）
  modules/              ← 6 个核心模块
    01-world-system.md
    02-character-package.md
    03-director-system.md
    04-production-pipeline.md
    05-agent-map.md
    06-business-later.md
  templates/            ← 4 个可复用模板
    character-package-template.md
    director-beat-template.md
    episode-package-template.md
    system-settlement-template.md
  operations/           ← 路线图
    roadmap.md

specs/                  ← 功能规格（speckit 工作流）
  001-ai-music-mv-workflow/
    spec.md, plan.md, tasks.md, ...

outputs/                ← 实际产出物
  characters/           ← 角色内容包实例
```

## 工作约定

- 先读 `.specify/memory/constitution.md` 了解 7 条基本原则
- 先在 `framework/templates/` 找是否有现成模板可用
- 昂贵生成动作前必须先过文字审核门禁
- 所有产出物放到 `outputs/` 下对应目录
