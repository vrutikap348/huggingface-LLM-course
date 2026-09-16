# Chapter 11: Fine-tune Large Language Models

*Estimated study time: ~6-8 hours*

This is where the course shifts fully from BERT-style task fine-tuning to modern instruction/chat fine-tuning of decoder-only LLMs.

## Chat templates

Instruction-tuned models expect input formatted with a specific chat template (special tokens marking system/user/assistant turns). `tokenizer.apply_chat_template()` applies the correct template for a given checkpoint automatically.

```python
messages = [
    {"role": "user", "content": "Explain LoRA in one sentence."}
]
prompt = tokenizer.apply_chat_template(messages, tokenize=False, add_generation_prompt=True)
```

## Supervised fine-tuning (SFT) with TRL

The TRL library's `SFTTrainer` wraps supervised fine-tuning on instruction/response pairs behind an interface very similar to `Trainer`, but adds LLM-specific handling like packing multiple short examples into one training sequence for efficiency.

## PEFT and LoRA

Full fine-tuning of a multi-billion-parameter model needs enormous GPU memory. LoRA (Low-Rank Adaptation) freezes the original weights and injects small trainable low-rank matrices into selected layers, cutting trainable parameters (and memory) by orders of magnitude while keeping most of full fine-tuning's quality. PEFT is the Hugging Face library that implements LoRA and related methods (QLoRA, prefix tuning, etc.).

```python
from peft import LoraConfig, get_peft_model

lora_config = LoraConfig(r=8, lora_alpha=16, target_modules=["q_proj", "v_proj"])
model = get_peft_model(base_model, lora_config)
model.print_trainable_parameters()  # typically well under 1% of total params
```

## Evaluation

Beyond loss, LLM evaluation covers benchmark suites (MMLU, HellaSwag, TruthfulQA, etc.) and, increasingly, LLM-as-a-judge setups where a stronger model scores the outputs of the one being evaluated.

---
[← Chapter 10](chapter-10-curate-datasets.md) | [Back to index](README.md) | [Next: Chapter 12 →](chapter-12-reasoning-models.md)
