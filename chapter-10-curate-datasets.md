# Chapter 10: Curate High-Quality Datasets

*Estimated study time: ~4-6 hours*

A newer chapter focused on data quality rather than model architecture, on the premise that fine-tuning results depend more on data quality than on almost anything else.

## Argilla

Argilla is an open-source tool for human-in-the-loop data annotation and review — filtering noisy examples, resolving label disagreements, and building feedback loops between model predictions and human correction.

## Key data-curation practices covered

- De-duplicating near-identical examples so the model doesn't over-index on repeated patterns.
- Filtering low-quality or toxic content before it reaches training.
- Balancing class/label distribution so the model isn't skewed toward the majority case.
- Synthetic data generation using a stronger LLM to expand or diversify a smaller hand-labeled seed set.

---
[← Chapter 9](chapter-09-building-demos.md) | [Back to index](README.md) | [Next: Chapter 11 →](chapter-11-fine-tune-llms.md)
