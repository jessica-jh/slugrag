# SlugRAG: RAG Evaluation Framework

SlugRAG is an evaluation toolkit for Retrieval-Augmented Generation (RAG) systems. It provides a standardized pipeline to:
1) validate JSONL submissions,
2) evaluate retrieval accuracy using standard IR metrics, and
3) optionally run LLM-based judging for generated responses.

---

## 🚀 Key Features

- **Retrieval Evaluation (Task A)**: Compute **nDCG@{1,3,5}** and **Recall@{1,3,5}** using `pytrec_eval`.
- **Format Validation**: Validate JSONL structure, required fields, data types, size limits, and `task_id` alignment before submission.
- **LLM-based Judging (Optional)**: Run judging utilities (e.g., RAGAS faithfulness, RadBench judge, IDK judge) via a single wrapper.
- **Multi-Model Support (Optional)**: Supports both **Azure OpenAI** and **local HuggingFace** models for judging.

---

## 📂 Repository Structure

### Core Scripts
- **`run_retrieval_eval.py`**  
  Evaluate retrieval performance and export both per-instance and aggregate results (CSV).
- **`format_checker.py`**  
  Validate JSONL format/constraints for submissions (supports multiple modes; use `retrieval_taska` for Task A).
- **`judge_wrapper.py`** *(optional)*  
  Wrapper for LLM-based evaluation utilities (RAGAS faithfulness / RadBench / IDK).
- **`judge_utils.py`** *(optional)*  
  Shared utilities for loading JSONL, prompt templating, parsing judge outputs, etc.

### Data & Configuration
- **`SlugRAG_TaskA.jsonl`**  
  Input file for Task A (used to validate `task_id` coverage).
- **`task_a_official_submission.jsonl`**  
  Example prediction file for Task A (retrieval submission format).
- **`requirements.txt`** / **`constraints.txt`**  
  Dependency list and version constraints (e.g., PyTorch pin).
