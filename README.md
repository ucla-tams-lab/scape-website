# SCAPE: Scenario-Conditioned Simulation-Augmented Policy Evaluation

**CoRL 2026** · Official project website

**Dijie Zhu · Seunghun Oh · Ruopeng Huang · Zhiyu Huang · Jiaqi Ma · Chen Tang**  
UCLA · Seoul National University · USC · NC State

[![Paper](https://img.shields.io/badge/arXiv-Paper-b31b1b.svg)](https://arxiv.org/abs/2608.19425)
[![Project Page](https://img.shields.io/badge/Project-Page-2575fc.svg)](https://ucla-tams-lab.github.io/scape-website/)
[![Code](https://img.shields.io/badge/GitHub-Code-181717.svg)](https://github.com/ucla-tams-lab/scape)

[![SCAPE combines limited paired real–simulation data with abundant simulation to predict performance across scenarios.](static/images/teaser.png)](https://ucla-tams-lab.github.io/scape-website/)

## TL;DR

**Predict how a policy will perform in each scenario using limited real-world tests and abundant, imperfect simulation.**

Real-world testing is costly, simulation is biased, and average performance can hide failures in individual scenarios. SCAPE combines the two evaluation sources to predict scenario-conditioned real-world policy performance with calibrated uncertainty.

1. **Correct simulation outcomes.** Learn a scenario-dependent correction from paired real and simulated evaluations.
2. **Train a scenario-level evaluator.** Combine real labels with corrected simulation labels. The final evaluator needs only the scenario context as input.
3. **Calibrate uncertainty.** Use held-out target evaluations for split conformal calibration, with marginal coverage under exchangeability.

## Key results

SCAPE is evaluated on autonomous driving with three nuPlan planners and quadruped velocity tracking, including deployment on a physical Unitree Go2.

| Domain | Lower prediction loss vs. neural baselines | Lower prediction loss vs. aggregate baselines |
| --- | ---: | ---: |
| Driving (nuPlan, Sim2Sim) | **4.9%** | **34.7%** |
| Quadruped tracking (Sim2Sim) | **14.5%** | **27.7%** |

These are average relative loss reductions over the evaluated settings, rather than improvements in the underlying policies themselves.

- **Physical Go2:** 11.3% lower velocity and 8.7% lower yaw-rate prediction error than the strongest baseline.
- **New-city evaluation:** adding simulation-only data from the held-out city reduces SCAPE's loss by a further 4.8%, without target labels from that city during training.

See the [project page](https://ucla-tams-lab.github.io/scape-website/) for the method overview, figures, and full results, and the [paper](https://arxiv.org/abs/2608.19425) for experimental details.

## Repository guide

| Repository | Contents |
| --- | --- |
| **`scape-website` (here)** | Project website, paper figures, and citation information. |
| [**`scape`**](https://github.com/ucla-tams-lab/scape) | Evaluator training, baselines, and evaluation code. Start here to reproduce the evaluation experiments. |
| [**`scape-locomotion`**](https://github.com/ucla-tams-lab/scape-locomotion) | Go2 locomotion data-generation pipeline. |

## Website development

This is a static website served by GitHub Pages from the root of the `main` branch.

- [`index.html`](index.html): page content, paper links, and BibTeX.
- [`static/images/`](static/images/): teaser, method, and result figures.
- [`static/css/style.css`](static/css/style.css): page styling.

Preview locally:

```bash
git clone https://github.com/ucla-tams-lab/scape-website.git
cd scape-website
python3 -m http.server 8000
```

Open [http://localhost:8000](http://localhost:8000) in your browser.

## Citation

```bibtex
@inproceedings{zhu2026scape,
  title     = {{SCAPE}: Scenario-Conditioned Simulation-Augmented Policy Evaluation},
  author    = {Zhu, Dijie and Oh, Seunghun and Huang, Ruopeng and Huang, Zhiyu and Ma, Jiaqi and Tang, Chen},
  booktitle = {Conference on Robot Learning (CoRL)},
  year      = {2026}
}
```

## Acknowledgments

Website layout inspired by [Nerfies](https://nerfies.github.io).
