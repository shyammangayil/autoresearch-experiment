# Autoresearch Experiment

An organized experimental fork of [Andrej Karpathy's autoresearch](https://github.com/karpathy/autoresearch) for autonomous LLM optimization on a single GPU.

## Overview

This repository provides a structured workspace to run **autoresearch** loops — where an AI agent autonomously edits `train.py`, runs short training experiments (fixed time budget), evaluates the validation metric (`val_bpb`), and keeps only improvements via a git-based ratchet.

The setup follows Karpathy's core philosophy while adding organization for repeatable experiments, logging, and analysis.

## Project Structure
.
├── autoresearch/              # Core autoresearch framework (or symlink)
├── core_src/                  # Original or base source files
├── experiments/               # Logs of individual iterations (JSON)
├── metrics/                   # Metric tracking and analysis
├── notes/                     # Research notes and observations
├── sample_data/               # Sample datasets or subsets
├── architecture.md            # System architecture and data flow
├── program.md                 # (To be created) Agent instructions and research goal
└── train.py / prepare.py      # Main editable training script + fixed prep



## What Was Created

- **Structured workspace** with dedicated folders for experiments, metrics, and notes to keep runs organized.
- **architecture.md** — Documents the core data flow and agent interaction loop.
- Initial experiment logs (`experiments/iter_*.json`) from early runs.
- This README for clear documentation.

## How It Works

1. **Fixed components** (`prepare.py`): Data preparation, tokenizer, dataloader, and evaluation utilities (agent does **not** modify these).
2. **Agent playground** (`train.py`): Contains the GPT model, optimizer, and training loop. The AI agent can freely edit architecture, hyperparameters, attention mechanisms, etc.
3. **Research directive** (`program.md`): Plain English instructions telling the agent what to optimize and how to explore.
4. **The Loop** (Autoresearch):
   - Agent reads `program.md`
   - Proposes edits to `train.py`
   - Runs training for a fixed short duration (e.g., 5 minutes wall-clock)
   - Evaluates `val_bpb` (or chosen metric)
   - Commits improvement or reverts via git
   - Repeats autonomously (typically ~12 experiments per hour)

You write the strategy once in `program.md`, point your coding agent (Claude, etc.) at the repo, and let it run overnight.

## Getting Started

1. Clone the repo and set up the environment (follow original autoresearch instructions: `uv sync`, run `prepare.py`).
2. Create/edit `program.md` with your research goal.
3. Launch the autoresearch loop.
4. Monitor `experiments/` and `notes/` for results.

## Goals of This Experiment

- Discover better small-model architectures and training recipes via autonomous iteration.
- Build a reproducible process for LLM optimization research.
- Log and analyze what the agent tries (successes + failures) to learn from the process.

## Next Steps

- Run an overnight session with a focused `program.md`
- Analyze accumulated improvements
- Test transfer of small-model gains to larger models

---

**Inspired by Karpathy's autoresearch (March 2026)**

Happy researching! Feel free to open issues or expand the `notes/` folder with observations.

