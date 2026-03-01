# SlugRAG: Evaluation Code and Results

This repository contains the code and evaluation artifacts used to **evaluate SlugRAG**, our **multi-turn Retrieval-Augmented Generation (RAG)** system, after the system was built.

It includes:
1) utilities to **validate JSONL files** used in our evaluation pipeline,
2) scripts to **compute retrieval metrics** (e.g., nDCG/Recall) from **SlugRAG model outputs**, and
3) optional scripts to run the **LLM-based judging components** used in our evaluation of generated responses.

> Note: This repository focuses on the **evaluation pipeline and evaluation outputs/results**, not on training or rebuilding the SlugRAG model itself.

---

## 🚀 Key Features

- **Retrieval Evaluation (Task A)**: Compute **nDCG@{1,3,5}** and **Recall@{1,3,5}** using `pytrec_eval`.
- **Format Validation**: Validate JSONL structure, required fields, data types, size limits, and `task_id` alignment before submission/evaluation.
- **LLM-based Judging (Optional)**: Run judging utilities (e.g., RAGAS faithfulness, RadBench judge, IDK judge) via a single wrapper.
- **Multi-Model Support (Optional)**: Supports both **Azure OpenAI** and **local HuggingFace** models for judging.

---

## 📂 Repository Structure

### Core Scripts
- **`run_retrieval_eval.py`**  
  Evaluate retrieval performance and export both per-instance and aggregate results (CSV).
- **`format_checker.py`**  
  Validates JSONL files used in the evaluation pipeline (supports multiple modes; use `retrieval_taska` for Task A).
- **`judge_wrapper.py`** *(optional)*  
  Wrapper for LLM-based evaluations (RAGAS faithfulness / RadBench / IDK).
- **`judge_utils.py`** *(optional)*  
  Utility functions for data processing, prompt templating, and parsing judge outputs.

### Evaluation Artifacts (.jsonl)
- **`SlugRAG_TaskA.jsonl`**  
  **Task A input file** (queries/tasks). Used to validate `task_id` coverage and alignment.
- **`task_a_official_submission.jsonl`**  
  **Task A prediction file produced by our SlugRAG model** (retrieval outputs).  
  For each `task_id`, it contains the top retrieved `contexts` (with `document_id` and `score`) used in evaluation.
- **`*_scored.jsonl`** *(generated)*  
  Post-processed prediction files with per-instance retrieval scores added (e.g., `retriever_scores`).

### Dependencies
- **`requirements.txt`** / **`constraints.txt`**  
  Dependency list and version constraints (e.g., PyTorch pin).

---
