---
layout: page
title: Controllable and Efficient Reasoning in LLMs
description: Understanding and controlling think, no-think, and intermediate-budget reasoning modes through post-training, prompting, and architecture.
importance: 1
category: research
related_publications: true
github: https://github.com/SR-A-W/demystifying-hybrid-thinking
---

This research direction studies how language models control reasoning behavior across think, no-think, and intermediate-budget settings. The work spans empirical diagnosis, post-training, training-free token-level control, and architecture-level mode separation.

## Demystifying Hybrid Thinking

[Demystifying Hybrid Thinking: Can LLMs Truly Switch Between Think and No-Think?](https://arxiv.org/abs/2510.12680) shows that current hybrid-thinking models only partially separate their modes: reasoning behavior can leak into no-think outputs. We identify key training factors and develop a practical recipe that makes no-think behavior shorter and more controllable while preserving performance. The paper was accepted to the EMNLP 2026 Main Conference.

## Mid-Think

[Mid-Think: Training-Free Intermediate-Budget Reasoning via Token-Level Triggers](https://aclanthology.org/2026.findings-acl.299/) studies the token-level cues that induce or suppress reasoning. It introduces a training-free format for intermediate-budget reasoning and was published in Findings of ACL 2026.

## Path-Lock Expert

[Path-Lock Expert](https://arxiv.org/abs/2604.27201) moves the problem from training to architecture. It replaces each decoder MLP with two mode-specific experts and uses deterministic control-token routing to lock a response onto a think or no-think path. The paper was accepted to COLM 2026.

Together, these projects form a continuous line of work: diagnosing why hybrid thinking fails, improving post-training controllability, and separating reasoning modes by design.

## Links

- [Demystifying Hybrid Thinking code](https://github.com/SR-A-W/demystifying-hybrid-thinking)
- [Mid-Think paper](https://aclanthology.org/2026.findings-acl.299/)
- [Path-Lock Expert code](https://github.com/SR-A-W/path-lock-expert)
