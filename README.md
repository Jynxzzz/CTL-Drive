# CTL-Drive

**[Ranked #15](https://waymo.com/open/challenges/e2e-driving/results/b34f2412-5a6e/1772305880072000/) on the [Waymo Open Dataset E2E Driving Challenge](https://waymo.com/open/challenges/e2e-driving/)** — trained on a single RTX 4090.

VLM-based E2E driving: Qwen3-VL-4B with QLoRA, CoVLA pre-training + WOD-E2E fine-tuning + proto intent conditioning, front camera only, text-encoded trajectories.

## Results

| Metric | CTL-Drive (#15) | #1 (NTR) | Gap |
|--------|-----------|--------------|-----|
| **ADE @ 3s** | **1.28m** | 1.17m | 0.11m |
| **ADE @ 5s** | **2.99m** | 2.63m | 0.36m |
| **RFS** | **7.70** | 8.05 | 0.35 |
| Training GPU | Single RTX 4090 | Multi-GPU cluster | — |

## Method

- **Base model:** Qwen3-VL-4B with QLoRA (r=128, alpha=256)
- **Teacher annotation:** 780K frames (401K WOD-E2E + 379K CoVLA) using Qwen3.5-397B on 20× H100 GPUs (~19h wall-clock)
- **Stage 1a:** CoVLA pre-training (379K frames, SFT)
- **Stage 1b:** WOD-E2E fine-tuning (401K samples, front-camera only, turn-balanced)
- **Features:** Intent conditioning, turn-aware fallback, text-encoded trajectories

## Acknowledgments

- Builds on [Poutine](https://arxiv.org/abs/2506.11234) (Rowe et al., 2025) from Mila / Université de Montréal
- Teacher annotation on the **Nibi cluster** via the **Digital Research Alliance of Canada**
- Training infrastructure provided by **Google TPU Research Cloud (TRC)**
- Supervised by Prof. Ciprian Alecsandru, Concordia University

## Links

- **Project Page:** [obsicat.com/poutine-e2e.html](https://obsicat.com/poutine-e2e.html)
- **Leaderboard:** [Waymo E2E Driving Challenge](https://waymo.com/open/challenges/e2e-driving/results/b34f2412-5a6e/1772305880072000/)
- **Author:** [Xingnan Zhou](https://obsicat.com) — PhD Candidate, Concordia University, Montreal

---

*Code release coming soon.*
