# 📘 **upskill-notebooklm-rag-local**

A fully local, privacy-friendly **NotebookLM-style RAG** system using **Ollama**, **FAISS**, and **Python**.  
No cloud. No API keys. 100% offline.

---

## 🚀 **Features**
- 100% local (offline)  
- PDF → Text → Chunks → Embeddings → Answers  
- OCR for scanned PDFs  
- Semantic search via **FAISS**  
- Local LLM responses using **Ollama**  
- Simple, modular structure  

---

## 📁 **Project Structure**
```
upskill-notebooklm-rag-local/
├── data/
│   ├── pdfs/      # Add your PDFs here
│   └── index/     # Auto-generated FAISS index
├── ingest.py      # Text extraction + OCR + chunking
├── embedding.py   # Embeddings + FAISS builder
├── search.py      # Semantic search
├── rag.py         # NotebookLM-style chat
└── utils.py       # Ollama utilities
```

---

## 🧩 **Requirements**
- Python **3.10+**  
- Ollama → https://ollama.com/download  
- **16GB RAM** minimum (7B models load but slow on CPU)  
- **Recommended for speed:**  
  - NVIDIA GPU / Apple Silicon / Jetson Orin  
- **CPU-friendly models:**  
  ```
  qwen2.5:3b-instruct
  phi3:mini
  ```

---

## ⚙️ **Installation**
```
git clone your-repo-url
cd upskill-notebooklm-rag-local
python -m venv .venv
source .venv/bin/activate   # or .venv/Scripts/activate on Windows
pip install -r requirements.txt
```

---

## 🧠 **Models to Install**
### LLM (answers)
```
ollama pull mistral
```
Or faster:
```
ollama pull qwen2.5:3b-instruct
```

### Embedding Model
```
ollama pull nomic-embed-text
```

---

## 📥 **Add PDFs**
Put files inside:
```
data/pdfs/
```

---

## 🏗️ **Build FAISS Index**
```
python rag.py --ingest
```

---

## 💬 **Start Chatting**
```
python rag.py
```

Example:
```
Q> Summarize page 3.
```

---

## 🏁 **Done**
Your offline NotebookLM-style RAG system is ready—private, fast, and ideal for technical PDFs, engineering docs, and research papers.
