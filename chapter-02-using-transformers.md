# Chapter 2: Using Transformers

*Estimated study time: ~4-6 hours*

This chapter opens up what `pipeline()` does internally, in three stages: tokenizer → model → post-processing.

## Behind the pipeline

1. **Tokenizer** converts raw text into numerical input IDs (plus an attention mask).
2. **Model** takes those IDs and produces logits (raw, unnormalized scores).
3. **Post-processing** turns logits into something usable — e.g. softmax + label mapping for classification.

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification

checkpoint = "distilbert-base-uncased-finetuned-sst-2-english"
tokenizer = AutoTokenizer.from_pretrained(checkpoint)
model = AutoModelForSequenceClassification.from_pretrained(checkpoint)

inputs = tokenizer("This course is great!", return_tensors="pt")
outputs = model(**inputs)
```

## Models

The `AutoModel` classes (`AutoModel`, `AutoModelForSequenceClassification`, `AutoModelForCausalLM`, etc.) automatically pick the right model architecture class based on the checkpoint's config — you rarely need to import a model-specific class directly.

## Tokenizers

- **Word-based tokenization**: simple but produces huge vocabularies and can't handle unseen words well.
- **Character-based tokenization**: tiny vocabulary but loses a lot of meaning per token and produces very long sequences.
- **Subword tokenization** (used by almost all modern models): splits rare words into meaningful sub-pieces while keeping common words whole — the practical middle ground.

## Handling multiple sequences

Models expect batched, rectangular input, so shorter sequences are padded to match the longest one in a batch, and an `attention_mask` tells the model which tokens are real vs. padding so it can ignore padding during attention computation. Very long sequences that exceed a model's context window need to be truncated.

```python
batch = tokenizer(
    ["Short text.", "A somewhat longer example sentence."],
    padding=True, truncation=True, return_tensors="pt",
)
```

---
[← Chapter 1](chapter-01-transformer-models.md) | [Back to index](README.md) | [Next: Chapter 3 →](chapter-03-fine-tuning.md)
