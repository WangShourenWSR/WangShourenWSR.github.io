---
layout: page
title: Path-Lock Expert
description: Architecture-level separation of think and no-think modes through deterministic control-token routing.
img: assets/img/projects/path-lock-expert/architecture.png
importance: 1
category: research
related_publications: false
github: https://github.com/SR-A-W/path-lock-expert
---

## The Problem

Hybrid-thinking language models promise two useful behaviors in one model: a deliberate **think** mode for difficult problems and a fast **no-think** mode for direct answers. In practice, however, the boundary is porous. Even when no-think is requested, a model may generate long answers and reflective phrases such as “wait” or “hmm.” We call this failure **reasoning leakage**. It increases latency and token use, and makes the supposedly direct mode unpredictable.

<figure class="project-figure">
  <img src="{{ '/assets/img/projects/path-lock-expert/reasoning-leakage.png' | relative_url }}" alt="An example of reasoning leakage in think and no-think responses">
  <figcaption>A motivating AIME24 example: the no-think response still performs visible self-reflection outside the empty thinking block.</figcaption>
</figure>

## Architecture-Level Mode Separation

[Path-Lock Expert: Separating Reasoning Mode in Hybrid Thinking via Architecture-Level Separation](https://arxiv.org/abs/2604.27201) asks whether this is not only a training problem, but also an architectural interference problem. A dense decoder asks the same feed-forward parameters to support two competing generation behaviors. Path-Lock Expert (PLE) therefore replaces the MLP in each decoder layer with two semantically locked experts: one for think and one for no-think.

A deterministic router reads the control token once and locks the entire sequence to one expert path across every layer and decoding step. Attention, embeddings, normalization, and the language-model head stay shared. Only one expert is active at inference time, avoiding a learned router, load-balancing losses, or a more complicated reinforcement-learning pipeline.

<figure class="project-figure">
  <img src="{{ '/assets/img/projects/path-lock-expert/architecture.png' | relative_url }}" alt="Path-Lock Expert architecture with shared attention and separate think and no-think MLP experts">
  <figcaption>PLE keeps the representational backbone shared while separating the feed-forward pathways most directly associated with generation behavior.</figcaption>
</figure>

## Results and Takeaway

Across mathematical and scientific reasoning benchmarks, PLE produces a more useful no-think mode while preserving strong think-mode performance. On Qwen3-4B and AIME24, it generates **17× fewer reflective tokens**, cuts average no-think output length from **8,665 to 4,101 tokens**, and improves no-think accuracy from **35.33% to 44.67%**, while maintaining think accuracy (61.33% vs. 60.00%).

<figure class="project-figure">
  <img src="{{ '/assets/img/projects/path-lock-expert/aime24-results.png' | relative_url }}" alt="Path-Lock Expert AIME24 accuracy, output length, and reasoning leakage results">
  <figcaption>AIME24 results comparing PLE with dense and training-only baselines across accuracy, output length, and reflective-token leakage.</figcaption>
</figure>

The central conclusion is that controllable hybrid thinking is partly an architectural problem. Training recipes can reduce leakage, but separating mode-specific feed-forward pathways provides a direct, complementary way to make the selected mode reliable by design. The paper was accepted to **COLM 2026**.

## Links

- [Paper](https://arxiv.org/abs/2604.27201)
- [Code](https://github.com/SR-A-W/path-lock-expert)
