# Hugging Face LLM Course – Notes

Personal study notes from the [Hugging Face LLM Course](https://huggingface.co/learn/llm-course) (formerly the Hugging Face NLP Course) — a free, 13-part curriculum (Chapter 0 through Chapter 12) covering the Transformers ecosystem end to end: tokenization, model architecture, fine-tuning, dataset curation, and reasoning-model training with reinforcement learning.

Code snippets in these notes are simplified/paraphrased for clarity and are not verbatim excerpts from the course material.

## Contents

| # | Chapter | Topic |
|---|---------|-------|
| 0 | [Setup](chapter-00-setup.md) | Environment setup, Hub account |
| 1 | [Transformer Models](chapter-01-transformer-models.md) | `pipeline()`, architectures, bias & limitations |
| 2 | [Using Transformers](chapter-02-using-transformers.md) | Tokenizer → model → post-processing |
| 3 | [Fine-tuning a Pretrained Model](chapter-03-fine-tuning.md) | Trainer API, manual training loop |
| 4 | [Sharing Models and Tokenizers](chapter-04-sharing-models.md) | Hugging Face Hub, model cards |
| 5 | [The Datasets Library](chapter-05-datasets-library.md) | Loading, streaming, FAISS semantic search |
| 6 | [The Tokenizers Library](chapter-06-tokenizers-library.md) | BPE, WordPiece, Unigram, training a tokenizer |
| 7 | [Classical NLP Tasks](chapter-07-classical-nlp-tasks.md) | NER, MLM, translation, summarization, QA |
| 8 | [How to Ask for Help](chapter-08-how-to-ask-for-help.md) | Debugging, forums, GitHub issues |
| 9 | [Building and Sharing Demos](chapter-09-building-demos.md) | Gradio, Hugging Face Spaces |
| 10 | [Curate High-Quality Datasets](chapter-10-curate-datasets.md) | Argilla, data quality practices |
| 11 | [Fine-tune Large Language Models](chapter-11-fine-tune-llms.md) | Chat templates, SFT, LoRA/PEFT |
| 12 | [Build Reasoning Models](chapter-12-reasoning-models.md) | RLHF, DPO, GRPO, TRL |

See [`takeaways.md`](takeaways.md) for an overall summary and references.

## Source

- Course: https://huggingface.co/learn/llm-course
- Transformers docs: https://huggingface.co/docs/transformers
- TRL docs: https://huggingface.co/docs/trl
- PEFT docs: https://huggingface.co/docs/peft
