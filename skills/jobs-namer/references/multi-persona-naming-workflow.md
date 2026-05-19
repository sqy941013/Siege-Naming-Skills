# Multi-Persona Batch Naming Workflow

Use this workflow when the user asks for:

- 所有人格 / 多个人格 / 多人翻译 / 轮流起名,
- 批量起名 for multiple operators,
- 每个人格给出 3 个名字,
- 投票 / consensus / ranked choice,
- a designated decision persona, such as `由斯大林决策`.

This workflow can be used for one operator or many operators.

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

For every target operator, read the local dossier from `resources/bios` before naming. Extract:

- codename and codename type,
- real name,
- birthplace and biography signals,
- original-language or English meaning when relevant,
- Unique Ability and playstyle,
- Side, Squad, and Specialties.

Always run the Codename Type Pass from `operator-naming-workflow.md` before generating candidates.

## Candidate Generation

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

- The decision persona may overrule raw vote count if a leading candidate violates that persona's standards, loses codename identity, or fails Chinese voice use.
- The decision must explicitly say why the winning name defeats the nearest alternatives.
- Keep the decision voice stylistically recognizable but do not endorse harmful ideology, violence, hate, or real-world abuse.

If no decision persona is named, choose the highest-scoring candidate across:

1. codename identity,
2. ability/playstyle fit,
3. BIO/persona fit,
4. Chinese voice fluency,
5. distinctiveness from existing operator names.

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
