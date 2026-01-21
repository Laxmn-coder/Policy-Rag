# Policy RAG Chatbot

A **local, privacy-preserving Policy RAG (Retrieval-Augmented Generation) system** built using **FastAPI**, **ChromaDB**, **Sentence Transformers**, and **Ollama**.
This system allows organizations to upload internal policy documents (PDFs) and ask questions that are answered **strictly from the uploaded documents**.

---

## 🚀 Features

* 📄 Upload and ingest PDF policy documents
* 🧠 Semantic search using embeddings (Sentence Transformers)
* 📦 Vector storage with ChromaDB
* 🤖 Local LLM inference using Ollama (no data leaves your system)
* ⚡ FastAPI backend with interactive Swagger UI
* 🐳 Docker & Docker Compose ready
* 🔐 Secure by design (no secrets or vector data committed)

---

## 🏗️ Project Structure

```
policy-rag/
│── backend/
│   ├── app/
│   │   ├── __init__.py
│   │   ├── api.py          # FastAPI routes
│   │   ├── rag.py          # Retrieval + generation logic
│   │   ├── ingest.py       # PDF ingestion & embedding
│   │   ├── llm_client.py   # Ollama client
│   │   └── config.py       # App configuration
│   ├── Dockerfile
│
│── frontend/
│   ├── app.py             # UI (Streamlit / client)
│   ├── Dockerfile
│   └── __init__.py
│
│── data/                  # Ignored (vector DB, generated data)
│── docker-compose.yml
│── requirements.txt
│── .gitignore
│── .env.example
│── README.md
```

---

## ⚙️ Requirements

* Python **3.10+**
* Ollama installed locally
* Git

---

## 🧪 Local Setup (Without Docker)

### 1️⃣ Clone the repository

```bash
git clone https://github.com/Laxmn-coder/Policy-Rag.git
cd Policy-Rag
```

### 2️⃣ Create & activate virtual environment

```bash
python -m venv env
env\Scripts\activate   # Windows
```

### 3️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

### 4️⃣ Start Ollama

```bash
ollama serve
```

Pull a model (once):

```bash
ollama pull llama3
```

### 5️⃣ Run the backend

```bash
cd backend
python -m uvicorn app.api:app --reload
```

Backend will be available at:

```
http://127.0.0.1:8000
```

Swagger UI:

```
http://127.0.0.1:8000/docs
```

---

## 🧠 API Endpoints

### 📄 Ingest PDF

```http
POST /ingest
```

Uploads a PDF and stores embeddings for a given `company_id`.

### 💬 Chat with Policies

```http
POST /chat
```

Example request:

```json
{
  "company_id": "384804",
  "question": "What is machine learning?"
}
```

Response:

```json
{
  "answer": "Machine learning is ..."
}
```

---

## 🐳 Docker Setup

```bash
docker-compose up --build
```

This will start:

* FastAPI backend
* Frontend
* Ollama integration

---

## 🔐 Security & Best Practices

* `.env` files are ignored
* Vector DB (`data/`) is not committed
* Fully offline & privacy-preserving
* No hallucinations: answers are grounded in uploaded documents

---

## 📌 Use Cases

* Internal company policy chatbot
* HR / Legal document Q&A
* Compliance & audit assistance
* Enterprise knowledge bases

---

## 📈 Future Improvements

* Authentication & role-based access
* Multi-document ranking
* Streaming responses
* CI/CD pipeline
* Cloud deployment support

---

## 👨‍💻 Author

**Laxman Rathod**
B.Tech Mechanical Engineering | Aspiring Data Scientist
Hackathon Team Lead (SIH, MCP)

---

## ⭐ If you like this project

Give it a ⭐ on GitHub —
