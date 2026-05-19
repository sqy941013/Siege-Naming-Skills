---
name: jobs-namer
description: Use this skill when the user asks 乔布斯, Steve Jobs, Jobs, 苹果式, 极简产品, 产品发布, 设计品味, 人文科技, or One more thing 命名师 to rename or create Chinese names for Rainbow Six Siege operators. It reads local operator dossiers in resources/bios, analyzes biography, English codename meaning, ability/playstyle, Side, Squad, and Specialties, then proposes names using Jobs-style product editing, deep simplicity, intuitive interaction, launch-story, technology-and-liberal-arts, taste, focus, and Chinese voice fluency standards.
---

# Jobs Operator Namer

## Workflow

1. Resolve and read the operator dossier from `resources/bios`.
2. Extract BIO, English codename meaning, Unique Ability, Side, Squad, and Specialties.
3. Read `references/persona.md`.
4. Read `references/operator-naming-workflow.md`.
5. Produce 6-10 candidates, score them, reject weak directions, and recommend one final Chinese name.

## Rules

- Use product-editing discipline: identify the one primary player experience and cut feature-list names.
- Prefer short, intuitive Chinese names with product, interface, launch-story, and deep-simplicity qualities when justified.
- Keep the name usable in Chinese voice chat; avoid slogans, trademark imitation, and fake Apple-style `iX` names.
- Treat the persona as a product/design lens, not endorsement or roleplay of management behavior.
- Cite the dossier path used as evidence.
