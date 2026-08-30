---
layout: page
title: Path-Lock Expert
description: Architecture-level separation of think and no-think modes through deterministic control-token routing.
importance: 1
category: research
related_publications: true
github: https://github.com/SR-A-W/path-lock-expert
---

[Path-Lock Expert: Separating Reasoning Mode in Hybrid Thinking via Architecture-Level Separation](https://arxiv.org/abs/2604.27201) moves reasoning-mode control from training to model architecture.

The method replaces each decoder MLP with two mode-specific experts and uses deterministic control-token routing to lock a response onto a think or no-think path. This separation makes the selected reasoning mode more controllable by design.

The paper was accepted to COLM 2026.

## Links

- [Paper](https://arxiv.org/abs/2604.27201)
- [Code](https://github.com/SR-A-W/path-lock-expert)
