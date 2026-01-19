# PePG
## Setup

### 1. Create Environment

```bash
conda create -n pepg python=3.10
```

### 2. Install Requirements

```bash
pip install -r requirements.txt
```

---

## Experiments

### Generate Comparison Plot

**Run experiment:**
```bash
python run_experiment.py --etas 0.1 --max_iterations 100 --n_jobs 20 --nus 0.1 --warmup 1 --compare_algorithms --policy_gradient --multi_agent --num_seeds 20 --eps 0.5
```

**Plot figures:**
```bash
python plot.py
```

### Generate Entropy Ablation Plot

**Run experiment:**
```bash
python entropy_ablation.py
```

**Plot figure:**
```bash
python plot_entropy_ablation.py
```

---