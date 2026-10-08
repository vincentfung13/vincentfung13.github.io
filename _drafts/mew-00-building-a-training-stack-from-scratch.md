---
layout: post
title: "mew #0: Building an LLM Training Stack from Scratch"
description: Why I'm building a 4D-parallel training stack by hand, and how each phase will be measured
tags: distributed-training
categories: mew
giscus_comments: true
related_posts: true
toc:
  sidebar: left
---

<!--
Template for every mew write-up. Keep the section order so the series reads
consistently. Move this file to _posts/YYYY-MM-DD-<slug>.md to publish, and
put figures in assets/img/posts/<slug>/.
Preview drafts locally with: bundle exec jekyll serve --drafts
-->

## The Question

What does this phase try to answer? One paragraph.

## The Cost Model

Predict before measuring: memory, communication volume, expected step time.
Inline math works, e.g. ring all-reduce moves $$2\frac{N-1}{N} \cdot B$$ bytes per rank.

## What I Built

The design, with short code excerpts from mew. Link to the commit or PR.

## Correctness

The parity test against the single-GPU reference: loss curves and gradient tolerances.

## Results

Measured numbers next to the prediction. Plots, Nsight traces, memory snapshots.

## Explaining the Gap

Where prediction and measurement differ, and why.

## What's Next

The next phase, and open questions.

## References

Papers from the roadmap's reading list for this phase.
