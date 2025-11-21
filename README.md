
# 📘 upskill-notebooklm-rag-local

A fully local, privacy-friendly **NotebookLM-style RAG system** using **Ollama**, FAISS, and Python.

## 🚀 Features
- 100% local (no internet required)
- PDF → Text → Chunks → Embeddings → Answers
- OCR fallback for scanned PDFs
- Semantic search using FAISS
- Local LLM answering using Ollama
- Beginner-friendly workflow

## 📁 Project Structure
```
upskill-notebooklm-rag-local/
│
├── data/
│   ├── pdfs/          # Put your PDFs here
│   └── index/         # Auto-generated embeddings + FAISS index
│
├── ingest.py          # Extract text, OCR, chunking
├── embedding.py       # Embedding + FAISS index builder
├── search.py          # Retriever (semantic search)
├── rag.py             # Main NotebookLM-style chat
├── utils.py           # Ollama config + chat/embedding utilities
├── requirements.txt
└── README.md
```

## 🧩 Requirements
- Python 3.10+
- Ollama installed → https://ollama.com/download  
- 16GB RAM minimum  
- 32–48GB RAM recommended (for faster models)

## ⚙️ Installation
```
git clone your-repo-url
cd upskill-notebooklm-rag-local
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

## 🧠 Install Ollama Models

### Answering Model (LLM)
```
ollama pull mistral
```
Why?  
✔ Lightweight  
✔ Good quality  
✔ Fast on CPU  
✔ Perfect for local RAG

### Embedding Model
```
ollama pull nomic-embed-text
```
Why?  
✔ Fast  
✔ Small  
✔ Works perfectly for PDF search

Embedding model → Converts text into vectors  
LLM → Generates human-like answers  
Both are required.

## 📥 Add Your PDFs
Place your files into:
```
data/pdfs/
```

## 🏗️ Build FAISS Index (One‑time per new PDF set)
```
python rag.py --ingest
```

This:
- Extracts text  
- Runs OCR if needed  
- Creates chunks  
- Embeds via Ollama  
- Builds FAISS vector index  

## 💬 Start Asking Questions
```
python rag.py
```

Example queries:
```
Q> What is this PDF about?
Q> Summarize page 3.
Q> What are the steps of this project?
Q> exit
```

## 🔧 Troubleshooting

### ❗ TimeoutError
Use smaller LLM:
```
ollama pull qwen2.5:3b-instruct
```
Or set timeout=None in utils.py.

### ❗ Slow Answers
Use:
```
qwen2.5:3b-instruct  (fastest)
```

### ❗ Better Quality
Use:
```
qwen2.5:7b-instruct
llama3.1:8b-instruct
```

## 🏁 Conclusion
Your local NotebookLM-style RAG system is ready.  
Just add PDFs → Ingest → Chat.
