# mbbb Baker Agent

A Claude Code subagent for professional pastry recipe lookup and Baker's Percentage calculation, built by an 18-year fine-dining kitchen veteran.

## What it does

- **Recipe lookup** — search a curated multilingual library (French + Chinese) by recipe name or ingredient
- **Baker's % calculation** — express every ingredient as a ratio of the base (flour, chocolate, cream, etc.)
- **Recipe scaling** — scale any formula to a target batch size (e.g. scale to 2000g flour)
- **Technique Q&A** — answer pastry-science questions (ganache ratios, mousse stability, hydrocolloid selection, meringue types, caramel temperatures) from a structured knowledge base

## Quick start

```bash
# Install the agent
cp agents/baker.md ~/.claude/agents/baker.md
cp -r scripts/ data/ /path/to/your-project/
```

Once installed, Claude Code routes pastry queries to the Baker Agent automatically.

## Example queries

```
Find the recipe for canelé
Scale this brioche to 2000g flour
Which recipes use praliné?
Why is my mousse unstable?
What ganache ratio should I use for a 70% chocolate?
```

Works in French and Chinese too — the underlying recipe library is bilingual.

## Recipe library

The agent ships with a tiered recipe library:

| Tier | Directory | Content |
|------|-----------|---------|
| Intermediate (highest quality) | `glm/intermediate/` | 60 vision-extracted bilingual recipes |
| GLM-converted | `glm/` | 139 bilingual French+Chinese recipes |
| OCR-converted | `_md/` | 97 French-only recipes (may have OCR errors) |

Recipe categories covered: entremets, tartes, choux/éclairs, chocolaterie, confiserie, viennoiserie, biscuits/cakes, macarons, salé.

## Knowledge base topics

Ganache · Mousse structure · Acidity control · Hydrocolloids · Crème pâtissière · Pâte sucrée · Pâte à choux · Caramel · Meringue · Praliné · Crème mousseline · Biscuit joconde/dacquoise

## Links

- [Repository](https://github.com/chefkannofriend-source/mbbb-baker-agent)
- [GAP manifest](https://github.com/chefkannofriend-source/mbbb-baker-agent/blob/main/agent.yaml)
