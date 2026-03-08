# 🤖 RAG Pipeline — Personal Document Parsing AI Chatbot

![Python](https://img.shields.io/badge/Python-3.x-blue)
![LangChain](https://img.shields.io/badge/LangChain-Framework-green)
![FAISS](https://img.shields.io/badge/FAISS-Vector%20Search-orange)
![ChromaDB](https://img.shields.io/badge/ChromaDB-Vector%20Store-purple)
![GenAI](https://img.shields.io/badge/GenAI-RAG%20Pipeline-red)

---

## 📌 Project Overview

This project implements a **Retrieval-Augmented Generation (RAG) pipeline** that enables natural language querying over personal documents. Instead of relying solely on a language model's pre-trained knowledge, this system retrieves contextually relevant chunks from user-uploaded documents and uses them to generate grounded, accurate responses.

**The core problem this solves:** Large Language Models hallucinate when answering questions about documents they haven't seen. RAG fixes this by giving the model real, retrieved context before it answers.

---

## 🗂️ Pipeline Architecture

```
User Query (Natural Language)
        ↓
Document Ingestion — PDF Parsing & Text Extraction
        ↓
Text Chunking — Split into semantically meaningful segments
        ↓
Embedding Generation — Convert chunks to dense vector representations
        ↓
FAISS Vector Index — Store & index embeddings for similarity search
        ↓
ChromaDB — Persistent vector storage layer
        ↓
Semantic Retrieval — Top-K most relevant chunks retrieved
        ↓
LangChain Prompt Engineering — Context + Query assembled into prompt
        ↓
LLM Response — Grounded answer generated from retrieved context
```

---

## 🛠️ Tech Stack

| Component | Tool | Purpose |
|---|---|---|
| **Framework** | LangChain | Pipeline orchestration, prompt management |
| **Vector Search** | FAISS | Fast approximate nearest-neighbour similarity search |
| **Vector Store** | ChromaDB | Persistent embedding storage & semantic retrieval |
| **Embeddings** | Sentence Transformers | Dense vector generation from text chunks |
| **Document Parsing** | PyPDF / LangChain Loaders | PDF ingestion & text extraction |
| **Language** | Python 3.x | Core implementation |

---

## 📁 Repository Structure

```
rag-pipeline/
│
├── source/                      # Source documents for ingestion
│
├── vector_db/
│   └── faiss_index/             # Persisted FAISS vector index
│
├── load_data.py                 # Document loading & PDF parsing
├── split_data.py                # Text chunking & segmentation logic
├── create_embeddings.py         # Embedding generation pipeline
├── create_vector_db.py          # FAISS index creation & persistence
├── get_vector_db.py             # Vector store retrieval interface
├── main.py                      # End-to-end pipeline entry point
├── .gitignore
└── README.md
```

---

## ⚙️ How It Works — Module Breakdown

### `load_data.py` — Document Ingestion
Loads PDF and text documents from the `source/` directory using LangChain document loaders. Handles multi-page PDFs and extracts raw text content for downstream processing.

### `split_data.py` — Text Chunking
Splits raw documents into overlapping chunks using LangChain's `RecursiveCharacterTextSplitter`. Chunk overlap ensures that context is not lost at segment boundaries — critical for accurate retrieval.

### `create_embeddings.py` — Embedding Generation
Converts text chunks into dense vector representations using a sentence embedding model. Each chunk is mapped to a high-dimensional vector that captures its semantic meaning.

### `create_vector_db.py` — FAISS Index Creation
Builds and persists a FAISS vector index from the generated embeddings. FAISS enables sub-second approximate nearest-neighbour search across thousands of document chunks.

### `get_vector_db.py` — Retrieval Interface
Loads the persisted FAISS index and ChromaDB store. Given a user query, retrieves the Top-K most semantically similar document chunks via cosine similarity search.

### `main.py` — Pipeline Entry Point
Orchestrates the full end-to-end flow: document loading → chunking → embedding → indexing → retrieval → prompt construction → LLM response generation.

---

## 🔑 Key Concepts Demonstrated

- **RAG Architecture** — Grounding LLM responses in retrieved document context to reduce hallucination
- **Vector Embeddings** — Representing text semantically as dense numerical vectors
- **Semantic Search** — Retrieval based on meaning, not keyword matching
- **Prompt Engineering** — Structuring the context + query prompt for optimal LLM output
- **Persistent Vector Storage** — FAISS index and ChromaDB enabling stateful retrieval across sessions
- **Document Chunking Strategy** — Overlapping chunks to preserve cross-boundary context

---

## 🚀 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/ShreyaVJadhav3/rag-pipeline.git
cd rag-pipeline
```

### 2. Install dependencies
```bash
pip install langchain faiss-cpu chromadb sentence-transformers pypdf
```

### 3. Add your documents
Place your PDF or text files inside the `source/` directory.

### 4. Build the vector index
```bash
python create_embeddings.py
python create_vector_db.py
```

### 5. Run the chatbot
```bash
python main.py
```

Enter your natural language query when prompted. The pipeline retrieves relevant chunks from your documents and generates a grounded response.

---

## 💡 Example Use Cases

- **Resume Q&A** — Upload your resume and ask *"What are my top technical skills?"*
- **Research Paper Summarisation** — Upload a paper and ask *"What methodology was used?"*
- **Personal Notes Search** — Query across multiple notes files semantically
- **Policy Document Analysis** — Ask specific questions about lengthy policy documents

---

## 📈 What This Project Demonstrates

This project goes beyond basic chatbot implementation by building a **production-style GenAI pipeline** with:

- Modular, file-separated architecture (not a single monolithic script)
- Persistent vector storage that survives session restarts
- Two-layer retrieval strategy (FAISS for speed + ChromaDB for persistence)
- Proper document chunking with overlap to preserve semantic context
- Prompt engineering layer for controlled LLM output

---

## 👩‍💻 Author

**Shreya Jadhav**  
Data Analyst | Python · SQL · Power BI · LangChain · GenAI  
📧 shreyajune03pune@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/jadhavshreya03pune) | [GitHub](https://github.com/ShreyaVJadhav3)

---

## 📌 Related Projects

- 🛡️ [Project Sentinel — E-Commerce Fraud Detection](https://github.com/ShreyaVJadhav3/project---sentinel---ecommerce---fraud---detection-) — End-to-end fraud pipeline detecting 586 ghost orders across 99K transactions
- 🎬 [Movie Recommender System](https://github.com/ShreyaVJadhav3/movie_recommender_system) — Content-based filtering using TF-IDF & Cosine Similarity
- 📊 [Power BI Sales Dashboard](https://github.com/ShreyaVJadhav3/PowerBI_projects) — Regional sales performance with DAX time-intelligence
