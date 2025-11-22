# 📘 **upskill-notebooklm-rag-local**

A fully local, privacy-friendly **NotebookLM-style RAG system** using **Ollama**, **FAISS**, and **Python**.  
No cloud. No API keys. 100% offline.

---

## 🚀 **Features**
- 100% local (no internet required)  
- PDF → Text → Chunks → Embeddings → Answers  
- OCR fallback for scanned PDFs  
- Semantic search powered by **FAISS**  
- Local LLM answering using **Ollama**  
- Beginner-friendly modular code  

---

## 📁 **Project Structure**
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
├── rag.py             # NotebookLM-style chat interface
├── utils.py           # Ollama config + chat/embedding utilities
├── requirements.txt
└── README.md
```

---

## 🧩 **Requirements**

### **Software**
- Python **3.10+**  
- Ollama → https://ollama.com/download  

### **Hardware Notes**
- **16GB RAM is enough to load a 7B model (Q4)**  
  but **CPU-only inference will be slow**.  
- For fast performance:
  - NVIDIA GPU (RTX 20/30/40 series)  
  - Apple Silicon (M1/M2/M3)  
  - Jetson Orin Nano / Orin NX  
- For CPU-only laptops, use smaller models:
  ```
  qwen2.5:3b-instruct
  phi3:mini
  tinyllama:1.1b
  ```
- **32GB+ RAM recommended** for smooth ingestion & large PDFs.

---

## ⚙️ **Installation**
```
git clone your-repo-url
cd upskill-notebooklm-rag-local
python -m venv .venv
```

### Windows
```
. .venv/Scripts/activate
```

### macOS / Linux
```
source .venv/bin/activate
```

### Install dependencies
```
pip install -r requirements.txt
```

---

## 🧠 **Install Ollama Models**

### Answering Model (LLM)
```
ollama pull mistral
```

Why?  
✔ Good RAG quality  
✔ Offline  
✔ Strong reasoning  

❗ *Note:* Slow on CPU laptops.

### Faster models:
```
ollama pull qwen2.5:3b-instruct
ollama pull phi3:mini
```

---

### Embedding Model
```
ollama pull nomic-embed-text
```

Why?  
✔ Fast  
✔ Lightweight  
✔ Excellent for semantic search  

Embedding → creates vectors  
LLM → generates answers  

Both are required.

---

## 📥 **Add Your PDFs**
Place your documents into:
```
data/pdfs/
```

---

## 🏗️ **Build FAISS Index**
*(One-time per PDF set)*

```
python rag.py --ingest
```

This will:
- Extract text  
- Perform OCR  
- Chunk the text  
- Generate embeddings  
- Build FAISS index  

Stored in:
```
data/index/
```

---

## 💬 **Start Asking Questions**
```
python rag.py
```

Example usage:
```
Q> What is this PDF about?
Q> Summarize page 3.
Q> What are the steps in this section?
Q> exit
```

---

## 🔧 **Troubleshooting**

### TimeoutError
Use a smaller model:
```
qwen2.5:3b-instruct
```
Or set:
```
timeout=None
```
in `utils.py`.

### Slow responses?
Use:
```
qwen2.5:3b-instruct
phi3:mini
```

### Need higher quality?
Use:
```
qwen2.5:7b-instruct
llama3.1:8b-instruct
```

---

## 🏁 **Conclusion**
Your fully local **NotebookLM-style RAG system** is ready.  
Add PDFs → Ingest → Chat.

Perfect for:
- Engineering manuals  
- Embedded & automotive docs  
- Research papers  
- Books & tutorials  
- Private knowledge bases  
