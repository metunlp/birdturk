# BIRDTurk: Adaptation of the BIRD Text-to-SQL Dataset to Turkish

<p align="center">
  <img src="images/birdturk.jpeg" alt="BIRDTurk" width="250">
</p>

## Overview

**BIRDTurk** is a Turkish adaptation of the **BIRD (BigBench for Relational Databases)** Text-to-SQL benchmark.  
The goal of this project is to evaluate and analyze **Text-to-SQL model performance in Turkish**, a morphologically rich and low-resource language, while preserving the full structural and logical complexity of the original BIRD dataset.

This repository documents the **arXiv version** of the paper, which has been **accepted to EACL 2026 (SIGTURK)**.  
The final camera-ready version will be published in the official conference proceedings.

Paper (arXiv): https://arxiv.org/abs/2602.03633  
Conference: **EACL 2026 – SIGTURK**

---

## Motivation

Most state-of-the-art Text-to-SQL models:
- Are trained and evaluated primarily on English datasets
- Show strong performance in English
- Degrade significantly in morphologically rich languages such as Turkish

**BIRDTurk** is designed to:
- Quantify performance degradation caused purely by language shift
- Identify systematic cross-lingual failure modes
- Provide a reproducible Turkish benchmark for Text-to-SQL research

---

## Dataset Description

### Original BIRD Dataset
- **12,751** natural language questions
- **95** real-world databases
- **37** different domains
- Complex SQL queries (joins, nested queries, aggregations)
- Large-scale (~33.4 GB)

### BIRDTurk Dataset
- One-to-one **Turkish translation** of BIRD questions
- **Identical SQL queries** (no modification)
- Database schemas and execution logic fully preserved
- Translation validated for **semantic and execution equivalence**

> Design principle: **Only the natural language layer changes. SQL and databases remain untouched.**

---

## Translation and Validation

- Controlled human-in-the-loop translation process
- Focus on:
  - Semantic fidelity
  - Schema alignment
  - Query executability
- Statistical sampling with human evaluators
- **98.15% translation accuracy** at **95% confidence level**

This ensures the benchmark measures **language effects**, not translation noise.

---

## Experimental Setup

Evaluations are conducted under three paradigms:

### 1. Inference-Based Prompting
- Zero-shot / few-shot prompting
- No task-specific training
- Measures raw multilingual generalization

### 2. Agentic Multi-Stage Reasoning
- Explicit reasoning decomposition
- Tool-augmented or step-based inference
- More robust to linguistic variation

### 3. Supervised Fine-Tuning
- Fine-tuning on labeled Text-to-SQL data
- Tested with multilingual and instruction-tuned models

---

## Key Findings

### Systematic Performance Drop
- All models perform worse in Turkish than in English
- Degradation is consistent across architectures
- Confirms language representation as a primary bottleneck

### Agentic Reasoning Is More Robust
- Multi-stage reasoning reduces language sensitivity
- Improves schema grounding and intent resolution
- Still not language-agnostic, but clearly superior

### Fine-Tuning Helps — With Limits
- Multilingual pretraining alone is insufficient
- Instruction-tuned models benefit more
- Morphology and tokenization remain unresolved challenges

---

## What Differentiates BIRDTurk

| Aspect | Prior Benchmarks | BIRDTurk |
|------|------------------|----------|
| Target Language | English | Turkish |
| Dataset Scale | Small–Medium | Large-scale (BIRD-level) |
| SQL Complexity | Often simplified | Full real-world SQL |
| Cross-Lingual Control | Weak | Strictly controlled |
| Validation | Limited | Statistically verified |
| Research Focus | Accuracy only | Language-induced effects |

**BIRDTurk is a controlled cross-lingual experiment, not a simple translation.**

---

## Why Turkish Exposes Model Weaknesses

- Agglutinative morphology
- Flexible word order
- Implicit arguments
- Indirect schema references
- Subword tokenization mismatch

These properties reveal reasoning and grounding failures masked in English benchmarks.

---

## Use Cases

- Multilingual Text-to-SQL evaluation
- Cross-lingual reasoning analysis
- Agentic vs single-shot model comparison
- Turkish NL-to-SQL system development
- Methodological template for other low-resource languages

---

## Limitations

- Focused solely on Turkish
- Schemas remain English (intentionally)
- Diagnostic benchmark, not a solution

---

## Conclusion

**BIRDTurk** is the first large-scale, execution-faithful Turkish Text-to-SQL benchmark and has been **accepted to EACL 2026 SIGTURK**.  
It demonstrates that strong English Text-to-SQL performance does not translate to multilingual robustness and establishes language as a first-order challenge in structured reasoning.

---

## Citation

```bibtex
@inproceedings{birdturk2026,
  title={BIRDTurk: Adaptation of the BIRD Text-to-SQL Dataset to Turkish},
  author={Aktas, Burak and Baytekin, Mehmet Can and Kose, Suha Kagan and Ilbilgi, Omer and Yilmaz, Elif Ozge and Toraman, Cagri and Gorur, Bilge Kaan},
  booktitle={Proceedings of the 18th Conference of the European Chapter of the Association for Computational Linguistics (EACL)},
  note={Accepted to SIGTURK. arXiv:2602.03633},
  year={2026}
}

