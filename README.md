# CTL-Drive

**Ranked #15 on the [Waymo Open Dataset E2E Driving Challenge](https://waymo.com/open/challenges/e2e-driving/results/b34f2412-5a6e/1772305880072000/)**

VLM-based end-to-end autonomous driving using text-encoded trajectories.

## Method

- **Base model:** Qwen3-VL-4B with QLoRA fine-tuning
- **Training data:** 795K frames (WOD-E2E + CoVLA-style annotation)
- **Input:** Front camera only, text-encoded trajectory output
- **Features:** CoVLA pre-training, WOD-E2E fine-tuning, intent conditioning, turn-aware fallback
- **Current stage:** Stage 1 (VLT pre-training) — GRPO reinforcement learning coming next

## Results

| Metric | Value |
|--------|-------|
| Waymo E2E Challenge Rank | **#15** |
| Submission | Stage 1 only (no RL) |
| Training GPU | Single RTX 4090 (24 GB) |
| Annotation Compute | Google TPU v4/v5e/v6e via TRC |

> This ranking was achieved with only supervised pre-training on a single consumer GPU. Stage 1b fine-tuning and GRPO reinforcement learning on TPU pods are in progress.

## Acknowledgments

- Based on [Poutine](https://arxiv.org/abs/2506.11234) (Rowe et al., 2025) from Mila / Université de Montréal
- Compute resources provided by **Google TPU Research Cloud (TRC)**
- Supervised by Prof. Ciprian Alecsandru, Concordia University

## Links

- **Project Page:** [obsicat.com/poutine-e2e.html](https://obsicat.com/poutine-e2e.html)
- **Leaderboard:** [Waymo E2E Driving Challenge](https://waymo.com/open/challenges/e2e-driving/results/b34f2412-5a6e/1772305880072000/)
- **Author:** [Xingnan Zhou](https://obsicat.com) — PhD Candidate, Concordia University, Montreal

---

*Code release coming soon.*
