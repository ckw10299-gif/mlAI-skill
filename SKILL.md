---
name: mlAI-skill
description: Use when analyzing game ad reference videos or AI creative materials for user acquisition, extracting visual/story/AI implementation anchors, classifying sub-directions, and migrating the effective mechanism into the user's own product without copying surface elements. Trigger for 买量素材分析, AI素材分析, 参考素材迁移, 方向池, 产品分析+迁移, 素材本地化, or when the user provides a reference video folder and product brief.
---

# 买量素材 AI 分析与迁移

Use this skill to analyze reference ad materials, especially AI-generated game ads, and turn them into grounded, product-specific creative directions.

Core rule: **extract why the reference works, then migrate the working mechanism into the product. Do not copy surface elements or reuse conclusions from another batch.**

## Required Inputs

### Brief Gate

Before using this skill for any real migration, the user must provide a brief for their own game/product. Do not begin product migration from reference materials without a current product brief.

If the user only provides reference videos/folders and asks for migration, first ask for the brief using the template below. If the user already provided a brief in the current conversation, summarize it and confirm you will use that version. A newer brief always overrides older defaults.

Required brief template:

```text
产品/游戏名称：
类型：
目标用户：
投放市场：
平台：
核心玩法：
前 30 秒真实体验：
可以展示的机制/卖点：
不能展示或不能承诺：
可用素材：
希望优化的指标：
其他限制：
```

Optional but useful:

```text
现有主角/角色设定：
现有美术风格：
已有游戏录屏/素材路径：
本次更想测试：CTR / 付费 / 降低单价 / 留存 / 某类人群
```

After the brief is available, collect:

- Reference folder or files: videos/images from the same direction or mixed directions.
- Direction name: what this batch is studying.
- Optional constraints: output format, Excel/Feishu/local doc, whether to include production method.

If the user provides multiple videos in one folder:

- Treat them as one batch.
- First classify sub-directions if the batch is mixed.
- Do not analyze each video in isolation unless the user asks for single-video work.

## Usage Guide

Recommended prompt:

```text
使用 mlAI-skill。

产品 brief：
产品/游戏名称：
类型：
目标用户：
投放市场：
平台：
核心玩法：
前 30 秒真实体验：
可以展示的机制/卖点：
不能展示或不能承诺：
可用素材：
希望优化的指标：
其他限制：

参考视频文件夹：
方向名：
这些视频是其他游戏参考素材，帮我先分类，再分析 AI锚点/剧情锚点/视觉锚点/实现方式，最后迁移到我的产品。
输出形式：聊天总结 / Excel / 飞书文档 / 都要
```

For a single video:

```text
使用 mlAI-skill。下面是我的产品 brief：...
参考视频：<file path>
请拆解这个视频的节奏、画面变化、AI实现锚点，并迁移成一个适合我产品的买量脚本 idea。
```

For an existing product whose brief is already known in the conversation:

```text
继续使用上次的产品 brief。
参考视频文件夹：
方向名：
这批是同一方向参考素材，请重新分析这一批，不要沿用上一批方向池。
```

## Workflow

### 1. Establish Product Ground Truth

Before migration, summarize the product's real usable hooks:

- Core loop: what the player actually does.
- Early experience: what can truthfully be shown in the first 30 seconds.
- Sellable systems: collection, battle, upgrade, social, reward, etc.
- User priorities: CTR, payment, CPA, retention, audience fit.
- Hard limits: anything not in the product must not appear as a promise.

For 《闪耀吧噜咪》, the following is a known example brief only. Do not use it as a substitute for the current task's brief unless the user explicitly provides it again, says to continue using the previous brief, or confirms this is the brief to use:

- Genre: pet-catching game.
- Core: catching Lummi, collecting, evolving, pet battle, lineup strategy.
- Early experience: newbie guidance, starter choice, adventure, maps/home unlock, encounter and catch Lummi.
- Sellable hooks: many Lummi, rarity, attributes, illustrated book, evolution, emotional value, adventure maps, random events, thousand-times catch, fair battle, attribute counters, weather, manual skills, quick pet switch, lineups, ranking/PVE, exchange/social, rewards.
- Avoid invented systems or people unless the user confirms them.

### 2. Classify Reference Materials

For each batch, classify the actual material types before migration.

Common classes:

- Evolution/progression full film.
- AI comedy pre-hook + gameplay/real material.
- Disaster diary/worldview.
- Family/help-seeking/emotional rescue.
- Last survivor/monologue.
- Absurd object/creature spectacle.
- Competitive comparison/battle flex.
- Reverse-routine/low-status comeback.

Classification must come from the videos. Do not import classes from earlier batches if they are not present.

### 3. Decompose Each Class

For each class or representative video, extract:

- First 3-second hook: why the user stops.
- Rhythm: opening image -> conflict -> escalation -> operation/choice -> payoff -> game bridge.
- Visual anchor: the most memorable visible object/person/creature/environment/change.
- Story anchor: the emotional or narrative engine.
- Transformation form: what changes over time and how clearly the change reads.
- Product bridge: what gameplay or product feature the reference eventually points to.
- Audience signal: who it attracts and whether that user is valuable for the product.
- Risk: misleading expectation, wrong audience, weak payment, overused visuals, platform risk.

### 4. Analyze AI Implementation

Always include the production lens when the source looks AI-made or when the user asks for AI anchors.

Answer:

- Implementation form: AI image-to-video, text-to-video, static image motion, character consistency, local morph, exaggerated body/object deformation, compositing with gameplay, or real gameplay stitched after pre-hook.
- AI visual anchor: the image element AI makes cheap, strange, scalable, or attention-grabbing.
- AI story anchor: the repeatable narrative setup enabled by AI.
- Required assets: number/type of images, character sheets, scenes, product clips, UI/gameplay captures.
- Reproducibility: easy/medium/hard, and why.
- Migration idea: what AI should generate for the product, not what the reference literally showed.

For migration, prefer anchors that are native to the product:

- Character state changes.
- Lummi injury/rescue/catching/evolution.
- Rare Lummi appearance.
- Map/weather/environment mutation.
- Battle outcome and lineup counter.
- Funny failed-catching behavior.

### 5. Migrate Mechanism, Not Surface

Use this chain:

`reference effective mechanism -> product-relevant equivalent -> concrete hook -> gameplay bridge -> risk check`

Examples:

- Shelter evolution is not copied as a building if the product is not about shelters. Migrate the visible growth mechanic into Lummi evolution, character upgrade, lineup power growth, or map unlock.
- AI comedy pre-hook is not copied as urine/bald-man content. Migrate the absurdity into a product-native funny anchor: unlucky trainer, strange Lummi, failed catch, wrong item, non-rare reversal.
- Family rescue should not be forced into starter choice. If the reference is help-seeking, migrate to injured/abandoned/endangered Lummi rescue.
- Disaster diary can migrate only if there is a product bridge: map mutation, weather anomaly, Lummi ecology crisis, dangerous area with rare Lummi.

If no product-relevant bridge exists, mark it as low priority or not recommended.

## Output Structure

Use the format the user asks for. If unspecified, provide a concise chat summary and offer Excel/Feishu output.

For Excel/structured docs, use these sheets/tables:

1. `素材分类`
   - sub-direction, source evidence, hook type, suitable material form.
2. `参考素材拆解`
   - video/class, first 3s hook, rhythm, visual anchor, story anchor, transformation, AI implementation, audience, risk.
3. `产品迁移方向池`
   - direction name, derived source, product equivalent, concrete hook, visual anchor, story anchor, material form, gameplay bridge, priority, risk.
4. `AI实现与锚点迁移`
   - reference AI method, reference anchor, product AI anchor, required assets, cost/difficulty, production notes.

Each direction must visibly derive from the reference analysis. Do not add unrelated product brainstorm items to the direction pool.

## Quality Rules

- Do not reuse another batch's Excel conclusions or direction pool.
- Do not invent product systems, characters, NPCs, or selling points.
- Do not force a migration when the mechanism does not fit.
- Do not leave competitor-specific surface elements in the migrated title unless the product truly has them.
- Distinguish "CTR hook" from "payment hook"; they are not always the same.
- Include enough concrete detail for a buyer/creative producer to script it.
- When the user criticizes a direction as unrelated, revise by returning to the reference evidence first.

## Quick Checklist

Before finalizing, confirm:

- Did every migrated direction trace back to a reference class or anchor?
- Are visual anchors and story anchors both named?
- Is AI implementation analyzed where relevant?
- Is the product bridge real and showable?
- Are non-fitting ideas downgraded or removed?
- Is the output easy to use for script generation or asset collection?
