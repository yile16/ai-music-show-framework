# Tasks: AI Music MV Workflow

**Input**: Design documents from `/specs/001-ai-music-mv-workflow/`

**Prerequisites**: `plan.md`, `spec.md`, `research.md`, `data-model.md`, `quickstart.md`

## Phase 1: Setup

- [ ] T001 Create `outputs/characters/_template/` package folder structure.
- [ ] T002 Create reusable templates for research, creative canon, song package, visual bible, storyboard, review, and production plan.
- [ ] T003 Create a workflow map template with owner type, input, output, quality gate, and scale notes.

## Phase 2: Foundational Decisions

- [ ] T004 Choose first demo character and record why it is copyright-safe enough for experimentation.
- [ ] T005 Define first target format: vertical short, MV clip, or mini variety-show segment.
- [ ] T006 Define first target duration and publish platform assumptions.
- [ ] T007 Define the project vocabulary: character, creative canon, song package, visual bible, storyboard, review gate, scale pipeline.

## Phase 3: User Story 1 - Produce One Character MV Package (P1)

**Goal**: Produce a complete text-first package for one character.

**Independent Test**: Another person can use the package to generate first audio, first image, and first storyboard test.

- [ ] T008 [US1] Collect source notes for the selected character in `outputs/characters/[slug]/research.md`.
- [ ] T009 [US1] Separate confirmed source material, traditional interpretation, and creative invention.
- [ ] T010 [US1] Write the character biography as a dramatic life story.
- [ ] T011 [US1] Create `outputs/characters/[slug]/creative-canon.md`.
- [ ] T012 [US1] Create final `production-plan.md` with next actions and dependencies.

## Phase 4: User Story 2 - Clarify Spirit and Music Direction (P2)

**Goal**: Turn biography into music-ready identity.

- [ ] T013 [US2] Extract core conflict, emotional color, values, and audience hook.
- [ ] T014 [US2] Define genre, tempo range, vocal style, arrangement references, and forbidden cliches.
- [ ] T015 [US2] Draft a Suno-compatible song brief.
- [ ] T016 [US2] Draft lyrics or lyric prompt with clear sections.
- [ ] T017 [US2] Review whether the song direction sounds character-specific rather than generic.

## Phase 5: User Story 3 - Generate Reusable Visual Identity (P3)

**Goal**: Make visual continuity possible before image generation.

- [ ] T018 [US3] Draft a copyright-safe visual bible.
- [ ] T019 [US3] Define stable identity anchors, costume rules, palette, silhouette, and stage persona.
- [ ] T020 [US3] Define supporting cast and environment rules only where needed for the demo.
- [ ] T021 [US3] Create image prompts and negative prompts for first reference generation.
- [ ] T022 [US3] Define the prompt revision loop for failed or drifting images.

## Phase 6: User Story 4 - Repeatable Agent Workflow (P4)

**Goal**: Identify what should become agents, tools, human gates, or scale pipelines.

- [ ] T023 [US4] Label every stage by owner type.
- [ ] T024 [US4] Search for existing skills/programs for research, lyric generation, storyboard generation, image consistency, image-to-video, and compliance review.
- [ ] T025 [US4] Decide which missing capabilities need custom agents.
- [ ] T026 [US4] Define quality gates before media generation and publication.
- [ ] T027 [US4] Run the workflow on a second character as a reuse test.

## Phase 7: Polish and Validation

- [ ] T028 Run checklist review against `checklists/requirements.md`.
- [ ] T029 Confirm every expensive generation step is preceded by text approval.
- [ ] T030 Confirm copyright and platform risks are flagged.
- [ ] T031 Summarize what to build next: skill, CLI, document template, or web app.
