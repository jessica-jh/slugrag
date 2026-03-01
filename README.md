# SlugRAG: RAG Evaluation Framework

SlugRAG is a comprehensive evaluation toolkit designed for Retrieval-Augmented Generation (RAG) systems. It provides a standardized pipeline to evaluate retrieval accuracy, validate submission formats, and conduct LLM-based assessment of generated responses.

## 🚀 Key Features

- **Retrieval Evaluation**: Calculate standard IR metrics such as NDCG@K and Recall@K.
- **LLM-based Judging**: Assess faithfulness and relevancy of responses using the RAGAS framework and custom "I Don't Know (IDK)" detection logic.
- **Format Validation**: Ensure that your prediction files meet the structural and size requirements before official submission.
- **Multi-Model Support**: Supports both Azure OpenAI and local HuggingFace models for evaluation.

## 📂 Repository Structure

### Core Scripts
- **`run_retrieval_eval.py`**: The main script for evaluating retrieval performance. It outputs aggregate scores across different collections.
- **`judge_wrapper.py`**: A wrapper for running LLM-based evaluations (e.g., Faithfulness, Answer Relevancy) using Ragas and local LLM clients.
- **`format_checker.py`**: Validates the JSONL structure, required fields, and file size constraints for Task A (Retrieval), Task B (Generation), and Task C (RAG).
- **`judge_utils.py`**: Utility functions for data processing, conversation extraction, and prompt templating.

### Data & Configuration
- **`SlugRAG_TaskA.jsonl`**: The primary dataset for the Retrieval task.
- **`requirements.txt`**: List of Python dependencies including LangChain, Ragas, and Transformers.
- **`constraints.txt`**: Specific version constraints for core libraries like PyTorch.

## 🛠 Setup & Installation

**1. Clone the repository**
```bash
git clone [https://github.com/jessica-jh/slugrag.git](https://github.com/jessica-jh/slugrag.git)
cd slugrag
