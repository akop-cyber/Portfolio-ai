# 🤖 Portfolio-AI — The Backend Brain of My Portfolio

> A RAG-powered AI that knows everything I've built — and can talk about it.

**Live Site → [aaravkumarranjan.netlify.app](https://aaravkumarranjan.netlify.app)**

---

## What Is This?

This is the backend powering the AI chat feature on my personal portfolio. Instead of a static "About Me" page, visitors can actually *talk* to my portfolio — asking about my projects, my stack, how I learn, or anything else.

Under the hood, it's a **Retrieval-Augmented Generation (RAG)** system built from scratch. The knowledge base is a PDF of my portfolio content. When someone asks a question, the system retrieves the most relevant chunks from that PDF and passes them to an LLM to generate a grounded, accurate answer.

This backend is built on the same architecture as Documind, adapted specifically to power the AI chat feature on my personal portfolio.



---

## Architecture

```
portfolio.pdf  →  loader  →  chunker  →  embedder  →  vector store
                                                            ↓
User Question  →  embed query  →  cosine similarity  →  top chunks
                                                            ↓
                                                    LLM → Answer
```

| Module | Role |
|---|---|
| `loader.py` | Extracts text from `portfolio.pdf` |
| `chunker.py` | Splits text into overlapping chunks |
| `embedder.py` | Generates semantic embeddings via `sentence-transformers` |
| `vector.py` | In-memory vector store for chunk embeddings |
| `retriever.py` | Cosine similarity search — returns top-k relevant chunks |
| `app.py` | FastAPI server that ties everything together |

---

## Why Build This Instead of Using a Library?

Because I wanted to understand what's actually happening. LangChain and LlamaIndex are great tools, but they abstract away the parts I care most about — how chunking affects retrieval quality, how similarity thresholds prevent hallucination, how the pipeline actually flows end to end.

This project is both a portfolio feature and a learning exercise.

---

## Tech Stack

**Backend:** Python, FastAPI, Sentence Transformers, scikit-learn, NumPy, PyPDF2  
**Deployment:** Render  
**Connected Frontend:** [aaravkumarranjan.netlify.app](https://aaravkumarranjan.netlify.app)

---

## Local Setup

```bash
git clone https://github.com/akop-cyber/Portfolio-ai.git
cd Portfolio-ai
pip install -r requirements.txt
uvicorn app:app --reload
```

Replace `portfolio.pdf` with your own PDF knowledge base to adapt this for your own portfolio.

---

## Author

**Aarav Kumar Ranjan** 

[Portfolio](https://aaravkumarranjan.netlify.app) · [GitHub](https://github.com/akop-cyber) · [Kaggle](https://kaggle.com/aaravkumarranjan)
