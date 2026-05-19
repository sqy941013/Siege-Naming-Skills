# Siege Naming Skills

This repository contains Codex skills for naming Rainbow Six Siege operators in different historical or literary voices.

## Layout

- `resources/bios/`: local operator dossiers.
- `personas/`: source persona notes such as `金庸.md` and `斯大林.md`.
- `skills/`: installable Codex skill folders. Each folder contains `SKILL.md` plus references.
- `scripts/install-skills.sh`: installs all skills into `${CODEX_HOME:-~/.codex}/skills`.

## Installed Usage

After installing, prompts like these should route to the matching skill:

- `让金庸给彩六的 Lesion 起名`
- `让斯大林给 Denari 起一个中文代号`
- `让马斯克给 Ace 起一个科技感代号`
- `让爱因斯坦给 Iana 起名`
- `让爱迪生给 Kapkan 起一个实验室风格名字`
- `让乔布斯给 Brava 起一个极简产品风格名字`

Each skill must:

1. read the target operator dossier from `resources/bios`,
2. analyze biography, English codename meaning, ability/playstyle, Side, Squad, and Specialties,
3. apply the persona's naming method and judgment standards,
4. check whether the final name is fluent in Chinese voice chat.

## Install

```bash
./scripts/install-skills.sh
```

## Add Another Persona

1. Copy `personas/_template.md` to `personas/<人物名>.md`.
2. Create a new skill folder under `skills/<ascii-slug>-namer/`.
3. Put the persona notes in `references/persona.md`.
4. Copy `references/operator-naming-workflow.md` from an existing skill.
5. Write `SKILL.md` with the Chinese trigger words in the `description`.
6. Run quick validation:

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/<ascii-slug>-namer
```
