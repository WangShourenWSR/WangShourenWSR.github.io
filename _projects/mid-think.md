---
layout: page
title: Mid-Think
description: Training-free intermediate-budget reasoning through token-level triggers that induce or suppress thinking.
img: assets/img/projects/mid-think/overview.png
importance: 4
category: research
related_publications: false
github: https://github.com/uservan/Mid-Think
---

## From Two Modes to a Useful Middle Ground

Reasoning models are usually presented with a binary choice: use full think mode or suppress reasoning with no-think. This is a coarse interface. Full reasoning can be expensive, while direct answering can leave accuracy on the table. [Mid-Think: Training-Free Intermediate-Budget Reasoning via Token-Level Triggers](https://aclanthology.org/2026.findings-acl.299/) searches for an intermediate operating point without training a new model or imposing a fixed token cutoff.

<figure class="project-figure">
  <img src="{{ '/assets/img/projects/mid-think/overview.png' | relative_url }}" alt="Mid-Think overview and accuracy-length trade-off">
  <figcaption>Mid-Think combines reasoning-activating and reasoning-suppressing cues to reach an intermediate accuracy–length trade-off.</figcaption>
</figure>

## Token-Level Triggers

Attention analysis reveals that high-level instructions are not the whole story. A small number of opening tokens behave like switches: a leading **“Okay”** token strongly attracts attention and activates reasoning, while the newline pattern after `&lt;/think&gt;` suppresses it. Controlled prompts reproduce the same behavior across reasoning settings, suggesting that the model has learned lexical triggers from highly regular training templates.

<figure class="project-figure">
  <img src="{{ '/assets/img/projects/mid-think/trigger-attention.png' | relative_url }}" alt="Attention heat maps showing reasoning trigger tokens">
  <figcaption>Across five opening formats, generation attention concentrates on “Okay” in reasoning modes and on the newline after the closing think tag in no-think mode.</figcaption>
</figure>

Mid-Think combines both cues in one format. The suppressing pattern first closes an empty thinking block; a new reasoning block then begins with the activating cue. This small prompt-level intervention produces an intermediate reasoning budget dynamically, rather than forcing every problem into the same preselected token limit.

## Accuracy, Efficiency, and RL Training

On MATH500, Mid-Think reaches **92.1% accuracy with 2,589 average tokens**, compared with 86.3% and 899 tokens for no-think, and 94.4% and 4,904 tokens for full think. Across MATH500, AIME, and GPQA, it consistently improves the accuracy–length trade-off over fixed-token and instruction-based budget controls.

<figure class="project-figure project-figure--narrow">
  <img src="{{ '/assets/img/projects/mid-think/budget-tradeoff.png' | relative_url }}" alt="Mid-Think accuracy and length trade-off against fixed reasoning budgets">
  <figcaption>Unlike a fixed token cap, Mid-Think adapts its realized budget across examples and remains close to the accuracy–length Pareto frontier.</figcaption>
</figure>

The same mechanism also helps reinforcement-learning post-training. Applying Mid-Think after supervised fine-tuning reduces RL training time by about **15%** (54 to 46 hours for Qwen3-8B), while improving final think-mode accuracy from **69.8% to 72.4% on AIME** and from **58.5% to 61.1% on GPQA**.

<div class="project-figure-grid project-figure-grid--two">
  <figure class="project-figure">
    <img src="{{ '/assets/img/projects/mid-think/rl-entropy.png' | relative_url }}" alt="Entropy by reinforcement-learning training step">
    <figcaption>Entropy over GRPO training steps.</figcaption>
  </figure>
  <figure class="project-figure">
    <img src="{{ '/assets/img/projects/mid-think/rl-entropy-time.png' | relative_url }}" alt="Entropy by reinforcement-learning wall-clock time">
    <figcaption>Mid-Think reaches the end of training in less wall-clock time.</figcaption>
  </figure>
</div>

The result is a lightweight way to regulate reasoning at both inference and training time. The paper was published in **Findings of ACL 2026**.

## Links

- [Paper](https://aclanthology.org/2026.findings-acl.299/)
- [Code](https://github.com/uservan/Mid-Think)
