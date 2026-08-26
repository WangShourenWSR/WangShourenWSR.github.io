---
layout: page
title: MemTrace
description: A benchmark for tracing how long-term memory systems handle individual knowledge points across time, question types, and evidence conditions.
importance: 2
category: open-source
related_publications: true
github: https://github.com/SR-A-W/MemTraceBench
---

MemTrace evaluates long-term memory systems at the level of individual knowledge points rather than isolated question rows. Each fact is probed across controlled changes in memory age, question type, and evidence condition.

This view reveals failures hidden by pooled accuracy: recovering current and earlier states does not necessarily imply tracking how a fact changed, and safe abstention does not necessarily imply correcting a false premise.

- [Paper](https://arxiv.org/abs/2606.17328)
- [Benchmark repository](https://github.com/SR-A-W/MemTraceBench)
