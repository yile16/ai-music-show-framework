# Phase 0.5：工具链验证

> 开始日期：2026-05-20 | 状态：**准备中 — 等待 API Key**

---

## 前置条件

### API Key 注册清单

在开始测试之前，需要注册以下 API Key：

| # | 服务 | 注册地址 | 用途 | 费用 |
|---|------|---------|------|------|
| 1 | **EvoLink** | https://evolink.ai → Dashboard → API Keys | 统一网关：音乐+图片+视频 | 按量付费 |
| 2 | **Suno API** | https://sunoapi.org | 音乐生成（备选方案） | 按量付费 |
| 3 | **OpenAI** | https://platform.openai.com | 图片生成（备选方案） | 按量付费 |

> **推荐**：先只注册 EvoLink（一个 Key 覆盖音乐/图片/视频），Suno API 和 OpenAI 作为备选。

### Key 配置方法

获取 Key 后，在终端执行：

```bash
# EvoLink（主方案）
export EVOLINK_API_KEY="你的key"

# Suno API（备选，如果你想直接调 Suno）
export SUNO_API_KEY="你的key"

# OpenAI（备选）
export OPENAI_API_KEY="你的key"
```

---

## 测试计划

### 测试 1：歌曲生成（验证 Suno 中文歌词可用率）

**目标**：确认 Suno 能否产出"好听的"国风 trap 金属中文歌

**测试 Prompt**（从孙悟空角色包提取）：

```yaml
Style: Chinese folk metal, trap beats, suona intro
Mood: Defiant but weary, powerful and wise
Vocal: Male gritty baritone, controlled rasp
Structure: Suona Intro → Spoken Verse → Build → Chorus → Trap Drop → Verse 2 → Chorus → Bridge whispered → Final Chorus → Outro
Theme: A rebel crushed by heaven, waited 500 years, rose again not to fight gods but to sing for those still buried under their own mountains
Avoid: nursery rhyme melodies, cartoonish sound effects, monkey king cliches
```

**歌词**（准备投喂的）：

```
[Intro - 唢呐 8秒]

[Verse 1 - 低音叙事]
从石头里来的 不需要名字
天说我不配 我自己写了四个字
金箍棒在手 不是为了打
是为了那些 和我一样不说疼的人

[Chorus - 爆发]
天不/容我/我也/没打算被容
五百/年的/天空/就一条缝
如果/你也/被压/在自己的山下
这一/棒是/替你/劈开的雷声

[Verse 2]
火眼金睛 看穿了所有的谎
但看不穿 为什么好人总是受伤
筋斗云翻了十万八千里
翻不出一个人心里的围墙

[Chorus - 更强]
天不/容我/我也/没打算被容
五百/年的/天空/就一条缝
如果/你也/被压/在自己的山下
这一/棒是/替你/劈开的雷声

[Bridge - 低语]
（五行山下 我数过每一道光
五百年的光 加在一起 也没有你的眼睛亮）

[Final Chorus - 全力量]
天不容我 我也没打算被容
五百年的天空 就一条缝
如果你也被压在自己的山下
这一棒是替你 劈开的雷声

[Outro - 唢呐渐弱，一个呼吸声]
```

**成功标准**：
- 10 次生成中至少有 3 首"可以听"的歌
- 至少 1 首的唢呐元素被正确生成
- 中文吐字清晰可辨

**实际结果**：（待测试后填写）

---

### 测试 2：角色定妆照生成（验证视觉锚点能否被正确理解）

**目标**：确认从角色包的视觉锚点 prompt 能生成一致的、有辨识度的角色形象

**测试 Prompt**（从孙悟空角色包提取）：

```
Full body shot of a powerful warrior monk, East Asian features with subtle simian traits. Golden pupils with faint flame inside. Short dark hair, angular face with a thin old scar on right cheek. A ring-shaped faint mark on forehead (like an old indentation). Wearing a black fitted battle suit under weathered dark-gold armor. Deep green burnt cape. Standing barefoot on a rocky mountaintop. Dark iron staff planted in ground next to him, glowing faint gold at the ends. Dark moody lighting, cinematic composition. Staring directly at viewer with a tired but unbroken expression.

Negative: no cartoon, no cute monkey, no red and gold color scheme, no smiling, no animalistic fur face, no Chinese opera face paint, no 1986 TV series reference
```

**多角度测试**：生成 3 张 — 正面、侧面、背面

**成功标准**：
- 3 张中的角色看起来是"同一个人"
- 金色瞳孔、额头印记、右脸疤痕 3 个锚点清晰可见
- 整体氛围"赛博神话"而非"古装剧"或"卡通片"

**实际结果**：（待测试后填写）

---

### 测试 3：图→视频 3 秒片段（验证角色一致性，最关键测试）

**目标**：确认图生视频后角色面部不发生严重变形

**测试方法**：
1. 取测试 2 中最好的一张定妆照作为输入图
2. 用 evolink-video 生成 3 秒视频片段
3. 分别用 Seedance 和 Kling 两种模型测试

**Motion Prompt**：
```
Slow camera push-in on the warrior's face. Wind gently moves his burnt cape. Golden light pulses faintly from the staff. Eyes blink once. Minimal movement, focused on character presence.
```

**成功标准**：
- 视频中角色面部保持可辨识（不变成另一个人）
- 金色瞳孔、额头印记在运镜中不消失/不扭曲
- 至少 1 个模型的产出可用

**实际结果**：（待测试后填写）

---

### 测试 4：成本记录

| 测试项 | API 调用次数 | 单次费用 | 总费用 | 备注 |
|--------|------------|---------|--------|------|
| 歌曲生成 | 10 次 | | | |
| 定妆照 | 5 次（含多角度） | | | |
| 图→视频 | 6 次（3 次×2 模型） | | | |
| **合计** | **21 次** | | **预估 $5-10** | |

---

## 判定标准

| 结果 | 判定 | 后续行动 |
|------|------|---------|
| 全部 3 项测试通过 | ✅ 绿灯 | 进入 Phase 1，按原计划全动态视频方向 |
| 歌曲+定妆照通过，视频失败 | ⚠️ 黄灯 | 进入 Phase 1，但分镜方向降级为 Slideshow + 运镜模式 |
| 歌曲或定妆照失败 | ⚠️ 黄灯 | 调整 prompt 后再测一次；如果连续 2 次失败则调整方案 |
| 全部 3 项失败 | 🔴 红灯 | 暂停，重新评估技术选型，可能需要换工具链 |

---

## 测试后待更新文件

每一项测试完成后，更新以下文件：

- [ ] `framework/templates/character-package-template.md` — 根据 prompt 实际效果优化 Suno/视觉提示字段
- [ ] `outputs/characters/sun-wukong/character-package.md` — 回写实际可用的 prompt
- [ ] `framework/operations/risk-register.md` — 更新 R1/R2 的实际数据
- [ ] `framework/modules/07-external-tools-integration.md` — 更新成本估算
- [ ] `outputs/_prompt-library.md` — 沉淀成功 prompt（新增）

---

## 下一步

1. 到 https://evolink.ai 注册获取 API Key
2. `export EVOLINK_API_KEY="你的key"`
3. 回复"Key就绪"，我立即启动测试 1
