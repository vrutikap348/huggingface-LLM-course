# Chapter 4: Sharing Models and Tokenizers

*Estimated study time: ~2-3 hours*

Covers publishing work to the Hugging Face Hub so it can be reused (by yourself, a team, or the community).

- `push_to_hub=True` in `TrainingArguments` uploads checkpoints automatically during training.
- `model.push_to_hub("repo-name")` and `tokenizer.push_to_hub("repo-name")` upload manually at any point.
- Every repo should have a **model card** (`README.md`) describing intended use, training data, limitations, and evaluation results — this is what most users read before adopting a model.
- Repos can be public or private, and support the same git-based version control as GitHub (branches, commits, diffs).

---
[← Chapter 3](chapter-03-fine-tuning.md) | [Back to index](README.md) | [Next: Chapter 5 →](chapter-05-datasets-library.md)
