# Data Model: AI Music MV Workflow

## Character

- `name`: canonical project name
- `source_type`: mythological, historical, literary public domain, original, or other
- `source_notes`: verified sources and uncertainty notes
- `core_conflict`: main dramatic tension
- `spirit_keywords`: 3-7 identity keywords
- `music_direction`: genre, mood, tempo, vocal identity, arrangement notes
- `copyright_risk`: low, medium, high, blocked

## Creative Canon

- `approved_biography`: project-approved life summary
- `fact_tradition_invention_split`: what is factual, traditional, or invented
- `world_role`: why this character appears in the universe-scale music show
- `power_conversion_rule`: how views, music, or attention become in-world power
- `forbidden_cliches`: ideas to avoid

## Song Package

- `song_title_options`
- `music_brief`
- `lyric_structure`
- `lyrics_or_prompt`
- `hook_lines`
- `generation_notes`
- `revision_history`

## Visual Bible

- `identity_anchors`: stable facial/body/costume cues
- `silhouette`
- `palette`
- `wardrobe_rules`
- `stage_persona`
- `supporting_cast`
- `environment_rules`
- `negative_prompts`
- `reference_strategy`

## Storyboard

- `scene_number`
- `duration`
- `story_beat`
- `shot_type`
- `image_prompt`
- `motion_prompt`
- `music_alignment`
- `production_risk`

## Workflow Step

- `name`
- `input`
- `output`
- `owner_type`: Agent, Existing Tool, Human Review, Future Scale Pipeline
- `quality_gate`
- `tool_candidates`
- `scale_notes`

## Review Gate

- `gate_name`
- `reviewer`
- `approval_criteria`
- `blocking_issues`
- `decision`: approved, revise, blocked

## Tool Candidate

- `name`
- `category`
- `maturity`
- `cost`
- `integration_complexity`
- `replacement_reason`
