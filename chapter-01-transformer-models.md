# Chapter 1: Transformer Models

*Estimated study time: ~4-6 hours*

## NLP vs. LLMs

NLP (Natural Language Processing) is the broad field of getting computers to work with human language — tasks like sentiment analysis, named entity recognition, translation, and summarization. LLMs (Large Language Models) are a subset of NLP models distinguished by their scale (parameters + training data) and their ability to perform many tasks with little or no task-specific fine-tuning, largely through prompting.

## The `pipeline()` function

The fastest way to use a pretrained model from the Hub is the `pipeline()` helper, which bundles preprocessing, model inference, and post-processing into one call.

```python
from transformers import pipeline

classifier = pipeline("sentiment-analysis")
classifier("I really enjoyed this course.")
# [{'label': 'POSITIVE', 'score': 0.999...}]
```

Pipelines exist for text generation, zero-shot classification, fill-mask, named entity recognition, question answering, summarization, and translation, among others.

## How Transformers work (high level)

- Transformers are trained as language models on large amounts of raw, unlabeled text (self-supervised learning), then adapted to a specific task via transfer learning.
- Pretraining is expensive and mostly done by large labs; fine-tuning a pretrained model on a smaller, task-specific dataset is far cheaper and is what most practitioners actually do.
- Transfer learning: instead of training from scratch, start from a pretrained checkpoint and continue training on your own data — this needs less data, time, and compute, and gives better results than training from zero.

## Three architecture families

| Architecture | Good at | Examples |
|---|---|---|
| Encoder-only | Understanding full sentences (classification, NER, extractive QA) | BERT, RoBERTa, DistilBERT |
| Decoder-only | Generating text one token at a time (chat, completion) | GPT family, Llama, Mistral |
| Encoder-decoder | Sequence-to-sequence tasks (translation, summarization) | T5, BART, mBART |

## Inference with LLMs

Modern decoder-only LLMs generate text autoregressively: they predict one token at a time, append it to the input, and repeat. Sampling parameters (temperature, top-k, top-p) control how deterministic vs. varied the output is.

## Bias and limitations

Pretrained models inherit biases present in their training data (which is often scraped from the internet), so outputs can reflect stereotypes around gender, race, or ideology even when the fine-tuning data is neutral. Always evaluate a model on its intended use case rather than assuming pretrained = safe.

---
[← Chapter 0](chapter-00-setup.md) | [Back to index](README.md) | [Next: Chapter 2 →](chapter-02-using-transformers.md)
