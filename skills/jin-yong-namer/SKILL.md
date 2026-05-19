---
name: jin-yong-namer
description: Use this skill when the user asks 金庸, Jin Yong, or a 金庸式/武侠式命名师 to rename or create Chinese names for Rainbow Six Siege operators. It also participates when the user asks 所有人格, 多人翻译, 批量起名, 轮流起名, 投票, or 指定人格决策. It reads local operator dossiers in resources/bios, analyzes the operator's biography, codename type, English codename meaning, ability/playstyle, and Chinese speech fluency, then proposes names using Jin Yong-inspired wuxia naming methods and judgment standards.
---

# Jin Yong Operator Namer

## Workflow

1. Resolve the target operator.
   - Prefer `resources/bios/<normalized-operator>.md`.
   - If the file is not obvious, search `resources/bios/*.md` for `干员代号: <name>`.
   - Read the whole dossier before naming.
2. Extract the naming evidence:
   - biography/personality and origin,
   - English codename literal meaning and associations,
   - unique ability and gameplay role,
   - Side, Squad, and Specialties.
3. Read `references/persona.md` for the Jin Yong naming lens.
4. Read `references/operator-naming-workflow.md` for the required output format, Codename Type Pass, and scoring checklist.
5. If the request involves multiple personas, all personas, batch naming, voting, subagents, or a designated decision persona, read `references/multi-persona-naming-workflow.md`; use Subagent mode for formal batch judging when available, otherwise fall back to Single-thread mode.
6. If the codename is 姓名型, make fluent transliteration the default main-name recommendation and use wuxia-style names only as aliases.
7. Generate candidates, reject weak ones, then recommend one final Chinese name.

## Rules

- Do not merely transliterate a non-name codename unless that is clearly the strongest choice.
- Do not replace a clear personal-name codename with a wuxia nickname as the main name.
- Prefer names that can be spoken smoothly in Chinese voice chat.
- Keep the name useful in gameplay callouts: short, distinct, and hard to confuse with existing operators.
- Preserve the operator's core identity more than the surface gimmick.
- Cite the local dossier path used as evidence.
