# 🧮 Agentic Math-Aware RAG — arXiv Paper QA

> Question-answering for research papers that retrieves the math a paper implies but never defines.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sourds42/maths-paper-rag/blob/main/math_rag_complete_interview.ipynb)

## What it does

A user asking *"how does this model reduce dimensionality?"* may not know the answer involves SVD.
This system detects implicit math concepts, pulls formal definitions from a curated knowledge base,
and returns a structured **Formula → Intuition → Application** answer grounded in the source paper.

## Stack

| Component | Choice |
|-----------|--------|
| LLM | TinyLlama-1.1B (default) / Mistral-7B-Instruct (4-bit NF4) |
| Embeddings | BAAI/bge-small-en-v1.5 |
| Reranker | cross-encoder/ms-marco-MiniLM-L-6-v2 |
| Vector index | FAISS IndexFlatIP |
| Sparse retrieval | BM25 (rank_bm25) |
| Fusion | Reciprocal Rank Fusion (k=60) |
| Agent pattern | ReAct — 6 tools, 2 quality gates |
| Evaluation | Recall@K, MRR, Faithfulness, ROUGE-L |

## Quick start

1. Click the **Open in Colab** badge above
2. Runtime → Change runtime type → **T4 GPU**
3. Add your HuggingFace token as a Colab Secret named `HF_TOKEN` *(only needed for Mistral-7B)*
4. Run all cells `Ctrl+F9` — takes ~10 min on first run
5. Step 16 launches a Gradio chat UI

## Pipeline
