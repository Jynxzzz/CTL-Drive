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

## Competitive Landscape

| Method | RFS | ADE 3s | Base Model | Params | RL |
|--------|-----|--------|------------|--------|----|
| NTR (#1) | 8.05 | 1.17m | DINO | 888M | — |
| Poutine (#3) | 7.99 | 1.21m | Qwen2.5-VL-3B | 3B | GRPO |
| qwer (#5) | 7.88 | 1.86m | **Qwen3-VL-4B** | 4B | — |
| FROST-Drive (#6) | 7.86 | 2.54m | InternVL3-78B | 105M learnable | — |
| **CTL-Drive (#15)** | **7.70** | **1.28m** | **Qwen3-VL-4B** | **4B** | **None** |

- **4B vs 78B**: CTL-Drive (4B params) is within 0.15 RFS of FROST-Drive (78B InternVL3)
- **Same base model**: *qwer* uses identical Qwen3-VL-4B and ranks #5 — the 0.17 RFS gap is the clearest target for GRPO RL
- **Top 3 all use RL** — we don't (yet)

## Method

- **Base model:** Qwen3-VL-4B with QLoRA (r=128, alpha=256)
- **Stage 1a:** CoVLA pre-training (228K frames, SFT)
- **Stage 1b:** WOD-E2E fine-tuning (90K samples, front-camera only, turn-balanced)
- **Features:** Intent conditioning, turn-aware fallback, text-encoded trajectories

## Acknowledgments

- Builds on [Poutine](https://arxiv.org/abs/2506.11234) (Rowe et al., 2025) from Mila / Université de Montréal
- Compute resources provided by **Google TPU Research Cloud (TRC)**
- Supervised by Prof. Ciprian Alecsandru, Concordia University

## Links

- **Project Page:** [obsicat.com/poutine-e2e.html](https://obsicat.com/poutine-e2e.html)
- **Leaderboard:** [Waymo E2E Driving Challenge](https://waymo.com/open/challenges/e2e-driving/results/b34f2412-5a6e/1772305880072000/)
- **Author:** [Xingnan Zhou](https://obsicat.com) — PhD Candidate, Concordia University, Montreal

---

*Code release coming soon.*
