# paper2code

An AI agent skill that converts any arxiv paper into a minimal, citation-anchored Python implementation — faithful to what the paper actually says, honest about everything it doesn't.

## What It Does

Give it an arxiv URL or paper ID and it will:

1. **Fetch and parse** the PDF, treating appendices and figure captions as first-class sources
2. **Identify the core contribution** — the one thing the paper claims to introduce
3. **Audit every implementation detail** — classifying each as `SPECIFIED`, `PARTIALLY_SPECIFIED`, or `UNSPECIFIED` before writing a single line of code
4. **Generate citation-anchored code** where every non-trivial decision links back to a specific paper section and equation (`# §3.2, Eq. 4`)
5. **Produce a walkthrough notebook** with CPU-runnable sanity checks that quote the paper and show the corresponding code

## Try It

```bash
# Install the skill
npx skills add PrathamLearnsToCode/paper2code/skills/paper2code

# Run in your agent
/paper2code https://arxiv.org/abs/1706.03762

# With options
/paper2code 2006.11239 --framework jax --mode full
```

## What Makes It Different

Most code generation tools fill ambiguous gaps silently and confidently. paper2code refuses to. If the paper doesn't specify a hyperparameter, the generated code marks it:

```python
# [UNSPECIFIED] Paper does not state epsilon for LayerNorm — using 1e-6 (common default)
# Alternatives: 1e-5 (PyTorch default), 1e-8 (some implementations)
self.norm = nn.LayerNorm(d_model, eps=1e-6)
```

Every specified detail is traced back to the paper:

```python
# §3.2, Eq. 2 — attention_weights = softmax(QK^T / sqrt(d_k))
attn_out = self.attention(self.norm1(x))
```

## Output Structure

```
attention_is_all_you_need/
├── README.md                    # Paper summary and quick-start
├── REPRODUCTION_NOTES.md        # Ambiguity audit — every unspecified choice documented
├── requirements.txt             # Pinned dependencies
├── src/
│   ├── model.py                 # Architecture with section citations
│   ├── loss.py                  # Loss functions with equation references
│   ├── data.py                  # Dataset skeleton with preprocessing TODOs
│   ├── train.py                 # Training loop (full/educational mode)
│   └── evaluate.py              # Metric computation
├── configs/
│   └── base.yaml                # All hyperparams — cited or flagged [UNSPECIFIED]
└── notebooks/
    └── walkthrough.ipynb        # Runnable on CPU, quotes paper passages
```

## Modes

| Mode | Description |
|------|-------------|
| `minimal` (default) | Core contribution only |
| `full` | Core + training loop + data pipeline + evaluation |
| `educational` | Adds extra inline comments, theory sections in notebook |

## Worked Examples

The repo ships with fully worked examples for:
- **Attention Is All You Need** (`1706.03762`) — the original Transformer
- **DDPM** (`2006.11239`) — denoising diffusion probabilistic models

Each includes the complete generated output plus an honest `review.md` evaluating what was right and where gaps were flagged.
