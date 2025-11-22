📘 upskill-notebooklm-rag-local

A fully local, privacy-friendly NotebookLM-style RAG system using Ollama, FAISS, and Python.

🚀 Features

100% local (no internet required)

PDF → Text → Chunks → Embeddings → Answers

OCR fallback for scanned PDFs

Semantic search using FAISS

Local LLM answering using Ollama

Beginner-friendly workflow

📁 Project Structure
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

🧩 Requirements
Software

Python 3.10+

Ollama installed → https://ollama.com/download

Hardware Notes

16GB RAM is enough to load a 7B model (Q4 quantized)
but CPU-only inference will be slow (0.5–2 tokens/sec).

For fast performance, use:

NVIDIA GPU (RTX 20/30/40 series)

Apple Silicon (M1/M2/M3)

Jetson Orin Nano / Orin NX

For CPU-only laptops, use smaller models:

qwen2.5:3b-instruct
phi3:mini
tinyllama:1.1b


32GB+ RAM recommended for handling large PDFs smoothly.

⚙️ Installation
git clone your-repo-url
cd upskill-notebooklm-rag-local
python -m venv .venv

# Windows
. .venv/Scripts/activate  

# macOS / Linux
source .venv/bin/activate

pip install -r requirements.txt

🧠 Install Ollama Models
Answering Model (LLM)
ollama pull mistral


Why?
✔ Good quality
✔ Strong for RAG
✔ Works offline

❗ Note: Mistral 7B is slow on CPU-only laptops.

Faster alternatives:

ollama pull qwen2.5:3b-instruct
ollama pull phi3:mini

Embedding Model
ollama pull nomic-embed-text


Why?
✔ Fast
✔ Lightweight
✔ Excellent for semantic PDF search

Embedding model → creates text vectors
LLM → generates final answers

Both are required.

📥 Add Your PDFs

Place your documents into:

data/pdfs/


Supports text PDFs, scanned PDFs (OCR), and large manuals.

🏗️ Build FAISS Index (One-time per new PDF set)
python rag.py --ingest


This process:

Extracts text

Runs OCR if needed

Splits text into chunks

Generates embeddings

Builds FAISS vector index

Index files are stored in:

data/index/

💬 Start Asking Questions
python rag.py


Example queries:

Q> What is this PDF about?
Q> Summarize page 3.
Q> What are the steps of this project?
Q> exit

🔧 Troubleshooting
❗ TimeoutError

Use a smaller LLM:

ollama pull qwen2.5:3b-instruct


Or set:

timeout=None


inside utils.py.

❗ Slow Answers

Use:

qwen2.5:3b-instruct
phi3:mini

❗ Need Better Quality?

Use:

qwen2.5:7b-instruct
llama3.1:8b-instruct

🏁 Conclusion

Your fully local NotebookLM-style RAG system is ready.
Just add PDFs → ingest → chat.

Ideal for:

Engineering manuals

Embedded & automotive documents

Research papers

Books & tutorials

Private knowledge bases
