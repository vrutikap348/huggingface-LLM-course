# Chapter 6: The 🤗 Tokenizers Library

*Estimated study time: ~4-5 hours*

Goes one level deeper than Chapter 2: how tokenizers are actually **trained**, not just used.

## Subword algorithms

| Algorithm | Idea | Used by |
|---|---|---|
| BPE (Byte-Pair Encoding) | Iteratively merges the most frequent adjacent symbol pair | GPT-2, RoBERTa |
| WordPiece | Similar to BPE but merges by likelihood gain rather than raw frequency | BERT, DistilBERT |
| Unigram | Starts from a large vocabulary and prunes tokens that hurt likelihood least | T5, ALBERT, XLNet |

## Training a new tokenizer

```python
tokenizer = old_tokenizer.train_new_from_iterator(
    text_iterator, vocab_size=25000
)
```

This is useful when moving to a new language or domain (e.g. legal or medical text) where the original vocabulary doesn't segment words efficiently.

## Fast tokenizers

Tokenizers written in Rust (the default "fast" tokenizers) expose offset mappings that trace every token back to its exact character span in the original string — essential for tasks like token classification and extractive QA where the answer must be mapped back to the source text.

---
[← Chapter 5](chapter-05-datasets-library.md) | [Back to index](README.md) | [Next: Chapter 7 →](chapter-07-classical-nlp-tasks.md)
