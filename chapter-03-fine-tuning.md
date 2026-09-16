# Chapter 3: Fine-tuning a Pretrained Model

*Estimated study time: ~6-8 hours*

This is where the course moves from using models to training them on a custom dataset.

## Processing the data

Datasets from the Hub are loaded with the `datasets` library, then tokenized in batches with `.map()` so the whole dataset doesn't need to be tokenized eagerly. A `DataCollatorWithPadding` pads each batch dynamically at collation time rather than padding the entire dataset to a fixed length upfront, which is more memory-efficient.

```python
from datasets import load_dataset
from transformers import AutoTokenizer, DataCollatorWithPadding

raw_datasets = load_dataset("glue", "mrpc")
tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")

def tokenize_fn(batch):
    return tokenizer(batch["sentence1"], batch["sentence2"], truncation=True)

tokenized = raw_datasets.map(tokenize_fn, batched=True)
collator = DataCollatorWithPadding(tokenizer=tokenizer)
```

## Training with the Trainer API

The high-level `Trainer` class wraps the entire training loop — optimizer, learning-rate schedule, evaluation, checkpointing — behind a small set of `TrainingArguments`.

```python
from transformers import TrainingArguments, Trainer

args = TrainingArguments("test-trainer", eval_strategy="epoch")
trainer = Trainer(
    model, args, train_dataset=tokenized["train"],
    eval_dataset=tokenized["validation"], data_collator=collator,
)
trainer.train()
```

## A full training loop, without Trainer

The course also walks through writing the loop manually with plain PyTorch (`DataLoader`, `AdamW` optimizer, a linear learning-rate scheduler, and `model.to(device)`), and then shows how the `Accelerate` library lets the same script run unchanged on CPU, single-GPU, multi-GPU, or TPU by wrapping the objects in an `Accelerator`.

> **Note:** Using the Trainer API is the fastest path for standard tasks; writing the manual loop is worth doing once, since it makes it much easier to debug training later when something goes wrong.

---
[← Chapter 2](chapter-02-using-transformers.md) | [Back to index](README.md) | [Next: Chapter 4 →](chapter-04-sharing-models.md)
