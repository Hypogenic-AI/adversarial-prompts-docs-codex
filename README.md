# Adversarial Prompt Hiding vs. Document Length

This project evaluates whether hiding adversarial prompts becomes easier or harder as documents get longer, using long-context LLM summarization on real paper PDFs with controlled injections.

## Key Findings
- Attack success was rare and occurred only in the shortest bin (512 tokens) when the injection was placed at the start and no defense was applied.
- Longer documents (1024/2048 tokens) showed zero attack success in this setup.
- Simple sanitization removed the remaining successes without noticeably reducing summary overlap.

## How to Reproduce
1. Set up the environment:
   ```bash
   uv venv
   source .venv/bin/activate
   uv pip install -r requirements.txt
   ```
2. Run experiments (requires `OPENAI_API_KEY`):
   ```bash
   python src/run_experiments.py
   ```
3. Analyze results:
   ```bash
   python src/analyze_results.py
   ```

## File Structure
- `src/run_experiments.py`: Runs LLM experiments and saves raw outputs.
- `src/analyze_results.py`: Computes metrics, stats, and plots.
- `results/`: Metrics, plots, and raw outputs.
- `REPORT.md`: Full research report with methodology and analysis.

See `REPORT.md` for full details and limitations.
