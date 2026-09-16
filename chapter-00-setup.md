# Chapter 0: Setup

*Estimated study time: ~1 hour*

This chapter is about getting a working environment ready before touching any course content.

## Two ways to work through the course

- **Notebook environment** (Google Colab, Kaggle) — zero local setup, free GPU access, good for following along quickly.
- **Local Python virtual environment** — better for long-term / production-style work, needed once projects grow beyond a single notebook.

## Local environment setup

```bash
python -m venv hf-env
source hf-env/bin/activate      # Windows: hf-env\Scripts\activate
pip install transformers datasets tokenizers accelerate evaluate
```

It's worth creating a free Hugging Face Hub account early, since later chapters push models, datasets, and Spaces to the Hub directly from code.

```bash
huggingface-cli login
```

> **Note:** Keep a separate virtual environment for this course instead of reusing an existing project env — `transformers`/`datasets` versions change often, and this avoids dependency conflicts.

---
[← Back to index](README.md) | [Next: Chapter 1 →](chapter-01-transformer-models.md)
