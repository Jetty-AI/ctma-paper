# Cascading Temporal Memory Architecture (CTMA)

**A Biologically-Inspired Framework for Persistent, Adaptive Memory in AI Systems**

📄 [Read the Full Paper (PDF)](./CTMA_arXiv_Paper.pdf) | 🌐 [gutbut.com](https://gutbut.com)

---

## Abstract

Contemporary large language models (LLMs) suffer from a fundamental architectural constraint: the absence of persistent, user-adaptive memory. Despite advances in reasoning and generation, every conversation begins from a blank slate. Context windows offer a fixed-length buffer but impose hard boundaries on temporal continuity, provide no mechanism for importance-weighted retention, and fail to model evolving information salience over time.

We introduce the **Cascading Temporal Memory Architecture (CTMA)**, a novel three-tier memory framework that draws on principles from cognitive psychology, neuroscience, and information theory to construct a longitudinal, user-specific knowledge graph with biologically-inspired decay dynamics. CTMA implements a memory lifecycle spanning **ephemeral**, **cascading**, and **permanent** storage tiers, governed by a temporal decay function modulated by behavioral signals, recency, frequency, and contextual importance.

### Directional Results (Prior Iterations, 2023–2024, n≈2,500)

*The following observations are from earlier builds of the platform (including Kaya Tech) and are presented as directional findings. The architecture has since been rebuilt and a formal validation study is underway.*

| Metric | Observed Result |
|--------|--------|
| Satisfaction vs. memoryless baseline | **~+34%** |
| Satisfaction vs. naïve RAG | **~+19%** |
| Decay–relevance correlation (Spearman ρ) | **~0.71** |
| 30-day retention lift (high-graph users) | **~2.4×** |
| Promotion accuracy at 60 days | **~91%** |

---

## Core Architecture

CTMA organizes memory into three tiers:

┌─────────────────────────────────────────────────────┐
│                   EPHEMERAL TIER                     │
│         Session-scoped · Full fidelity               │
│              Hard expiry on session end               │
└──────────────────────┬──────────────────────────────┘
                       │ Extraction Pipeline
                       ▼
┌─────────────────────────────────────────────────────┐
│                  CASCADING TIER                       │
│     Days to months · Modulated exponential decay      │
│  S(m,t) = S₀·e^(−λΔt) + αF(m,t) + βB(m,t) + γC(m,t) │
│                                                       │
│  ┌─────────┐  ┌──────────┐  ┌────────────────────┐  │
│  │ Frequency│  │Behavioral│  │   Co-Activation    │  │
│  │Reinforce │  │ Signals  │  │   (Graph Edges)    │  │
│  └─────────┘  └──────────┘  └────────────────────┘  │
└──────────┬──────────────────────────┬───────────────┘
    Promote │ (S > T↑ for 30 days)    │ Demote (S < T↓)
           ▼                          ▼
┌─────────────────────┐    ┌──────────────────┐
│   PERMANENT TIER    │    │     ARCHIVE      │
│ Immune to decay     │    │  Garbage collect  │
│ Always in context   │    │                  │
└─────────────────────┘    └──────────────────┘

---

## The Salience Function

The core equation governing memory dynamics in the cascading tier:

**S(m, t) = S₀(m) · e^(−λ(m) · Δt) + α · F(m, t) + β · B(m, t) + γ · C(m, t)**

Where:
- **S₀(m)** — Initial importance score (semantic category, emotional valence, novelty)
- **λ(m)** — Memory-specific decay rate, dynamically modulated by access frequency and importance
- **F(m, t)** — Frequency reinforcement (spacing effect)
- **B(m, t)** — Behavioral signals (corrections, revisitations, engagement, emotional markers)
- **C(m, t)** — Contextual co-activation (spreading activation along knowledge graph edges)

---

## Behavioral Signal Types

| Signal | Weight | Description |
|--------|--------|-------------|
| Explicit correction | 2.0 | User corrects system output |
| Explicit save/pin | 2.5 | User saves information |
| Contradiction | 1.8 | New info conflicts with existing memory |
| Revisitation | 1.5 | Referenced across independent sessions |
| Emotional valence | 1.2 | Strong emotional response detected |
| Engagement duration | 1.0 | Extended interaction time |

---

## Paper Details

- **Title:** Cascading Temporal Memory Architecture: A Biologically-Inspired Framework for Persistent, Adaptive Memory in AI Systems
- **Published:** March 2026
- **Pages:** 13
- **References:** 22 cited works
- **Format:** LaTeX source + compiled PDF

---

## Citation
```bibtex
@article{gutbut2026ctma,
  title={Cascading Temporal Memory Architecture: A Biologically-Inspired Framework for Persistent, Adaptive Memory in AI Systems},
  author={gutbut.com Research},
  year={2026},
  month={March},
  url={https://github.com/Jetty-AI/ctma-paper}
}
```

---

## References

Key works cited in this paper include:

- Vaswani et al. (2017) — *Attention Is All You Need*
- Graves et al. (2014) — *Neural Turing Machines*
- Anderson & Schooler (1991) — *Reflections of the Environment in Memory*
- Lewis et al. (2020) — *Retrieval-Augmented Generation*
- Park et al. (2023) — *Generative Agents*
- Packer et al. (2023) — *MemGPT*
- Ebbinghaus (1885) — *Memory: A Contribution to Experimental Psychology*

See the full paper for the complete bibliography of 22 references.

---

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — you are free to share and adapt with attribution.

---

**Contact:** hello@gutbut.com | [gutbut.com](https://gutbut.com)
