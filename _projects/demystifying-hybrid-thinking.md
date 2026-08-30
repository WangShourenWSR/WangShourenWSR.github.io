---
layout: page
title: Demystifying Hybrid Thinking
description: An empirical study of whether hybrid-thinking language models truly separate think and no-think behavior.
img: assets/img/projects/demystifying-hybrid-thinking/motivation.png
importance: 2
category: research
related_publications: false
github: https://github.com/SR-A-W/demystifying-hybrid-thinking
---

## Can a Model Really Stop Thinking?

Hybrid-thinking models expose think and no-think controls so users can trade reasoning depth for speed. [Demystifying Hybrid Thinking: Can LLMs Truly Switch Between Think and No-Think?](https://arxiv.org/abs/2510.12680) begins by testing whether those controls create genuinely distinct behaviors. The answer is only partially: no-think responses are shorter than think responses, but they often remain much longer and more reflective than those of a direct-answer instruction model.

<figure class="project-figure">
  <img src="{{ '/assets/img/projects/demystifying-hybrid-thinking/motivation.png' | relative_url }}" alt="A think and no-think comparison showing reasoning leakage">
  <figcaption>A no-think response still generates reasoning-supportive language such as “Wait,” showing that the switch does not fully control the model's behavior.</figcaption>
</figure>

## What Controls the Switch?

We systematically vary the data and training design to identify four factors that most strongly affect mode separation:

1. **Data scale:** sufficiently large hybrid-thinking datasets are needed for stable control.
2. **Unpaired supervision:** using think and no-think answers from different questions yields cleaner separation than pairing both answers with the same question.
3. **Mode balance:** moderately increasing the share of no-think data shortens direct responses without sacrificing accuracy.
4. **Training order:** a two-phase schedule—first learning strong reasoning, then learning hybrid control—outperforms mixing both objectives from the beginning.

<div class="project-figure-grid">
  <figure class="project-figure">
    <img src="{{ '/assets/img/projects/demystifying-hybrid-thinking/mov_accuracy.png' | relative_url }}" alt="No-think accuracy comparison across benchmarks">
    <figcaption>No-think accuracy remains competitive.</figcaption>
  </figure>
  <figure class="project-figure">
    <img src="{{ '/assets/img/projects/demystifying-hybrid-thinking/mov_length.png' | relative_url }}" alt="No-think output length comparison across benchmarks">
    <figcaption>Hybrid no-think outputs remain substantially longer than direct answers.</figcaption>
  </figure>
  <figure class="project-figure">
    <img src="{{ '/assets/img/projects/demystifying-hybrid-thinking/mov_wait.png' | relative_url }}" alt="Reflective-token count comparison across benchmarks">
    <figcaption>Reflective tokens expose residual reasoning leakage.</figcaption>
  </figure>
</div>

## A Practical Recipe

Combining these findings gives a simple recipe for more controllable hybrid thinking: use larger, unpaired data; keep a moderate no-think proportion; and apply hybrid training only after establishing the model's reasoning ability. On MATH500, this reduces average no-think output length from **1,085 to 585 tokens** and reasoning-supportive token occurrences from **5,917 to 522**, while maintaining accuracy in both modes.

The work turns a vague behavior—“the model does not really stop thinking”—into a measurable training problem and a set of actionable design choices. It also motivates the later Path-Lock Expert project, which tackles the remaining interference at the architecture level. The paper was accepted to the **EMNLP 2026 Main Conference**.

## Links

- [Paper](https://arxiv.org/abs/2510.12680)
- [Code](https://github.com/SR-A-W/demystifying-hybrid-thinking)
