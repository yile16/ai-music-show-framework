# Implementation Plan: AI Music MV Workflow

**Branch**: `001-ai-music-mv-workflow` | **Date**: 2026-05-19 | **Spec**: [spec.md](./spec.md)

**Input**: Feature specification from `/specs/001-ai-music-mv-workflow/spec.md`

## Summary

Build a text-first production workflow for one-character AI music MV creation. The MVP should turn a character idea into a complete creative package: research summary, character spirit, song direction, lyrics prompt, visual bible, storyboard, review gates, tool candidates, and a repeatable workflow map. The first implementation should be workflow/document driven, with structured outputs that can later become agents, CLI commands, or a web app.

## Technical Context

**Language/Version**: Markdown-first workflow for the test; future automation can use Python or TypeScript after tool choices are validated.

**Primary Dependencies**: Existing AI tools and skills for research, writing, prompt generation, image generation, music generation, video generation, and compliance review.

**Storage**: Files per character package; future version may use a content database for characters, prompts, assets, review gates, and tool results.

**Testing**: Document checklist review, package completeness review, dry-run on one character, and second-character reuse test.

**Target Platform**: Creator workflow used locally first; future target can be CLI, web workspace, or agent orchestration system.

**Project Type**: Creative production workflow / agent orchestration framework.

**Performance Goals**: One complete text-first character package within one working session before any expensive media generation.

**Constraints**: Text must be approved before image, music, or video generation; output must separate fact, tradition, and invention; protected-IP risk must be reviewed before publication.

**Scale/Scope**: MVP covers one character and one short MV unit; scale target is a repeatable multi-character universe-scale AI music variety show.

## Constitution Check

- Text-first planning before expensive generation: pass.
- Human review at legal, creative, and publication gates: pass.
- Existing mature tools preferred before custom agents: pass.
- Single-character demo before platform-scale buildout: pass.

## Project Structure

### Documentation (this feature)

```text
specs/001-ai-music-mv-workflow/
├── spec.md
├── plan.md
├── research.md
├── data-model.md
├── quickstart.md
├── tasks.md
└── checklists/
    └── requirements.md
```

### Future Source Code Shape

```text
workflow/
├── character-research/
├── spirit-extraction/
├── song-package/
├── visual-bible/
├── storyboard/
├── tool-discovery/
├── review-gates/
└── publishing-readiness/

packages/
├── character-canon/
├── prompt-library/
├── asset-manifest/
└── workflow-runner/

outputs/
└── characters/
    └── [character-slug]/
        ├── research.md
        ├── creative-canon.md
        ├── song-package.md
        ├── visual-bible.md
        ├── storyboard.md
        ├── review.md
        └── production-plan.md
```

**Structure Decision**: Start with documentation and repeatable templates. Add code only when repeated runs reveal stable data structures and bottlenecks.

## Agent / Scale / Human Review Map

| Stage | Owner Type | Why |
|-------|------------|-----|
| Character source discovery | Agent + Existing Tool | Research breadth matters; citations and uncertainty tracking are needed. |
| Biography summarization | Agent | Structured condensation is repeatable and low-cost. |
| Spirit and music direction | Agent + Human Review | AI can propose; human taste must approve. |
| Lyrics and Suno prompt | Agent + Existing Tool | Strong fit for structured generation and iteration. |
| Worldbuilding bridge | Agent + Human Review | Narrative coherence and brand tone need taste judgment. |
| Visual bible | Agent + Human Review | Consistency and copyright safety require approval. |
| Image generation | Existing Tool | Use mature text-to-image systems first. |
| Storyboard | Agent + Human Review | Agent drafts; producer decides pacing and feasibility. |
| Image-to-video generation | Existing Tool + Scale Pipeline | Tool choice and batch execution become scale bottlenecks. |
| Compliance review | Agent + Human Review | Agent flags risks; human makes final call. |
| Tool/skill discovery | Agent | Repeated market scan can save development effort. |
| Publishing package | Agent + Human Review | Agent prepares metadata; human approves release. |

## Phase 0: Research Decisions

See [research.md](./research.md).

## Phase 1: Design Artifacts

See [data-model.md](./data-model.md) and [quickstart.md](./quickstart.md).

## Complexity Tracking

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|--------------------------------------|
| Multiple agent roles | The workflow spans research, creative writing, prompt design, compliance, and production orchestration. | A single prompt can produce a demo, but cannot scale into reusable quality gates and repeatable character packages. |
| Human review gates | Creative taste, copyright risk, and publication risk cannot be fully delegated. | Fully automated publishing is too risky for early-stage content experiments. |
