# RAG Multimodal Chatbot

A multimodal Retrieval-Augmented Generation (RAG) chatbot built for a health-documents Q&A task, developed as part of a graduate coursework lab (DATA 266 — Lab 2, Kaggle competition track).

## Overview

The system answers multi-turn conversational questions about health documents (text, figures, and tables) by:

- **Chunking** source documents into overlapping text nodes
- **Hybrid retrieval** combining dense embeddings (sentence-transformers) with sparse BM25, fused via Reciprocal Rank Fusion (RRF)
- **Figure-aware retrieval**, matching questions to referenced figures/tables using regex + fuzzy matching (RapidFuzz)
- **Sentence-level re-ranking** of retrieved context before generation
- **Answer generation** via the OpenAI API, grounded strictly in retrieved context

## Repo Structure

```
.
├── notebook.ipynb        # Main implementation (retrieval + generation pipeline)
├── submission.csv         # Generated answers for the evaluation set
├── docs/
│   └── lab_instructions.pdf   # Original assignment brief
└── .gitignore
```

## Tech Stack

- Python (Google Colab environment)
- `sentence-transformers`, `faiss-cpu`, `rank_bm25` — retrieval
- `pymupdf`, `pdfplumber` — PDF parsing
- `openai` — answer generation
- `rapidfuzz` — fuzzy text matching for figure references
- `pandas` — data handling

## Notes

- API keys are loaded at runtime (e.g. via Colab secrets) and are **not** stored in this repo.
- This was developed as a graded academic assignment; shared here primarily for personal portfolio/reference purposes.

## Status

Initial import — original development history was not tracked in git at the time; this repo starts from the final submitted version.
