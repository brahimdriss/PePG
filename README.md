# Performative Policy Gradient (PePG)

Official implementation of **"Performative Policy Gradient: Optimality in Performative Reinforcement Learning"** (ICML 2026).

## Overview

This repository provides the first policy gradient algorithm that provably converges to *performatively optimal* policies in Performative Markov Decision Processes (PeMDPs). The codebase extends the ICML'23 [Performative Reinforcement Learning](https://github.com/StratisMarkou/icml2023-performative-rl-paper-code) implementation of Mandal et al., reusing its environment and experimental setup to compare PePG against the stability-seeking baselines from that work.

**Key Features:**
- First policy gradient algorithm with convergence guarantees to performatively optimal policies
- Performative Policy Gradient Theorem for arbitrary differentiable policy/environment parametrisations
- Unregularised and entropy-regularised variants
- Empirical comparison against stability-seeking baselines (MDRR, RPO-FS)

## Installation

```bash
# Create conda environment
conda create -n pepg python=3.10
conda activate pepg

# Clone the repository
git clone https://github.com/brahimdriss/PePG.git
cd PePG

# Install required packages
pip install -r requirements.txt
```

## Repository Structure

```
.
├── src/
│   ├── agents/                 # Gridworld agent implementation
│   ├── envs/                   # Performative environments (gridworld)
│   ├── policies/               # Policy parametrisations (softmax, tabular, ε-greedy, ...)
│   ├── experiments/            # Ablation study drivers
│   ├── plotting/               # Plot helpers
│   ├── performative_pepg.py    # PePG algorithm
│   ├── reg_pepg.py             # Entropy-regularised PePG
│   ├── mixed_delayed_rr.py     # MDRR baseline
│   ├── performative_prediction.py
│   └── generate_data.py        # Experiment dispatcher
├── run_experiment.py           # Main comparison entry point
├── entropy_ablation.py         # Entropy-regularisation ablation
├── lr_ablation.py              # Learning-rate ablation
├── plot.py                     # Comparison plots
├── plot_entropy_ablation.py    # Ablation plots
└── plot_lr_ablation.py
```

## Quick Start

### Comparison: PePG vs. baselines

```bash
python run_experiment.py \
    --etas 0.1 \
    --max_iterations 100 \
    --n_jobs 20 \
    --nus 0.1 \
    --warmup 1 \
    --compare_algorithms \
    --policy_gradient \
    --multi_agent \
    --use_pepg \
    --num_seeds 20 \
    --eps 0.5
```

Then generate the figures:

```bash
python plot.py
```

### Entropy-regularisation ablation

```bash
python entropy_ablation.py
python plot_entropy_ablation.py
```

### Learning-rate ablation

```bash
python lr_ablation.py
python plot_lr_ablation.py
```

## Experiments

Experiments are run on a performative gridworld with `num_followers` agents whose dynamics shift in response to the deployed policy, controlled by a performative strength parameter `eps`. The main comparison evaluates average performative utility of PePG against repeated retraining (RPO-FS) and mixed delayed repeated retraining (MDRR) under both single-agent and multi-agent settings. Raw results are written to `data/` and figures to `figures/`.

## Citation

```bibtex
@inproceedings{basu2026performative,
  title={Performative Policy Gradient: Optimality in Performative Reinforcement Learning},
  author={Basu, Debabrota and Das, Udvas and Driss, Brahim and Mukherjee, Uddalak},
  booktitle={Proceedings of the 43rd International Conference on Machine Learning},
  year={2026}
}
```

## Paper

- **Authors**: Debabrota Basu, Udvas Das, Brahim Driss, Uddalak Mukherjee

## Contact

For questions or issues, please open an issue on GitHub or contact the authors.
