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
- `让莎士比亚给 Jäger 起一个戏剧风格名字`
- `Skopós / Tubarão / Rauora 所有人格每人 3 个候选，投票，由斯大林决策`

Each skill must:

1. read the target operator dossier from `resources/bios`,
2. analyze biography, English codename meaning, ability/playstyle, Side, Squad, and Specialties,
3. classify whether the codename is a personal-name codename, callsign/title codename, or mixed codename,
4. keep fluent transliteration as the default main recommendation for personal-name codenames such as `Zofia`,
5. apply the persona's naming method and judgment standards,
6. check whether the final name is fluent in Chinese voice chat.

## Multi-Persona Batch Naming

When the user asks for 所有人格, 多人翻译, 批量起名, 轮流起名, 投票, subagents, or 指定人格决策, use each skill's `references/multi-persona-naming-workflow.md`.

The required batch flow is:

1. the main thread maintains the target-name queue and processes one operator at a time,
2. read the current operator dossier and build a neutral evidence packet,
3. classify codename type before styling,
4. in formal batch judging, launch one isolated subagent per active persona when a Codex, Claude Code, or compatible runner is available,
5. if subagents are unavailable, use the documented Single-thread mode fallback,
6. each active persona gives exactly 3 candidates per operator,
7. each candidate ties back to BIO, codename meaning, ability/playstyle, persona fit, and Chinese voice fluency,
8. cluster similar candidates by semantic direction,
9. vote across clusters,
10. send the aggregated decision packet to the designated decision persona subagent when one is named,
11. distinguish 主译名, 风格名, 玩家外号, and 技能名 when relevant.

Subagent mode isolates persona context deliberately. Candidate persona agents receive only the operator evidence packet and their own persona reference; they do not see other personas' candidates. The main thread aggregates without inventing new names, then the decision persona makes a separate final pass from the vote summary.

## Install

```bash
./scripts/install-skills.sh
```

## Add Another Persona

1. Copy `personas/_template.md` to `personas/<人物名>.md`.
2. Create a new skill folder under `skills/<ascii-slug>-namer/`.
3. Put the persona notes in `references/persona.md`.
4. Copy `references/operator-naming-workflow.md` from an existing skill.
5. Copy `references/multi-persona-naming-workflow.md` from an existing skill.
6. Write `SKILL.md` with the Chinese trigger words in the `description` and mention batch naming participation.
7. Run quick validation:

```bash
python3 ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/<ascii-slug>-namer
```
