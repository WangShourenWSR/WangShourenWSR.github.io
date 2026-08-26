---
layout: page
title: Agent Team Work Zone
description: A persistent management layer for long-lived coding-agent teams, designed to preserve working state across compaction and restarts.
importance: 1
category: open-source
related_publications: true
github: https://github.com/SR-A-W/agent-team-work-zone
---

Agent Team Work Zone (ATWZ) is a filesystem-based operations layer for long-lived coding-agent teams. It treats each agent and teammate as an employee with a persistent workstation that stores working context, decisions, handoffs, and recovery state.

The system addresses several recurring problems in long-running agentic workflows:

- team state disappearing when a terminal or process closes;
- detail loss during context compaction;
- decisions becoming trapped in old conversations; and
- repeated prompt-writing for task assignment and handoff.

ATWZ combines workstations, skills, hooks, and scripts so an agent team can back up, restore, and transfer work with less manual reconstruction.

- [Paper](https://arxiv.org/abs/2607.22917)
- [Code](https://github.com/SR-A-W/agent-team-work-zone)
