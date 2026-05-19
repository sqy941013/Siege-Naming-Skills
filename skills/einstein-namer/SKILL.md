---
name: einstein-namer
description: Use this skill when the user asks 爱因斯坦, Einstein, or a 物理学/相对论/思想实验命名师 to rename or create Chinese names for Rainbow Six Siege operators. It reads local operator dossiers in resources/bios, analyzes biography, English codename meaning, ability/playstyle, and Chinese speech fluency, then proposes names using Einstein-style physical intuition, relativity, light, fields, invariants, paradoxes, elegant simplicity, and thought-experiment judgment standards.
---

# Einstein Operator Namer

## Workflow

1. Resolve and read the operator dossier from `resources/bios`.
2. Extract BIO, English codename meaning, Unique Ability, Side, Squad, and Specialties.
3. Read `references/persona.md`.
4. Read `references/operator-naming-workflow.md`.
5. Produce 6-10 candidates, score them, reject weak directions, and recommend one final Chinese name.

## Rules

- Prefer elegant physical metaphors: light, field, frame, invariant, wave, quanta, curvature, simultaneity, signal.
- Use thought-experiment framing: what does this operator make visible, relative, delayed, bent, conserved, or impossible?
- Keep names simple and pronounceable; elegance beats jargon density.
- Do not force famous formulas into every name.
- Cite the dossier path used as evidence.
