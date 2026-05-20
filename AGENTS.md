# 诸天音综系统框架 — Agent 指南

## 项目定位

这是一个以"我"为主视角、由播放量升级系统驱动的 AI 角色内容宇宙。把神话、历史和大众熟知角色沉淀为可复用的角色内容包，再组合成小说剧情、音乐 MV、短视频切片、综艺 Battle 和全民音综事件。

**核心公式**：角色内容包 + 导演系统 + AI 制作能力 + 播放量结算 = 可持续扩展的角色内容宇宙

## 目录结构

```
framework/              ← 框架设计文档（源）
  modules/              ← 10 个核心模块
    01-world-system.md
    02-character-package.md
    03-director-system.md
    04-production-pipeline.md
    05-agent-map.md
    06-business-later.md
    07-external-tools-integration.md  ← 工具与服务集成计划书
    08-quality-review.md             ← 框架质量评估系统（评级 Agent）
    09-narrative-engine.md           ← 叙事引擎（五拍弧线）
    10-audience-system.md            ← 观众与社区系统
  templates/            ← 5 个可复用模板
    character-package-template.md
    director-beat-template.md
    episode-package-template.md
    system-settlement-template.md
    iteration-log-template.md        ← 内容迭代日志
  operations/           ← 运营文档
    roadmap.md
    risk-register.md                 ← 风险登记册

specs/                  ← 功能规格（speckit 工作流）
  001-ai-music-mv-workflow/
    spec.md, plan.md, tasks.md, ...

outputs/                ← 实际产出物
  characters/           ← 角色内容包实例
    sun-wukong/         ← 孙悟空角色包（已填写）
    _template/          ← 空白模板副本

.claude/skills/         ← 外部 AI 技能（待安装）
    evolink-media/      ← 一站式媒体生成 API（60+ 模型）
    ai-music-video/     ← 端到端 MV 合成
    evolink-music/      ← Suno 音乐生成
    evolink-video/      ← 视频生成
```

## 工具与服务

### 已规划的外部工具（详见模块 07）

| 工具 | 用途 | 状态 |
|------|------|------|
| evolink-media | 统一 API 网关（音乐/图片/视频） | 计划安装 |
| ai-music-video | MV 合成（Suno + ffmpeg） | 计划安装 |
| evolink-music | Suno v5 音乐生成 | 按需安装 |
| evolink-video | 图→视频生成 | 按需安装 |
| storyboard-consistent-character | 角色一致性架构参考 | GitHub 研究 |

### AI 模型能力（API 层）

- **音乐**：Suno v5, Suno v4.5
- **图片**：Flux, Seedream, GPT Image
- **视频**：Kling 3.0, Seedance, Veo 3, Sora
- **合成**：ffmpeg + SRT 字幕

## 工作约定

- 先读 `.specify/memory/constitution.md` 了解 7 条基本原则
- 先在 `framework/templates/` 找是否有现成模板可用
- 昂贵生成动作前必须先过文字审核门禁
- 所有产出物放到 `outputs/` 下对应目录
- 使用外部工具前，查阅 `framework/modules/07-external-tools-integration.md` 确认对应环节的推荐工具
