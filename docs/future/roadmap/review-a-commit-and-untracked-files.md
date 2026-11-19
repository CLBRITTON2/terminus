---
title: review a commit, and untracked files
state: researching
created: 2026-11-18
tags: [enhancement]
---

Two narrow things a review could not be pointed at, met on mega on 2026-11-18. Neither is why that day's reviews ran wide; see the correction below.

- **A change that is already committed.** A review takes the working tree's changes, named paths, or the full tree. Once a batch is committed, the only way to look at it again is by path, which reviews those files whole and not what the batch changed in them. A way to name a commit or a range would let a committed batch be reviewed as the change it was.
- **A new file that is not yet tracked,** in paths mode. On mega the implementer reported that paths mode refused `ui/src/modal.ts`, which a fix had just created. Not confirmed by the planning agent.

## correction, 2026-11-19

This card first said that a review "took in everything else in those files" because terminus could not be scoped, and that this made a correct fix impossible to show clean. That was wrong, and Michael pointed it out: terminus reviews the changes in the working tree, and does not need the whole tree.

What happened on mega was the planning agent's doing. A batch was committed before its review was clean, and the next prompt then asked for "the files of the last three batches" to be reviewed together. That is a paths review of whole files, by instruction. The practice already says what to do instead: review the working tree, which is the batch, before it is committed.

One observation from doing exactly that the next day (`6082dde05ee4`, mega, working tree). The review named the batch's own files as its starting points and returned six blocking findings, none against the lines the batch changed: all were older code in files the batch touched. So a review scoped to a change still judges what it reads in the changed files. Whether that is the intent, or whether a finding should say that it lies outside the change, is a question for terminus.

Captured by the planning agent on mega.
