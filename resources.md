# Resources Catalog

## Summary
This document catalogs all resources gathered for the research project, including papers, datasets, and code repositories.

### Papers
Total papers downloaded: 6

| Title | Authors | Year | File | Key Info |
|-------|---------|------|------|----------|
| PISanitizer: Preventing Prompt Injection to Long-Context LLMs via Prompt Sanitization | Geng et al. | 2025 | papers/2511.10720_PISanitizer_long_context_prompt_sanitization.pdf | Long-context prompt injection defense |
| When Reject Turns into Accept: Quantifying the Vulnerability of LLM-Based Scientific Reviewers to Indirect Prompt Injection | Sahoo et al. | 2025 | papers/2512.10449_indirect_prompt_injection_scientific_reviewers.pdf | Indirect injection in scientific reviews |
| Multilingual Hidden Prompt Injection Attacks on LLM-Based Academic Reviewing | Theocharopoulos et al. | 2025 | papers/2512.23684_multilingual_hidden_prompt_injection_academic_review.pdf | Multilingual hidden prompts in papers |
| ObliInjection: Order-Oblivious Prompt Injection Attack to LLM Agents with Multi-source Data | Wang et al. | 2025 | papers/2512.09321_ObliInjection_order_oblivious_prompt_injection.pdf | Order-robust injections for multi-source contexts |
| BrowseSafe: Understanding and Preventing Prompt Injection Within AI Browser Agents | Zhang et al. | 2025 | papers/2511.20597_BrowseSafe_prompt_injection_browser_agents.pdf | HTML-based prompt injection benchmark |
| Securing Large Language Models (LLMs) from Prompt Injection Attacks | Suri, McCrae | 2025 | papers/2512.01326_securing_llms_from_prompt_injection.pdf | Defense evaluation overview |

See `papers/README.md` for detailed descriptions.

### Datasets
Total datasets documented: 2

| Name | Source | Size | Task | Location | Notes |
|------|--------|------|------|----------|-------|
| arxiv-summarization | HuggingFace | ~200K docs | Long-doc summarization | datasets/arxiv_summarization/ | Sample saved in `samples.json` |
| pubmed-summarization | HuggingFace | ~133K docs | Long-doc summarization | datasets/pubmed_summarization/ | Sample saved in `samples.json` |

See `datasets/README.md` for detailed descriptions and download instructions.

### Code Repositories
Total repositories cloned: 3

| Name | URL | Purpose | Location | Notes |
|------|-----|---------|----------|-------|
| rebuff | https://github.com/protectai/rebuff | Prompt injection detector | code/rebuff/ | Useful baseline defense |
| superagent | https://github.com/superagent-ai/superagent | App-level injection protection | code/superagent/ | Defensive patterns and tooling |
| promptfoo | https://github.com/promptfoo/promptfoo | Prompt evaluation framework | code/promptfoo/ | Can run injection test suites |

See `code/README.md` for detailed descriptions.

## Resource Gathering Notes

### Search Strategy
- Queried arXiv for prompt injection, hidden instruction, and long-context attacks.
- Selected papers with long-document settings or indirect injection attacks.
- Searched GitHub for prompt injection defenses and evaluation tooling.

### Selection Criteria
- Direct relevance to hiding instructions in long documents or indirect prompt injection.
- Recency and applicability to long-context LLMs.
- Availability of public PDFs and usable codebases.

### Challenges Encountered
- Some HuggingFace datasets use legacy loading scripts not supported by the installed `datasets` version. Switched to Parquet-based datasets (`ccdv/*`).
- Streaming sample extraction was slow; small samples were saved for documentation only.

### Gaps and Workarounds
- No public dataset specifically designed for varying document length with controlled injections; recommend synthesizing injections into long-document corpora.

## Recommendations for Experiment Design

1. **Primary dataset(s)**: `ccdv/arxiv-summarization` and `ccdv/pubmed-summarization` for long documents.
2. **Baseline methods**: No-defense LLM, simple sanitization, and a classifier-based injection detector (e.g., Rebuff).
3. **Evaluation metrics**: Attack success rate, task accuracy on original objective, and defense false-positive rate.
4. **Code to adapt/reuse**: `code/rebuff/` for detection baselines and `code/promptfoo/` for evaluation harnesses.
