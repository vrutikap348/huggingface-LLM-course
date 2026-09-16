# Chapter 7: Classical NLP Tasks

*Estimated study time: ~8-10 hours*

Applies everything so far to the tasks that make up the traditional NLP toolkit, each fine-tuned with the same load → tokenize → Trainer/loop → evaluate pattern:

- **Token classification** — NER and POS tagging; labels are aligned to tokens rather than whole sentences, which needs special handling for subwords split across multiple tokens.
- **Fine-tuning a masked language model (MLM)** — domain-adapting a model like BERT on unlabeled in-domain text before fine-tuning it on a downstream task.
- **Translation and summarization** — sequence-to-sequence fine-tuning with models like T5/mBART, evaluated with BLEU and ROUGE respectively.
- **Question answering** — extractive QA, where the model predicts start/end token positions of the answer span within a context passage.
- **Training a causal language model from scratch** — what changes when there's no pretrained checkpoint to start from (tokenizer training, architecture config, and much larger data/compute requirements).
- **Debugging the training pipeline** — a systematic checklist for when loss doesn't go down: check the data first, then the batch shapes, then the loss function, then the learning rate.

> **Note:** This chapter is long mainly because each task needs its own preprocessing/label-alignment logic — the actual training code is nearly identical across all of them once the data is in the right shape.

---
[← Chapter 6](chapter-06-tokenizers-library.md) | [Back to index](README.md) | [Next: Chapter 8 →](chapter-08-how-to-ask-for-help.md)
