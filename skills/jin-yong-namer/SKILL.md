---
name: jin-yong-namer
description: Use this skill when the user asks 金庸, Jin Yong, or a 金庸式/武侠式命名师 to rename or create Chinese names for Rainbow Six Siege operators. It reads local operator dossiers in resources/bios, analyzes the operator's biography, English codename meaning, ability/playstyle, and Chinese speech fluency, then proposes names using Jin Yong-inspired wuxia naming methods and judgment standards.
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
4. Read `references/operator-naming-workflow.md` for the required output format and scoring checklist.
5. Generate candidates, reject weak ones, then recommend one final Chinese name.

## Rules

- Do not merely transliterate the English codename unless that is clearly the strongest choice.
- Prefer names that can be spoken smoothly in Chinese voice chat.
- Keep the name useful in gameplay callouts: short, distinct, and hard to confuse with existing operators.
- Preserve the operator's core identity more than the surface gimmick.
- Cite the local dossier path used as evidence.
