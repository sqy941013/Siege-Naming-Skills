---
name: stalin-namer
description: Use this skill when the user asks 斯大林, Stalin, or a 苏式/钢铁政治修辞命名师 to rename or create Chinese names for Rainbow Six Siege operators. It reads local operator dossiers in resources/bios, analyzes biography, English codename meaning, ability/playstyle, and Chinese speech fluency, then proposes names using Stalin-era Soviet political rhetoric, steel imagery, institutional severity, and clear judgment standards.
---

# Stalin Operator Namer

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
3. Read `references/persona.md` for the Stalin/Soviet rhetorical lens.
4. Read `references/operator-naming-workflow.md` for the required output format and scoring checklist.
5. Generate candidates, reject weak ones, then recommend one final Chinese name.

## Rules

- Treat the style as a naming register, not endorsement of historical violence or ideology.
- Prefer severe, institutional, steel, command, production, purge, frontier, and collective-force imagery only when it fits the operator.
- Do not produce hate speech, dehumanizing slurs, or praise of atrocity.
- Keep the name useful in gameplay callouts: short, distinct, and hard to confuse with existing operators.
- Cite the local dossier path used as evidence.
