# GPT-2 Foundation

> 🙏 **Inspired by & full credit to [Sebastian Raschka](https://github.com/rasbt/LLMs-from-scratch)** — this project closely follows his *"Build a Large Language Model From Scratch"* book and code. Grateful for the clarity he brings to LLM internals.

---

## Overview

This is a **bare-bones GPT-2 implementation** focused purely on understanding the foundational mechanics of how a language model is built and trained — no pretraining at scale, no fine-tuning pipelines, no external APIs. Just the raw infrastructure running on a small dataset.

Think of it as a learning sandbox, not a production model.

---

## What's Covered

| Component | Description |
|---|---|
| **Model** | GPT-2 architecture (124M params), 12 layers, 12 heads, 256 context length |
| **Tokenizer** | OpenAI's `tiktoken` (GPT-2 BPE encoding) |
| **Loss** | Cross-entropy loss + perplexity tracking |
| **Data Pipeline** | Custom DataLoader with 90/10 train/val split on *"The Verdict"* text |
| **Training** | Simple loop with AdamW optimizer, loss evaluated every 5 steps |
| **Decoding** | Temperature scaling + Top-K sampling for controlled text generation |
| **Plots** | Train/Val loss curves and temperature behavior plots saved to `Graphs/` |

---

## Project Structure

```
GPT2-foundation/
├── GPT2.ipynb          # Main notebook
├── Graphs/
│   ├── loss-plot.pdf           # Train/Val loss over epochs
│   └── temperature-plot.pdf    # Token probability at different temperatures
└── README.md
```

---

## Stack

- **PyTorch** — model, training, and inference
- **tiktoken** — tokenization
- **matplotlib** — visualizations
- **NumPy** — utilities

---

## Key Observations

- Training loss drops steadily; validation loss starts to diverge after ~6 epochs, a classic sign of **overfitting on small data** — expected here.
- Temperature `< 1` → confident, repetitive output. Temperature `> 1` → creative, unpredictable output.
- Top-K sampling keeps generation grounded while still allowing variety.

---

## Disclaimer

This is intentionally simple. The dataset is tiny (~5K tokens), the model is untrained from scratch on small compute, and the goal is **understanding the mechanics** — not building a useful language model.

---

Thanks again [Sebastian Raschka](https://github.com/rasbt) — genuinely couldn't have understood this stuff without your work.

date:2026-02-26  11:45PM