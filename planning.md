## Research Question
Is adversarial prompt hiding more or less effective as document length increases, when the injected instruction is held constant?

## Background and Motivation
Prompt injection attacks are increasingly embedded in long, realistic documents (papers, web pages, reports). Prior work shows hidden instructions can influence LLM outputs, but there is limited controlled evidence on how document length itself affects attack success. Understanding this relationship informs both attacker capabilities and defense design for long-context systems.

## Hypothesis Decomposition
- H1: For a fixed injection payload, attack success rate (ASR) changes systematically with document length.
- H1a: Longer documents increase ASR by providing more concealment opportunities.
- H1b: Longer documents decrease ASR by adding noise that dilutes the injection.
- H2: Injection position (early vs. middle vs. late) interacts with length.
- H3: Simple sanitization or detection has different false-positive/false-negative tradeoffs across length bins.

## Proposed Methodology

### Approach
Create controlled long-document contexts from existing summarization corpora, embed a fixed adversarial instruction, and measure model compliance with the injected instruction while performing the primary task. Vary document length by truncation/concatenation to form length bins, and evaluate ASR and task performance across conditions using real LLM APIs.

### Experimental Steps
1. **Resource review and dataset selection**: Use arXiv and PubMed long-doc datasets from `datasets/` for realistic long contexts.
2. **Document length stratification**: Define length bins (short/medium/long/very long) based on token counts; sample equal numbers per bin.
3. **Injection construction**: Embed a fixed instruction (e.g., override summary with a targeted phrase or JSON key) at controlled positions (start/middle/end).
4. **Prompting protocol**: Provide a system prompt requiring faithful summarization; measure whether the output follows the injected instruction.
5. **Baseline and defenses**: Compare no-defense baseline vs. a simple sanitization heuristic (e.g., strip suspicious markers) and optional classifier-based detector if feasible.
6. **Run experiments**: Execute multi-run API calls per condition with fixed temperature and seed; cache outputs.
7. **Scoring**: Compute ASR and task quality proxy (e.g., summary length, overlap with reference abstract via ROUGE-L if available).
8. **Statistical analysis**: Test differences in ASR across length bins and positions.

### Baselines
- **No-defense baseline**: Raw document + injection.
- **Simple sanitization**: Remove or neutralize common instruction patterns before model call.
- **(Optional) Detector-assisted**: Use Rebuff or a lightweight heuristic classifier to flag and remove injections.

### Evaluation Metrics
- **Attack Success Rate (ASR)**: Percent of outputs that comply with injected instruction.
- **Task Performance**: ROUGE-L or semantic similarity to gold abstract (if available) or summary length/coverage proxy.
- **Defense Utility**: Change in ASR vs. change in task performance.

### Statistical Analysis Plan
- Use chi-square tests or logistic regression for ASR across length bins.
- Use ANOVA or Kruskal-Wallis for task performance metrics across bins.
- Report 95% confidence intervals; apply Benjamini-Hochberg correction for multiple comparisons.
- Significance level: α = 0.05.

## Expected Outcomes
- Support H1a if ASR increases with length; support H1b if ASR decreases with length.
- Expect position effects: early injections may dominate shorter contexts; late injections may be stronger in long contexts.

## Timeline and Milestones
- Phase 1 (Planning): 30 min
- Phase 2 (Setup/Data checks): 30 min
- Phase 3 (Implementation): 60–90 min
- Phase 4 (Experiments): 60–90 min
- Phase 5 (Analysis): 45 min
- Phase 6 (Documentation): 30–45 min

## Potential Challenges
- API cost/time; mitigate with small samples per bin.
- Dataset format variability; use provided samples and schema checks.
- Ambiguous ASR detection; use strict string-matching and manual spot checks.
- Rate limits; implement retries and caching.

## Success Criteria
- Completed experiments across at least 3 length bins and 2 injection positions.
- Reported ASR and task performance with statistical tests.
- Clear conclusion with limitations and reproducibility details.
