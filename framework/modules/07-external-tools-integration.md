# 模块 07：外部工具与服务集成计划

> 本文档将外部 AI 工具、开源项目、LobeHub 技能映射到框架的各生产环节。
> 状态：**计划书** | 版本：0.1.0 | 日期：2026-05-20

---

## 总览

```
┌─────────────────────────────────────────────────────────────┐
│                    诸天音综系统框架                            │
│                                                             │
│  模块 01-06（已建立）          外部工具 & 服务（本模块）        │
│  ┌──────────────────┐       ┌──────────────────────────┐    │
│  │ 世界观 & 系统     │       │ evolink-music (Suno)     │    │
│  │ 角色内容包        │       │ ai-music-video (合成)    │    │
│  │ 导演系统          │       │ evolink-video (图→视频)  │    │
│  │ 生产流程          │──→────│ evolink-media (统一API)  │    │
│  │ Agent 地图        │       │ storyboard-consistent    │    │
│  │ 商业化规划        │       │ VideoForge (参考架构)    │    │
│  └──────────────────┘       └──────────────────────────┘    │
│                                                             │
│  新增：07-外部工具集成（本模块）                               │
└─────────────────────────────────────────────────────────────┘
```

---

## 一、工具清单与定位

### 1.1 LobeHub 技能（可直接安装到 Claude Code）

#### Tier 1 — 核心推荐（覆盖生产全链路）

| 技能标识 | 一句话定位 | 覆盖框架环节 |
|---------|-----------|------------|
| `openclaw-skills-evolink-media` | **一站式媒体 API**：60+ 模型，图/视频/音乐统一调用 | 阶段 5-7-9 |
| `openclaw-skills-ai-music-video` | **端到端 MV 生成**：Suno 音乐 + 画面生成 + ffmpeg 合成 | 阶段 5-9 |
| `openclaw-skills-evolink-music` | **Suno 音乐专精**：v4/v4.5/v5，文本→音乐，人声控制 | 阶段 5 |
| `openclaw-skills-evolink-video` | **视频生成专精**：37 模型，图→视频，文本→视频 | 阶段 7-9 |

#### Tier 2 — 辅助能力（特定环节增强）

| 技能标识 | 一句话定位 | 覆盖框架环节 |
|---------|-----------|------------|
| `openclaw-skills-ai-video-gen-tools` | 文本→视频全流程：图片+合成+配音+编辑 | 阶段 7-9 |
| `samuraigpt-generative-media-skills-media` | 终端一站式：100+ 模型 | 阶段 5-6-7 |
| `davila7-claude-code-templates-multimodal-audiocraft` | Meta AudioCraft：MusicGen + AudioGen | 阶段 5（本地音乐生成备选） |

#### Tier 3 — 专项能力

| 技能标识 | 用途 |
|---------|------|
| `openclaw-skills-eachlabs-video-generation` | 文本→视频、头像生成、运动控制 |
| `openclaw-skills-music-video-generation` | 音频可视化、歌词视频 |
| `openclaw-skills-volcengine-ai-video-generation` | 火山引擎视频生成（国内备选） |

### 1.2 GitHub 开源项目（架构参考 & 代码复用）

| 项目 | Stars | 核心价值 | 复用什么 |
|------|-------|---------|---------|
| **[Sri01729/template-ai-storyboard-consistent-character](https://github.com/Sri01729/template-ai-storyboard-consistent-character)** | 34 | Mastra 多 Agent 分镜系统，角色跨镜头一致性 | **Agent 架构、Memory 管理、一致性方案** |
| **[hempstar-777/VideoForge](https://github.com/hempstar-777/VideoForge)** | 新 | AI MV 生成引擎完整代码 | **工程架构、API 编排模式** |
| **[SpoddyCoder/visualizing-music](https://github.com/SpoddyCoder/visualizing-music)** | 3 | AI 音乐视频笔记和踩坑记录 | **实践经验和边界案例** |
| **[bruchansky/shotblockr](https://github.com/bruchansky/shotblockr)** | 3 | 3D + AI 分镜 | **分镜交互设计思路** |

---

## 二、生产流程逐阶段工具映射

### 阶段 5：音乐方案 → 歌曲生成

```
角色内容包（音乐表达字段）
        │
        ▼
┌──────────────────────────────────────┐
│ 第一选择: evolink-music               │
│   - Suno v4.5/v5 音乐生成             │
│   - 自定义歌词 / 纯器乐 / 人声控制     │
│   - 输入：歌词 + 曲风 + 情绪标签       │
│   - 输出：mp3 音频文件                 │
│                                      │
│ 备选: evolink-media（统一 API）       │
│ 备选: samuraigpt-media（100+ 模型）   │
│ 本地备选: AudioCraft MusicGen         │
└──────────────────────────────────────┘
```

### 阶段 6：视觉设定 → 图片生成

```
角色内容包（视觉表达字段）
        │
        ▼
┌──────────────────────────────────────┐
│ 第一选择: evolink-media               │
│   - GPT Image / Flux / Seedream       │
│   - 支持角色锚点 prompt + 负面提示词   │
│   - 批次生成后人工筛选                │
│                                      │
│ 角色一致性方案（关键！）:              │
│   → 参考 storyboard-consistent-char   │
│     的 Memory 管理方案                │
│   → 第一张"定妆照"锁定 seed           │
│   → 后续生成都带上定妆照作为 reference │
│                                      │
│ 备选: stable-diffusion 技能           │
└──────────────────────────────────────┘
```

### 阶段 7：分镜脚本 → 视频片段

```
分镜脚本（镜头序列）
        │
        ▼
┌──────────────────────────────────────┐
│ 第一选择: evolink-video               │
│   - Seedance / Kling / Veo 3          │
│   - 图→视频（每个分镜作为输入图）      │
│   - 文→视频（镜头描述直接生成）        │
│                                      │
│ 批量生成策略:                         │
│   - 按分镜表逐镜头生成                 │
│   - 每个镜头生成 2-3 个备选            │
│   - 人工/Agent 初筛后进入剪辑          │
│                                      │
│ 备选: ai-video-gen-tools              │
│   - LumaAI / Runway / Replicate       │
│   - 带配音和编辑能力                   │
└──────────────────────────────────────┘
```

### 阶段 9：生成与发布 → MV 合成

```
音频 + 视频片段 + 分镜时间轴
        │
        ▼
┌──────────────────────────────────────┐
│ 第一选择: ai-music-video              │
│   - Suno 音乐 + 画面 + ffmpeg 合成    │
│   - 自动 SRT 字幕（歌词时间戳）       │
│   - 支持 Slideshow / Video / Hybrid   │
│   - Token 成本追踪内置                │
│                                      │
│ 输出格式:                             │
│   - 竖版 9:16（短视频平台）           │
│   - 横版 16:9（B站/YouTube）          │
│   - 封面图 + 标题包                   │
└──────────────────────────────────────┘
```

---

## 三、关键架构方案：角色视觉一致性

这是 AI 视频制作中最大的技术难点。开源项目 `template-ai-storyboard-consistent-character` 提供了可参考的方案。

### 3.1 问题定义

同一个角色在不同镜头中面部、服装、体型发生变化，导致观众无法认出是同一人。

### 3.2 解决方案（三层防线）

```
第一层：Prompt 锚点系统
─────────────────────────
  角色内容包中的"形象锚点"字段作为所有 prompt 的固定前缀:
  "Male, East Asian features, golden pupils with faint flame,
   dark iron staff with gold runes, black fitted battle suit,
   deep green burnt cape, ring-shaped scar on forehead..."

第二层：Reference Image + Seed Lock
─────────────────────────────────────
  1. 首先生成"角色定妆照"（多角度：正面/侧面/背面）
  2. 人工确认定妆照后，锁定 seed
  3. 后续所有图片/视频生成都使用定妆照作为 reference_image
  4. Motion strength 控制在 0.6-0.8（避免变形）

第三层：一致性审核 Agent（远期）
─────────────────────────────────
  自动对比新生成的镜头与定妆照，检测：
  - 面部关键特征是否一致
  - 服装颜色是否偏移
  - 体型比例是否偏离设定
  触发阈值时自动标记"需要人工复审"
```

### 3.3 实现路径

| 阶段 | 做法 | 依赖 |
|------|------|------|
| Phase 1（当前） | 手动：在模板中填写详细锚点 prompt，人工对比 | 无 |
| Phase 2 | 半自动：脚本固定 prompt 前缀 + seed lock | evolink-media API |
| Phase 3 | Agent 化：参考 storyboard-consistent-char 的 Memory 管理 | Mastra 框架 |

---

## 四、多模型统一调度策略

### 4.1 为什么需要统一 API

- 避免逐个对接 Suno/Kling/Flux/Seedance 的认证和文档
- 模型有各自的强项和地域限制
- API 变更时只需改一处

### 4.2 推荐方案：`evolink-media` 作为主 API

```
                    ┌─────────────────┐
                    │  evolink-media   │
                    │  (统一 API 网关)  │
                    └───────┬─────────┘
                            │
        ┌───────────────────┼───────────────────┐
        ▼                   ▼                   ▼
   ┌──────────┐      ┌──────────┐        ┌──────────┐
   │  音乐     │      │  图片     │        │  视频     │
   │ Suno v5  │      │ Flux     │        │ Kling    │
   │ Suno v4.5│      │ Seedream │        │ Seedance │
   │          │      │ GPT Img  │        │ Veo 3    │
   └──────────┘      └──────────┘        │ Sora     │
                                          └──────────┘
```

### 4.3 成本估算（每个 MV Demo）

| 环节 | 调用次数 | 预估费用 |
|------|---------|---------|
| 歌曲生成（Suno v5） | 2-3 次 | ~$0.20 |
| 视觉定妆照（Flux 高清） | 5-10 张 | ~$0.50 |
| 分镜图片（10-15 镜 x 3 备选） | 30-45 张 | ~$2.00 |
| 视频片段（8-10 段，每段 5 秒） | 8-10 次 | ~$3.00 |
| MV 合成（ffmpeg） | 1 次 | 本地免费 |
| **合计** | | **~$5-6** |

> 以上为估算，实际费用取决于模型选择、分辨率和 API 定价变动。

---

## 五、"自建 vs 借用"决策矩阵

| 能力 | 决策 | 理由 |
|------|------|------|
| 歌曲生成 | **借用** Suno v5（via evolink） | 自建无价值，Suno 已成熟 |
| 歌词撰写 | **自建 Agent**（精神提炼 Agent） | 需要深度角色理解，通用模型写不好 |
| 图片生成 | **借用** Flux/Seedream（via evolink） | 自建无价值 |
| 视觉一致性 | **自建 Agent**（参考 storyboard 架构） | 这是核心壁垒，通用方案不解决 |
| 分镜脚本 | **自建 Agent** | 需要结合角色包+导演系统，封闭场景 |
| 视频生成 | **借用** Kling/Seedance（via evolink） | 自建成本不可承受 |
| MV 合成 | **借用** ffmpeg + ai-music-video 技能 | 现成方案够用 |
| 审核 | **自建 Agent** | 规则定制化程度高 |
| 工具发现 | **借用** lobehub 搜索 | 已存在 |

---

## 六、分阶段集成路线

### Phase 1：本地验证（当前阶段 — 文档 & 模板）

- [ ] 安装 `evolink-media` 技能到项目
- [ ] 用孙悟空角色包的歌词 + 曲风字段，试生成一首歌
- [ ] 用角色包的视觉锚点 prompt，试生成 3 张定妆照
- [ ] 记录 prompt 迭代经验，回写到角色包模板

### Phase 2：流程串通（1-2 周后）

- [ ] 用 `ai-music-video` 技能跑通一个 30 秒 demo
- [ ] 记录每个环节的 token 消耗和时间成本
- [ ] 将成功的 prompt 沉淀为"提示词资产库"

### Phase 3：Agent 化（3-4 周后）

- [ ] 参考 `storyboard-consistent-character` 架构，用 Mastra 搭建分镜 Agent
- [ ] 角色一致性 Memory 管理接入
- [ ] 自动审核 Agent 第一版

### Phase 4：规模化（Phase 5 路线图）

- [ ] 批量角色内容包生成
- [ ] 数据回流 → 排名系统
- [ ] 多角色 Battle/MV 自动化

---

## 七、技能安装命令速查

```bash
# 核心包（推荐先装）
npx -y @lobehub/market-cli skills install openclaw-skills-evolink-media --agent claude-code
npx -y @lobehub/market-cli skills install openclaw-skills-ai-music-video --agent claude-code

# 专项能力（按需安装）
npx -y @lobehub/market-cli skills install openclaw-skills-evolink-music --agent claude-code
npx -y @lobehub/market-cli skills install openclaw-skills-evolink-video --agent claude-code

# 安装后技能文件在 .claude/skills/ 目录下
```

---

## 八、风险与备用方案

| 风险 | 概率 | 备用方案 |
|------|------|---------|
| Suno API 定价大幅上涨 | 中 | 切到 AudioCraft MusicGen（本地免费） |
| 角色一致性在视频生成中崩坏 | 高 | 降级为 Slideshow 模式（静态图 + 运镜），放弃完整视频生成 |
| evolink API 服务不稳定 | 低 | 直连各模型官方 API（Suno/Kling/Flux 各有独立接入） |
| 短视频平台对 AI 内容限流 | 中 | 加强"人类参与度"标签，混合实拍素材 |
| 版权审核不通过 | 中 | 切到 100% 原创角色，放弃神话 IP |
