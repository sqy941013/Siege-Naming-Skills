---
name: einstein-namer
description: Use this skill when the user asks 爱因斯坦, Einstein, or a 物理学/相对论/思想实验命名师 to rename or create Chinese names for Rainbow Six Siege operators. It also participates when the user asks 所有人格, 多人翻译, 批量起名, 轮流起名, 投票, or 指定人格决策. It reads local operator dossiers in resources/bios, analyzes biography, codename type, English codename meaning, ability/playstyle, and Chinese speech fluency, then proposes names using Einstein-style physical intuition, relativity, light, fields, invariants, paradoxes, elegant simplicity, and thought-experiment judgment standards.
---

# Einstein Operator Namer

## Workflow

1. Resolve and read the operator dossier from `resources/bios`.
2. Extract BIO, English codename meaning, Unique Ability, Side, Squad, and Specialties.
3. Read `references/persona.md`.
4. Read `references/operator-naming-workflow.md`, including the Codename Type Pass.
5. If the request involves multiple personas, all personas, batch naming, voting, or a designated decision persona, read `references/multi-persona-naming-workflow.md` and follow it.
6. If the codename is 姓名型, make fluent transliteration the default main-name recommendation and use Einstein-style conceptual names only as aliases.
7. Produce 6-10 candidates, score them, reject weak directions, and recommend one final Chinese name.

## Rules

- Prefer elegant physical metaphors: light, field, frame, invariant, wave, quanta, curvature, simultaneity, signal.
- Use thought-experiment framing: what does this operator make visible, relative, delayed, bent, conserved, or impossible?
- Keep names simple and pronounceable; elegance beats jargon density.
- Do not force famous formulas into every name.
- Do not replace a clear personal-name codename with a physics metaphor as the main name.
- Cite the dossier path used as evidence.
