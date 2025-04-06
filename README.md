# Artificial-Intelligence-Research-Assistant-with-Meta-s-Llama-4-Scout-and-Vector-Database# PDF Knowledge Extraction and QA System

This project is a full-stack pipeline to convert PDF documents into vector embeddings, store them in a vector database, and allow querying via natural language using LLaMA 4 and cosine similarity. It's fast, modular, and tailored for internal document question answering.

---

## What It Does

- Loads and processes multiple PDF files from a directory
- Splits documents into intelligently sized chunks for better embedding quality
- Generates vector embeddings using HuggingFace models
- Stores embeddings using ChromaDB
- Lets you query the system using natural language
- Uses cosine similarity to fetch the most relevant text
- Builds a context-aware prompt to ensure accurate, source-based responses
- Answers are generated using Meta's LLaMA 4 (via Groq API)

---

## Why It’s Worth Bragging About

- **Smart PDF Handling**: Uses `PyMuPDFLoader` and chunking to preserve context and ensure cleaner embedding.
- **High-Quality Embeddings**: Powered by `sentence-transformers/all-MiniLM-L6-v2`, a strong balance between speed and performance.
- **Fast Inference**: Integrated with `Groq`, so LLM responses are lightning fast.
- **Grounded QA**: Uses only the internal context; no hallucination, no fluff.
- **Built for Scaling**: Handles multiple PDFs, limits processing intelligently, and is easy to deploy or wrap in an API.

---

## How to Run

1. **Install dependencies** (see below)
2. **Set environment variables** if needed (defaults are included)
3. **Run the script** directly to extract, embed, and query.

```bash
python main.py
```

---

## Requirements

Install the dependencies using pip:

```bash
pip install langchain chromadb sentence-transformers PyMuPDF tqdm scikit-learn
```

---

## Environment Variables

| Variable              | Default               | Description                       |
|-----------------------|------------------------|-----------------------------------|
| `SOURCE_DIRECTORY`    | `External_Database`    | Path to your folder of PDFs       |
| `PERSIST_DIRECTORY`   | `db`                   | Where to save Chroma vector store |
| `EMBEDDINGS_MODEL_NAME` | `all-MiniLM-L6-v2`   | HF embedding model to use         |

---

## File Overview

- `load_pdf_documents()`: Reads and loads all PDFs
- `process_documents()`: Splits into chunks
- `generate_and_save_embeddings()`: Embeds and saves to JSON
- `retrieve_relevant_text()`: Finds most similar content to the question
- `build_strict_prompt()`: Constructs a rules-based QA prompt
- `ChatGroq`: Runs LLaMA 4 to answer based only on internal data

---

## Example Query

**Question**: What is DenseNet and give page number?

This will:
- Find the top chunks from the internal database
- Build a context-limited prompt
- Ask LLaMA 4 to answer strictly based on that context

---



---


