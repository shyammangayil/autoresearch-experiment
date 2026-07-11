# AI Research Organization Architecture

## Control Flow
1. CEO Agent initiates the research cycle.
2. Literature Review Agent reads 'program.md' and 'train.py'.
3. Experiment Designer proposes changes to 'train.py'.
4. Code Reviewer validates the Python syntax and logic.
5. Execution: The system runs 'train.py' for 5 minutes.
6. Decision: Results (val_bpb) are logged to 'autoresearch-experiment/metrics'.

## AI-Agent Interactions
- Agents communicate via LiteLLM to optimize costs (Task 5).
- Success/Failure is tracked in the 'experiments/' directory (Task 3).