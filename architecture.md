
# Autoresearch Architecture

## Data Flow
- **prepare.py**: Fixed utilities, tokenization, and data loading.
- **train.py**: The agent-modifiable core containing the GPT model and training loop.
- **program.md**: The human-provided instructions and context for the AI agents.

## Agent Interaction
1. Agent reads `program.md` to understand the current objective.
2. Agent modifies `train.py` (hyperparameters, architecture, etc.).
3. System runs `train.py` for 5 minutes.
4. System compares `val_bpb` results and logs to the memory repository.
