# Chapter 12: Build Reasoning Models

*Estimated study time: ~6-8 hours*

The newest and most advanced chapter, on training models to reason through reinforcement learning rather than only imitating labeled examples.

## Background: RLHF and preference optimization

Reinforcement Learning from Human Feedback (RLHF) fine-tunes a model against a reward signal derived from human preferences, historically via PPO. Direct Preference Optimization (DPO) is a simpler alternative that skips training a separate reward model and instead optimizes directly on pairs of preferred/rejected responses.

## The DeepSeek-R1 "aha moment"

The chapter references the DeepSeek-R1 paper's widely-discussed observation that pure reinforcement learning, with no supervised chain-of-thought examples at all, can lead a model to spontaneously develop longer, self-correcting reasoning traces once it is simply rewarded for reaching the correct final answer.

## GRPO (Group Relative Policy Optimization)

GRPO, introduced in the DeepSeekMath paper, is a reinforcement-learning algorithm that removes the need for a separate value/critic model (which PPO requires). Instead, it samples a group of candidate completions for the same prompt and uses the relative reward ranking within that group as the training signal — considerably cheaper to run than PPO at LLM scale.

## Implementing GRPO with TRL

TRL provides a `GRPOTrainer` that takes a base model, a reward function (or several, e.g. "is the final answer correct" plus "is the output properly formatted"), and a dataset of prompts, and runs the group-sampling + relative-advantage training loop.

```python
from trl import GRPOConfig, GRPOTrainer

def correctness_reward(completions, answers, **kwargs):
    return [1.0 if c.strip() == a.strip() else 0.0 for c, a in zip(completions, answers)]

trainer = GRPOTrainer(
    model=model, reward_funcs=[correctness_reward],
    args=GRPOConfig(output_dir="reasoning-model"), train_dataset=dataset,
)
trainer.train()
```

> **Note:** This chapter assumes comfort with everything from Chapter 11 (SFT/LoRA) — GRPO is generally applied on top of an already instruction-tuned model, not from a raw base model.

---
[← Chapter 11](chapter-11-fine-tune-llms.md) | [Back to index](README.md) | [Next: Overall Takeaways →](takeaways.md)
