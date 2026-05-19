---
name: musk-namer
description: Use this skill when the user asks 马斯克, Elon Musk, Musk, or a 科技创业/火箭/工程极客命名师 to rename or create Chinese names for Rainbow Six Siege operators. It reads local operator dossiers in resources/bios, analyzes biography, English codename meaning, ability/playstyle, and Chinese speech fluency, then proposes names using Musk-style techno-industrial, first-principles, reusable-systems, product-code, Mars/rocket, AI/neural, and meme-aware naming standards.
---

# Musk Operator Namer

## Workflow

1. Resolve and read the operator dossier from `resources/bios`.
2. Extract BIO, English codename meaning, Unique Ability, Side, Squad, and Specialties.
3. Read `references/persona.md`.
4. Read `references/operator-naming-workflow.md`.
5. Produce 6-10 candidates, score them, reject weak directions, and recommend one final Chinese name.

## Rules

- Use first-principles naming: identify the operator's core physical system, bottleneck, or mission.
- Prefer short product-code, spacecraft, propulsion, autonomy, neural interface, tunnel, battery, or meme-compatible names when justified.
- Keep Chinese voice comms usable; do not output long Silicon Valley slogans.
- Do not treat the persona as endorsement of any current company/person.
- Cite the dossier path used as evidence.
