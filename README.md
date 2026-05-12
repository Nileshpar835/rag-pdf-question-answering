# 📄 Intelligent PDF Question Answering System using RAG

An end-to-end **Retrieval-Augmented Generation (RAG)** pipeline for **semantic document search and intelligent question answering from PDFs** using **LangChain, ChromaDB, Sentence Transformers, and Groq LLM**.

This project enables users to upload multiple PDF documents, retrieve relevant contextual information using vector similarity search, and generate accurate answers using a Large Language Model (LLM).

---

## 🚀 Features

✅ Multi-PDF document ingestion  
✅ Intelligent document chunking  
✅ Semantic search using embeddings  
✅ Vector database storage with ChromaDB  
✅ Context-aware Question Answering (RAG)  
✅ Fast LLM inference using Groq API  
✅ Metadata-aware retrieval  
✅ Scalable architecture for enterprise document search

---

## 🏗️ Architecture

```text
                ┌──────────────────┐
                │   PDF Documents  │
                └────────┬─────────┘
                         │
                         ▼
                ┌──────────────────┐
                │ PDF Loader       │
                │ (PyPDFLoader)    │
                └────────┬─────────┘
                         │
                         ▼
                ┌──────────────────┐
                │ Text Chunking    │
                │ Recursive Split  │
                └────────┬─────────┘
                         │
                         ▼
                ┌──────────────────┐
                │ Embedding Model  │
                │ MiniLM-L6-v2     │
                └────────┬─────────┘
                         │
                         ▼
                ┌──────────────────┐
                │ ChromaDB         │
                │ Vector Store     │
                └────────┬─────────┘
                         │
                    User Query
                         │
                         ▼
                ┌──────────────────┐
                │ Semantic Search  │
                │ Top-K Retrieval  │
                └────────┬─────────┘
                         │
                         ▼
                ┌──────────────────┐
                │ Groq LLM         │
                │ (Qwen3-32B)      │
                └────────┬─────────┘
                         │
                         ▼
                    🎯 Final Answer
```

---

## 🧠 How It Works

### 1️⃣ Document Ingestion

The system loads PDF documents using **PyPDFLoader** and extracts document text page-by-page.

### 2️⃣ Text Chunking

Large documents are split into smaller chunks using:

- **Chunk Size:** `500`
- **Chunk Overlap:** `50`

This improves retrieval quality and preserves context.

### 3️⃣ Embedding Generation

Each text chunk is converted into vector embeddings using:

```python
all-MiniLM-L6-v2
```

from Sentence Transformers.

### 4️⃣ Vector Database Storage

Embeddings are stored inside **ChromaDB** for efficient semantic similarity search.

### 5️⃣ Semantic Retrieval

When a user asks a question:

```text
"What is Encoder-Decoder Architecture?"
```

The query is converted into embeddings and compared with stored document embeddings.

Top relevant chunks are retrieved.

### 6️⃣ Response Generation

Retrieved context is sent to the **Groq LLM** which generates a context-aware response.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|----------|
| Python | Programming Language |
| LangChain | LLM Orchestration |
| ChromaDB | Vector Database |
| Sentence Transformers | Embeddings |
| PyPDF | PDF Processing |
| RecursiveCharacterTextSplitter | Chunking |
| Groq API | LLM Inference |
| Qwen3-32B | Language Model |
| Google Colab | Development Environment |

---

## 📂 Project Structure

```text
rag-pdf-question-answering/
│
├── data/
│   ├── pdfs/
│   │   ├── research1.pdf
│   │   └── research2.pdf
│
├── vector_store/
│
├── notebooks/
│   └── rag-pdf-question-answering.ipynb
│
├── README.md
└── .gitignore
```

---

## ⚙️ Installation

### 1️⃣ Clone Repository

```bash
git clone https://github.com/your-username/rag-pdf-question-answering.git
cd rag-pdf-question-answering
```

### 2️⃣ Create Virtual Environment

```bash
python -m venv venv
```

### 3️⃣ Activate Environment

#### Windows

```bash
venv\Scripts\activate
```

### 4️⃣ Install Dependencies

```bash
pip install langchain langchain-core langchain-community langchain-text-splitters sentence-transformers chromadb pypdf pymupdf langchain-groq scikit-learn
```

---

## 🔑 Setup Groq API Key

Get your API key from:

```text
https://console.groq.com/keys
```

Then add:

```python
API_GROQ_KEY = "your_api_key_here"
```

Or using environment variables (recommended):

```python
import os

os.environ["GROQ_API_KEY"] = "your_api_key_here"
```

---

## ▶️ Usage

### Run Notebook

Open:

```text
notebooks/rag_pipeline.ipynb
```

Upload PDF documents inside:

```text
data/pdfs/
```

Ask questions like:

```python
answer = generate_output(
    "What is Transformer Architecture?",
    rag_retriever,
    llm
)

print(answer)
```

### Example Query

```text
How does Encoder-Decoder work?
```

### Example Output

```text
The encoder-decoder architecture is a sequence-to-sequence framework where the encoder processes input information and the decoder generates output using contextual representations.
```

---

## 📊 Example Pipeline

```python
query = "What is LLM?"

answer = generate_output(
    query,
    rag_retriever,
    llm
)

print(answer)
```

---

## 🔥 Key Highlights

- Built a complete **RAG architecture from scratch**
- Implemented **semantic similarity search**
- Integrated **Vector Database (ChromaDB)**
- Used **Sentence Transformers for embeddings**
- Built an **LLM-powered PDF assistant**
- Implemented **context-aware response generation**

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository  
2. Create a new branch

```bash
git checkout -b feature-name
```

3. Commit your changes

```bash
git commit -m "Added new feature"
```

4. Push to GitHub

```bash
git push origin feature-name
```

5. Create a Pull Request

---

## 👨‍💻 Author

### Nilesh Parmar

**GitHub:** https://github.com/nileshpar835  
**LinkedIn:** https://linkedin.com/in/nileshpar835

---

## ⭐ Support

If you found this project useful, consider giving it a **star ⭐ on GitHub**.

---

## 📜 License

This project is licensed under the **MIT License**.

```text
MIT License

Copyright (c) 2026 Nilesh Parmar

Permission is hereby granted, free of charge,
to any person obtaining a copy of this software
and associated documentation files...
```
