# Literature Review

## Research Area Overview
This topic sits at the intersection of prompt injection security, long-context LLM behavior, and hidden-instruction attacks. The key question is whether longer documents make it easier to conceal adversarial instructions or whether added context dilutes their influence. Recent work focuses on prompt injection in agentic settings, long-context defenses, and empirical evaluations using realistic documents (papers, web pages) to quantify attack success rates.

## Key Papers

### Paper 1: PISanitizer: Preventing Prompt Injection to Long-Context LLMs via Prompt Sanitization
- **Authors**: Runpeng Geng, Yanting Wang, Chenlong Yin, Minhao Cheng, Ying Chen, Jinyuan Jia
- **Year**: 2025
- **Source**: arXiv
- **Key Contribution**: Proposes a defense tailored to long-context prompt injection where malicious instructions are a small fraction of the context.
- **Methodology**: Prompt sanitization for long documents; evaluates injection success in long-context settings.
- **Datasets Used**: Not specified in the abstract; likely long-document contexts or synthesized long prompts.
- **Results**: Reports improved defense effectiveness for long-context injections compared to short-context defenses.
- **Code Available**: Not specified in the abstract.
- **Relevance to Our Research**: Directly addresses long-context prompt injection and whether defenses can identify small injected spans within long documents.

### Paper 2: When Reject Turns into Accept: Quantifying the Vulnerability of LLM-Based Scientific Reviewers to Indirect Prompt Injection
- **Authors**: Devanshu Sahoo, Manish Prasad, Vasudev Majhi, Jahnvi Singh, Vinay Chamola, Yash Sinha, et al.
- **Year**: 2025
- **Source**: arXiv
- **Key Contribution**: Measures how indirect prompt injections embedded in scientific papers influence LLM-based review decisions.
- **Methodology**: Insert hidden instructions into scientific papers; evaluate acceptance recommendation shifts under attack.
- **Datasets Used**: Scientific paper documents (full-length reviewer inputs).
- **Results**: Quantifies changes in acceptance/rejection behavior when hidden prompts are present.
- **Code Available**: Not specified in the abstract.
- **Relevance to Our Research**: Tests long-document prompt hiding in a realistic setting (paper reviews), directly aligned with the hypothesis.

### Paper 3: Multilingual Hidden Prompt Injection Attacks on LLM-Based Academic Reviewing
- **Authors**: Panagiotis Theocharopoulos, Ajinkya Kulkarni, Mathew Magimai.-Doss
- **Year**: 2025
- **Source**: arXiv
- **Key Contribution**: Demonstrates hidden prompt injections embedded in academic papers, including multilingual instructions.
- **Methodology**: Inject semantically equivalent prompts in multiple languages into full-length papers; evaluate reviewer outcomes.
- **Datasets Used**: ~500 ICML papers (per abstract).
- **Results**: Shows prompt hiding can survive long document noise, including multilingual obfuscation.
- **Code Available**: Not specified in the abstract.
- **Relevance to Our Research**: Provides empirical evidence of hidden prompt effectiveness in long documents and explores multilingual concealment.

### Paper 4: ObliInjection: Order-Oblivious Prompt Injection Attack to LLM Agents with Multi-source Data
- **Authors**: Reachal Wang, Yuqi Jia, Neil Zhenqiang Gong
- **Year**: 2025
- **Source**: arXiv
- **Key Contribution**: Introduces prompt injection attacks robust to unknown ordering of multi-source inputs.
- **Methodology**: Designs order-oblivious injection strategies for multi-segment contexts.
- **Datasets Used**: Multi-source agent inputs; specific datasets not in abstract.
- **Results**: Demonstrates high attack success even when attacker does not control input order.
- **Code Available**: Not specified in the abstract.
- **Relevance to Our Research**: Long documents often combine multiple sources; order-robust injections inform how hiding may scale with length.

### Paper 5: BrowseSafe: Understanding and Preventing Prompt Injection Within AI Browser Agents
- **Authors**: Kaiyuan Zhang, Mark Tenenholtz, Kyle Polley, Jerry Ma, Denis Yarats, Ninghui Li
- **Year**: 2025
- **Source**: arXiv
- **Key Contribution**: Builds a benchmark of prompt injection attacks embedded in realistic HTML pages and evaluates defenses.
- **Methodology**: Curated HTML-based attack benchmark and defense evaluations.
- **Datasets Used**: Realistic web pages with injected instructions.
- **Results**: Reports attack impact and mitigation effectiveness in browser agents.
- **Code Available**: Not specified in the abstract.
- **Relevance to Our Research**: Web pages are long, noisy documents; benchmark informs how injection success changes with context length and structure.

### Paper 6: Securing Large Language Models (LLMs) from Prompt Injection Attacks
- **Authors**: Omar Farooq Khan Suri, John McCrae
- **Year**: 2025
- **Source**: arXiv
- **Key Contribution**: Evaluates robustness of LLMs to prompt injection and discusses defense approaches (e.g., task-specific fine-tuning such as JATMO).
- **Methodology**: Compare defenses and robustness across LLM setups.
- **Datasets Used**: Not specified in the abstract.
- **Results**: Highlights tradeoffs between instruction-following and robustness.
- **Code Available**: Not specified in the abstract.
- **Relevance to Our Research**: Provides baseline defenses for experiments on long-document prompt hiding.

## Common Methodologies
- Prompt injection via hidden instructions embedded in long documents (papers, web pages).
- Evaluation on LLM-as-judge or agentic tasks, focusing on decision shifts or task redirection.
- Comparing baseline defenses versus long-context-specific sanitization or filtering.

## Standard Baselines
- Instruction-following LLMs with no defense (attack success rate baseline).
- Simple input filtering or prompt sanitization applied to the full context.
- Task-specific fine-tuning or restricted function models (e.g., JATMO-style defenses).

## Evaluation Metrics
- **Attack Success Rate (ASR)**: Rate at which the injected instruction overrides the intended task.
- **Task Performance**: Accuracy or quality on the original task (e.g., review decision consistency).
- **Defense Utility**: Tradeoff between blocking attacks and preserving task performance.

## Datasets in the Literature
- Long-form scientific papers and academic review corpora (used for hidden prompt injection).
- Realistic web pages with embedded instructions (browser agent benchmarks).

## Gaps and Opportunities
- Limited controlled studies that vary document length systematically while keeping injection content fixed.
- Few benchmarks quantify how injection efficacy scales with length and position (beginning vs middle vs end).
- Sparse public datasets designed specifically for long-context prompt hiding experiments.

## Recommendations for Our Experiment
- **Recommended datasets**: `ccdv/arxiv-summarization`, `ccdv/pubmed-summarization` for long documents.
- **Recommended baselines**: No-defense LLM, simple sanitization, and a classifier-based injection detector (e.g., Rebuff).
- **Recommended metrics**: Attack success rate, task performance degradation, and false-positive rate for defenses.
- **Methodological considerations**: Control injection length, position, and language; stratify document length bins to test the hypothesis.
