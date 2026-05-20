# Research: AI Music MV Workflow

## Decision: Start with one complete text-first character package

**Rationale**: The user explicitly wants to avoid wasting tokens and generation budget. A text-first package exposes weak assumptions before image, music, or video tools are involved.

**Alternatives considered**:
- Build a full automation platform first: rejected because the creative pipeline is not yet proven.
- Generate a video immediately: rejected because visual consistency and story quality are unresolved.

## Decision: Treat this as a creative production workflow before treating it as software

**Rationale**: The key risks are story coherence, taste, prompt quality, copyright safety, and repeatability. Software should codify the winning workflow after one or two manual runs.

**Alternatives considered**:
- Build many specialized agents immediately: too much structure before the workflow is validated.
- Use one mega prompt forever: fast, but hard to audit, debug, or scale.

## Decision: Use a four-lane ownership model

**Rationale**: Each step should be labeled as Agent, Existing Tool, Human Review, or Future Scale Pipeline. This directly answers the user's question about which parts need agents and which parts need scale.

**Alternatives considered**:
- Agent-only map: misses tool maturity and human approval needs.
- Tool-only map: misses orchestration, taste, and review gates.

## Decision: Make copyright/compliance a first-class gate

**Rationale**: Mythological and historical characters are safer than modern IP, but visual depictions and celebrity/variety-show references still create risk. The system must distinguish inspiration from copying.

**Alternatives considered**:
- Review only at publication: rejected because late-stage legal issues waste generation work.

## Decision: Use a fictional host/system premise as the narrative wrapper

**Rationale**: The user wants novel-like scripts and an in-world explanation for why characters perform in short videos. A host with a system, power, or mission can connect episodes and support long-term seriality.

**Alternatives considered**:
- Standalone MV anthology: simpler, but less sticky as a universe-scale show.
- Pure music variety show format: clear, but lacks the novel/game-like growth hook.
