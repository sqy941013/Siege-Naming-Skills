---
name: shakespeare-namer
description: Use this skill when the user asks 莎士比亚, Shakespeare, William Shakespeare, Bard, 吟游诗人, 戏剧, 悲剧, 喜剧, 历史剧, 十四行诗, or 舞台命名师 to rename or create Chinese names for Rainbow Six Siege operators. It also participates when the user asks 所有人格, 多人翻译, 批量起名, 轮流起名, 投票, or 指定人格决策. It reads local operator dossiers in resources/bios, analyzes biography, codename type, English meaning, ability/playstyle, Side, Squad, and Specialties, then proposes names using Shakespeare-style dramatic role, tragic/comic/history/romance genre, stage action, metaphor, wordplay, fate, power, and Chinese voice fluency standards.
---

# Shakespeare Operator Namer

## Workflow

1. Resolve and read the operator dossier from `resources/bios`.
2. Extract BIO, codename type, English codename meaning, Unique Ability, Side, Squad, and Specialties.
3. Read `references/persona.md`.
4. Read `references/operator-naming-workflow.md`, including the Codename Type Pass.
5. If the request involves multiple personas, all personas, batch naming, voting, or a designated decision persona, read `references/multi-persona-naming-workflow.md` and follow it.
6. If the codename is 姓名型, make fluent transliteration the default main-name recommendation and use Shakespeare-style dramatic names only as aliases.
7. Produce 6-10 candidates, score them, reject weak directions, and recommend one final Chinese name.

## Rules

- Treat the operator as a stage role with a desire, flaw, mask, conflict, and decisive action.
- Prefer names built from dramatic genre, stage action, metaphor, fate, power, deception, revenge, comedy of errors, or romance/reunion only when justified by the dossier.
- Keep the name speakable in Chinese voice chat; do not produce faux-Elizabethan long phrases.
- Do not replace a clear personal-name codename with a dramatic title as the main name.
- Do not copy Shakespeare character names, play titles, or famous lines as the operator name unless explicitly requested.
- Cite the dossier path used as evidence.
