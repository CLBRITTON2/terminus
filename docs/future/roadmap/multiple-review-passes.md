---
title: multiple review passes
state: researching
created: 2026-08-25
tags: [epic, spike]
milestone: v0.1.x
---

include support for multiple review passes. this will be useful for the [[grouped-reviews]] implementation, and also for additional types of review passes.

today an agent or operator can manually invoke different configurations; this feature would allow multiple passes/configurations to all aggregate into a single "review cycle" and report.

## discussion

the selected/excluded-quality aggregation rule is settled in the [2026-08-25 journal](../../journal/2026-08-25.md): a quality counts as selected for the cycle if any pass selected it, and the cycle's excluded set is the union of the per-pass exclusions minus every quality some pass selected. a quality excluded by one pass but selected by another therefore does not appear as cycle-level excluded. this describes quality selection, not whether the cycle is clean; aggregation of findings and verdicts still needs design.

the September [territory-coverage implementation](../../current/territory-coverage.md) also reports which starting-point files project-local qualities reach. the cycle must define file-level coverage separately: the union of selected qualities cannot establish which files were covered across passes. preserve the distinction between coverage and the findings verdict, including how ad-hoc and unavailable assessments participate. [Coverage follow-ons](../territory-coverage-follow-ons.md) records this boundary.

a second seam rides in: the territory bypass means a `--quality` pass inherits the starting-points-not-a-fence model, so "spot-check this quality on these files" silently becomes "this quality on the whole tree, reached from these files." fine for forcing a question a filter would answer no to, but a multi-pass design should name it deliberately — a pass that means "check quality x on the files i changed" is a different review shape than "check quality x everywhere", and the design should decide which shape a named pass is.
