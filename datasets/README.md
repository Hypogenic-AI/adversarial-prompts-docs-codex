# Downloaded Datasets

This directory contains datasets for the research project. Data files are NOT
committed to git due to size. Follow the download instructions below.

## Dataset 1: ccdv/arxiv-summarization

### Overview
- **Source**: HuggingFace `ccdv/arxiv-summarization`
- **Size**: ~200K papers (arXiv)
- **Format**: HuggingFace Dataset (Parquet shards)
- **Task**: Long-document summarization / long-context processing
- **Splits**: train/validation/test
- **License**: See dataset card on HuggingFace

### Download Instructions

**Using HuggingFace (recommended):**
```python
from datasets import load_dataset
dataset = load_dataset("ccdv/arxiv-summarization")
dataset.save_to_disk("datasets/arxiv_summarization")
```

### Loading the Dataset
```python
from datasets import load_from_disk
dataset = load_from_disk("datasets/arxiv_summarization")
```

### Sample Data
See `datasets/arxiv_summarization/samples.json`.

### Notes
- Long-form scientific papers are useful for testing hidden prompt insertion at different lengths.

---

## Dataset 2: ccdv/pubmed-summarization

### Overview
- **Source**: HuggingFace `ccdv/pubmed-summarization`
- **Size**: ~133K biomedical papers
- **Format**: HuggingFace Dataset (Parquet shards)
- **Task**: Long-document summarization / long-context processing
- **Splits**: train/validation/test
- **License**: See dataset card on HuggingFace

### Download Instructions

**Using HuggingFace (recommended):**
```python
from datasets import load_dataset
dataset = load_dataset("ccdv/pubmed-summarization")
dataset.save_to_disk("datasets/pubmed_summarization")
```

### Loading the Dataset
```python
from datasets import load_from_disk
dataset = load_from_disk("datasets/pubmed_summarization")
```

### Sample Data
See `datasets/pubmed_summarization/samples.json`.

### Notes
- Biomedical papers provide long, domain-specific documents for evaluating prompt hiding robustness.
