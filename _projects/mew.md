---
layout: page
title: mew
description: An LLM training stack written from scratch, from tokenizer to 4D parallelism and GRPO
img: assets/img/projects/mew-logo.jpg
importance: 1
category: Open Source
github: https://github.com/vincentfung13/mew
---

<div class="row justify-content-center">
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/projects/mew-logo.jpg" title="mew" class="img-fluid rounded z-depth-1" %}
  </div>
</div>

[**mew**](https://github.com/vincentfung13/mew) is a GPT-style language model and training stack that I am building from scratch, one component at a time. The goal is a stack that covers **4D-parallel pretraining** (DP × TP × PP × CP, plus expert parallelism for MoE) and **post-training** (SFT and GRPO), where every piece is understood well enough to predict how it should perform before measuring it.

## Principles

- **Predict, then measure.** Each component starts with a cost model (memory, communication volume, expected step time). The gap between prediction and measurement, and its explanation, is the deliverable.
- **Correctness before speed.** Every feature lands with a parity test against a single-GPU reference run.
- **Compare against the industrial version.** Each stage is benchmarked side by side with the PyTorch built-in or [TorchTitan](https://github.com/pytorch/torchtitan) on the same hardware.
- **Publish as I go.** Each phase ends with a write-up on the [blog](/blog/).

## What's in mew Today

- **Tokenization:** a byte-pair encoding (BPE) tokenizer, trained and applied with multiprocessing.
- **Model:** Transformer blocks with RoPE and grouped-query attention, written on top of basic PyTorch ops.
- **Kernels:** a Triton FlashAttention (forward and backward) with bf16 AMP, checked against the eager reference.
- **Training:** a custom AdamW and LR schedule, memmap data loaders, Hydra configs and W&B tracking.
- **Distributed** (on the `feature/data_parallel` branch): a `DistributedDataParallel` wrapper with async per-parameter all-reduce and `no_sync()` for gradient accumulation.
- **Performance tooling:** FLOPs-per-token accounting, MFU and tokens/s logging, CUDA memory snapshots, NVTX/Nsight Systems profiling, and an interactive memory report.

## Roadmap

| Phase | Focus                                         | Status      | Write-up                               |
| ----- | --------------------------------------------- | ----------- | -------------------------------------- |
| 0     | Harness: launch, reference runs, comm logging | in progress | Building a Training Stack from Scratch |
| 1     | Fast DDP: bucketing, comm/compute overlap     | planned     | Why Naive DDP Is Slow                  |
| 2     | ZeRO and FSDP                                 | planned     | A Whiteboard Memory Model              |
| 3     | Tensor and sequence parallelism               | planned     | Why TP Stays Inside NVLink             |
| 4     | Pipeline parallelism                          | planned     | Choosing a 3D Layout                   |
| 5     | Context parallelism (ring attention)          | planned     | Long-Context Training                  |
| 6     | MoE and expert parallelism                    | planned     | Where MoE Training Time Goes           |
| 7     | Checkpointing, fault tolerance, capstone      | planned     | Capstone vs TorchTitan                 |
| 8     | SFT                                           | planned     | What Packing Buys You                  |
| 9     | GRPO                                          | planned     | Where RL Time Goes                     |

The full plan, including the compute budget and reading list, lives in [`docs/ROADMAP.md`](https://github.com/vincentfung13/mew/blob/feature/data_parallel/docs/ROADMAP.md).
