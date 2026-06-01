# paper-read-skill

An AI agent skill-set for **deep, rigorous reading of academic research papers and technical blog posts**. Drop it into Cursor, Claude Code, Codex, or OpenCode — then hand it a paper URL, PDF, DOI, or blog link and get a rich, exhaustive analysis in Chinese prose.

## What it does

The agent auto-routes to a type-specific analysis framework based on what you give it:

### 📄 Research Papers (`paper-analysis` skill)

| Paper type | What the agent does |
|---|---|
| **Benchmark** | Dissects dataset construction, evaluation protocols, metrics (with LaTeX formulas), reproducibility risk |
| **Methodology / Algorithm** | Unpacks architecture, training strategy, technical innovation; situates in the research timeline |
| **Survey / Opinion** | Audits argument structure, coverage gaps, author biases |

For every paper the agent:
- Traces the **full citation network** — direct baselines are mandatory, contemporaneous work is searched
- **Profiles core contributors** — first/corresponding author academic trajectory, prior work, Twitter/X discussion
- Reports **community signals** — citation growth, GitHub stars, endorsements from prominent researchers
- Explains every **evaluation metric** with a LaTeX formula and a concrete worked example
- Checks **GitHub repos, Hugging Face pages, and issue/discussion threads** for real-world adoption data

### 📝 Tech Blogs (`blog-reading` skill)

| Blog type | What the agent does |
|---|---|
| **Technical-research** | Explains engineering principles, assesses innovation depth and evidence strength |
| **Product-launch** | Cuts through marketing language, extracts genuine technical progress and user value |
| **Industry-opinion** | Deconstructs argument logic, surfaces unstated assumptions, presents countervoices |
| **Case-story** | Separates PR polish from real field experience, surfaces transferable patterns |

Output is **fluent Chinese prose** — no markdown bullet lists in the main body, coherent paragraphs with logical transitions, as if narrated by a senior technical editor to a peer.

## Example usage

```
# In Claude Code or Cursor:
Read this paper: https://arxiv.org/abs/2305.10601
```

```
Analyze this blog post: https://cursor.sh/blog/shadow-workspace
```

## Install

```bash
npx skills add Ayanami0730/paper-read-skill -g
```

Or copy `skills/` subdirectories manually to `~/.cursor/skills/`.

## Compatible runtimes

Cursor · Claude Code · OpenAI Codex · OpenCode
