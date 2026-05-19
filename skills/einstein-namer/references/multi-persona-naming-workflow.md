# Multi-Persona Batch Naming Workflow

Use this workflow when the user asks for:

- 所有人格 / 多个人格 / 多人翻译 / 轮流起名,
- 批量起名 for multiple operators,
- 每个人格给出 3 个名字,
- 投票 / consensus / ranked choice,
- a designated decision persona, such as `由斯大林决策`.

This workflow can be used for one operator or many operators. It has two modes:

- **Single-thread mode**: the main agent simulates every persona. Use this for quick answers or when no subagent runner is available.
- **Subagent mode**: the main agent launches one isolated subagent per persona for each operator, then launches a decision subagent when requested. Prefer this for formal batch naming when the runtime supports Codex native subagents, Claude Code agents, or another compatible agent runner.

If the user explicitly asks for subagents, isolated personas, Claude Code compatibility, or formal batch judging, use Subagent mode when the tools are available. If subagents cannot be launched, state the fallback briefly and use Single-thread mode.

## Persona Scope

1. If the user explicitly names personas, use only those personas.
2. If the user says 所有人格, use all available naming personas in the repository or installed skills.
3. Current default persona order:
   - 金庸 (`jin-yong-namer`)
   - 马斯克 (`musk-namer`)
   - 爱因斯坦 (`einstein-namer`)
   - 爱迪生 (`edison-namer`)
   - 斯大林 (`stalin-namer`)
   - 乔布斯 (`jobs-namer`)
   - 莎士比亚 (`shakespeare-namer`)
4. For each persona, read that persona's `references/persona.md` when accessible. In this repository, use `skills/<persona-slug>/references/persona.md`. In installed skills, use sibling skill folders when available.
5. If a persona reference is not accessible, state the gap briefly and continue from the persona's known rules only if enough context remains.

## Operator Evidence

The main thread owns the operator list and processes one operator at a time. Do not send the whole batch to persona subagents at once.

For every target operator, read the local dossier from `resources/bios` before naming. Extract:

- codename and codename type,
- real name,
- birthplace and biography signals,
- original-language or English meaning when relevant,
- Unique Ability and playstyle,
- Side, Squad, and Specialties.

Always run the Codename Type Pass from `operator-naming-workflow.md` before generating candidates.

Build one neutral evidence packet per operator. Every persona subagent must receive the same evidence packet, plus only that persona's reference rules.

Evidence packet shape:

```md
# Operator Evidence Packet

- Operator:
- Dossier path:
- Codename type:
- Real name:
- Birthplace / cultural context:
- Codename meaning or original-language meaning:
- BIO signals:
- Unique Ability:
- Playstyle:
- Side / Squad / Specialties:
- Main naming constraints:
  - 姓名型 transliteration rule:
  - Chinese voice-chat constraints:
  - main-name / alias distinction:
```

Keep the packet factual. Do not include early favorites, leader preferences, or another persona's candidates.

## Candidate Generation: Single-Thread Mode

For each target operator:

1. Each active persona gives exactly 3 candidates.
2. Each candidate must include a short reason tied to:
   - persona fit,
   - BIO or character arc,
   - codename meaning or original-language meaning,
   - ability/playstyle,
   - Chinese voice fluency.
3. For 姓名型 codenames, at least one candidate from each persona must preserve or refine transliteration unless the user explicitly requests non-name aliases only.
4. Clearly label whether a candidate is intended as:
   - 主译名,
   - 风格名,
   - 玩家外号,
   - 技能名.

## Candidate Generation: Subagent Mode

For each target operator, the main thread launches independent persona subagents in parallel when possible.

Subagent isolation rules:

1. One persona per subagent.
2. Each persona subagent receives:
   - the neutral operator evidence packet,
   - that persona's `references/persona.md`,
   - `references/operator-naming-workflow.md`,
   - this candidate output schema.
3. Persona subagents must not see other personas' candidates, vote totals, or the intended decision persona.
4. Persona subagents produce exactly 3 candidates and one persona-level first choice.
5. The main thread does not rewrite candidate names, except for trivial normalization of whitespace or punctuation.

Persona subagent prompt contract:

```md
You are the <persona> naming agent for Rainbow Six operator naming.

Use the attached operator evidence packet and your persona reference only.
Give exactly 3 Chinese candidate names.
Respect codename type:
- 姓名型: at least one candidate must preserve/refine transliteration as 主译名.
- 绰号/称号型: adapt meaning and persona style.
- 混合型: preserve identity first, then style.

Return only this schema:

## Persona
<persona name>

## Candidates

1. 名字:
   类型: 主译名 / 风格名 / 玩家外号 / 技能名
   理由:
   BIO 依据:
   原文含义:
   玩法贴合:
   语音风险:

2. 名字:
   类型:
   理由:
   BIO 依据:
   原文含义:
   玩法贴合:
   语音风险:

3. 名字:
   类型:
   理由:
   BIO 依据:
   原文含义:
   玩法贴合:
   语音风险:

## Persona Vote
首选:
理由:
```

Agent-runner compatibility:

- **Codex native subagents**: use one subagent per persona. Do not pass other persona outputs to candidate agents.
- **Claude Code or external runners**: use the same prompt contract and evidence packet; collect their markdown output without changing the schema.
- **Mixed runners**: allowed. The main thread treats all persona outputs as schema-compatible ballots.

## Main-Thread Aggregation

After all persona outputs for one operator are collected, the main thread aggregates. It must not add new names unless needed to preserve a codename identity rule that every persona missed.

Aggregation steps:

1. Verify every active persona returned exactly 3 candidates.
2. Normalize obvious variants only for clustering; preserve original candidate text.
3. Cluster similar candidates by semantic direction, not only exact wording.
4. Count:
   - persona first-choice votes,
   - strong secondary support,
   - support for 主译名 / 风格名 / 玩家外号 / 技能名 layers.
5. Identify the top 2-3 clusters and the main disagreement.
6. Prepare a decision packet.

Decision packet shape:

```md
# Decision Packet

- Operator:
- Dossier path:
- Codename type:
- Key evidence:
- Active personas:
- Candidate table:
  - persona:
  - candidate:
  - type:
  - reason summary:
  - persona first choice: yes/no
- Clustered vote summary:
- Top contenders:
- Naming risks:
- Required final output:
  - final name:
  - classification:
  - why it beats alternatives:
```

## Voting

1. Cluster similar candidates by semantic direction, not only exact wording.
   - Example: `火垒`, `火堡`, and `燃垒` are one fire-fortress cluster.
   - Example: `塔强卡` and `塔昌卡` are one transliteration cluster.
2. Count support from persona first choices and strong secondary candidates.
3. Explain the top 2-3 clusters with:
   - what they preserve,
   - what they lose,
   - whether they work as 主译名 or only as aliases.
4. Voting informs the result but does not mechanically bind it when the user named a decision persona.

## Decision Persona

If the user names a decision persona, that persona makes the final decision after voting.

- In Subagent mode, launch a separate decision subagent for the named persona and give it only the decision packet plus that persona's reference rules.
- The decision subagent may overrule raw vote count if a leading candidate violates that persona's standards, loses codename identity, or fails Chinese voice use.
- The decision must explicitly say why the winning name defeats the nearest alternatives.
- Keep the decision voice stylistically recognizable but do not endorse harmful ideology, violence, hate, or real-world abuse.
- If the decision persona is also one of the candidate personas, do not reuse its candidate subagent output as the final decision. Launch or simulate a separate decision pass so it can evaluate all ballots.

If no decision persona is named, choose the highest-scoring candidate across:

1. codename identity,
2. ability/playstyle fit,
3. BIO/persona fit,
4. Chinese voice fluency,
5. distinctiveness from existing operator names.

## Processing a Batch

For multiple target operators:

1. Maintain a visible or internal queue of operator names.
2. Process exactly one operator through evidence, candidates, aggregation, and decision before moving to the next.
3. Carry forward only finalized names and documented naming rules, not raw debates that could bias later operators.
4. At the end, produce a compact final table for the whole batch.

## Final Output

For each operator, end with:

1. `最终名`
2. `主译名 / 风格名 / 玩家外号 / 技能名` classification
3. one-sentence reason
4. top alternatives and why they lost
5. dossier path used as evidence

For batch requests, include a compact final table:

| 英文 | 最终名 | 类型 | 决策理由 |
|---|---|---|---|
