---
layout: about
title: About
permalink: /
subtitle: Staff Applied Scientist at <a href='https://www.tiktok.com/'>TikTok</a> · Business Integrity

profile:
  align: right
  image: profile.jpeg
  image_circular: false # crops the image to make it circular

selected_papers: true # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: true # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: false # set to true once the first post is published
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---

## About Me

I am a Staff Applied Scientist at [TikTok](https://www.tiktok.com/) Business Integrity. We build LLMs and MLLMs through both pre-training and post-training, that power the moderation of TikTok's monetization ecosystem, keeping the platform safe for users and the business sustainable.

Before this role, I was a Staff Research Engineer at [Gaussian Robotics](https://www.gaussianrobotics.com/), where I built the machine learning stack for low-compute robots: multi-task learning on edge devices, INT8 quantization and hardware-in-the-loop testing. Earlier I was a Senior Research Scientist at TikTok AI Lab, working on novel view synthesis and visual search, and before that I worked on large-scale visual search at ViSenze and led pedestrian recognition and tracking at Tuputech.

I received a bachelor's degree in Computing Science from [the University of Glasgow](https://gla.ac.uk) in 2016.

These days I care most about how large models are trained: making pre-training and post-training fast, correct and explainable at scale. In my spare time I am building [**mew**](/projects/mew/), an LLM training stack written from scratch, and [blogging](/blog/) what I learn along the way.

## Featured Projects

<div class="card mt-3 mb-3">
  <div class="row no-gutters">
    <div class="col-sm-3 p-3">
      <a href="/projects/mew/"><img src="/assets/img/projects/mew-logo.jpg" class="img-fluid rounded" alt="mew logo"></a>
    </div>
    <div class="col-sm-9">
      <div class="card-body">
        <h5 class="card-title mb-1"><a href="/projects/mew/">mew</a></h5>
        <p class="card-text mb-2">An LLM training stack written from scratch: BPE tokenizer, Transformer, Triton FlashAttention and data-parallel training today, growing toward 4D parallelism (DP × TP × PP × CP), MoE with expert parallelism, SFT and GRPO. Every component ships with a cost model, a parity test and a benchmark against TorchTitan.</p>
        <p class="card-text"><a href="https://github.com/vincentfung13/mew"><i class="fa-brands fa-github"></i> code</a> · <a href="/projects/mew/">roadmap</a> · <a href="/blog/">blog series</a></p>
      </div>
    </div>
  </div>
</div>

<style>
  /* Title-case the theme's homepage section headings (News, Latest Posts, Selected Publications). */
  article > h2 { text-transform: capitalize; }
</style>
