Enterprise GenAI RAG Assistant

Enterprise GenAI RAG Assistant is a production-style Retrieval-Augmented Generation (RAG) application that allows users to upload PDF documents and ask context-aware questions. The system retrieves the most relevant document chunks using semantic search and generates grounded answers using Large Language Models.

This project demonstrates modern GenAI engineering skills including:

Retrieval-Augmented Generation (RAG)
Embeddings
Vector Databases
Semantic Search
LLM Orchestration
FastAPI Backend Development
Streamlit Frontend Development
Prompt Engineering
Hallucination Reduction
🚀 Features
PDF document upload
Automatic PDF parsing
Intelligent text chunking
OpenAI embeddings generation
Semantic vector search using FAISS
Context-aware question answering
Source citation support
Hallucination reduction
FastAPI REST APIs
Streamlit user interface
Docker containerization
Enterprise-ready architecture
🧠 Tech Stack
Backend
Python
FastAPI
LangChain
OpenAI API
Frontend
Streamlit
Vector Database
FAISS
Document Processing
PyPDF
Deployment
Docker
Docker Compose
# 🏗️ Architecture Diagram

![Architecture Diagram](./screenshots/architecture-diagram.png)
<img width="1529" height="860" alt="image" src="https://github.com/user-attachments/assets/43e6a7be-441b-4f4b-bd15-1b87b5bf8648" />

---

# 🔥 RAG Workflow

![RAG Workflow](./screenshots/rag-workflow.png)

---

# 🧩 Application Screens

![Application Screens](./screenshots/application-screens.png)

🔄 System Workflow
User uploads PDF
        ↓
FastAPI receives file
        ↓
PDF text extraction
        ↓
Document chunking
        ↓
Embedding generation
        ↓
FAISS vector storage
        ↓
User asks question
        ↓
Semantic retrieval
        ↓
LLM generates grounded answer
        ↓
Source citations returned

📁 Project Structure
enterprise-genai-rag-assistant/
│
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── config.py
│   │   ├── schemas.py
│   │   ├── routers/
│   │   │   ├── documents.py
│   │   │   └── chat.py
│   │   └── services/
│   │       ├── pdf_service.py
│   │       └── rag_service.py
│   │
│   ├── uploads/
│   ├── vectorstore/
│   ├── requirements.txt
│   ├── Dockerfile
│   └── .env.example
│
├── frontend/
│   ├── app.py
│   └── requirements.txt
│
├── screenshots/
│
├── docker-compose.yml
│
└── README.md
⚙️ Environment Variables

Create file:

backend/.env

Add:

OPENAI_API_KEY=your_openai_api_key_here
VECTORSTORE_PATH=vectorstore/faiss_index
UPLOAD_DIR=uploads
MODEL_NAME=gpt-4o-mini
EMBEDDING_MODEL=text-embedding-3-small
▶️ Run Backend
cd backend

python -m venv venv
Windows
venv\Scripts\activate
Install dependencies
pip install -r requirements.txt
Run FastAPI
uvicorn app.main:app --reload

Open Swagger Docs:

http://localhost:8000/docs
▶️ Run Frontend
cd frontend

pip install -r requirements.txt

streamlit run app.py

Open:

http://localhost:8501
🐳 Run With Docker

Create .env file first.

Then run:

docker-compose up --build

FastAPI:

http://localhost:8000/docs

Streamlit:

http://localhost:8501
📌 API Endpoints
Upload PDF
POST /documents/upload
Ask Question
POST /chat/ask
Request
{
  "question": "What are the compliance requirements in this policy?"
}
Response
{
  "answer": "The policy requires audit-ready logging and privacy review.",
  "sources": [
    {
      "source": "policy.pdf",
      "page": 2,
      "content": "Relevant source text..."
    }
  ]
}
🧠 Hallucination Reduction Strategy

The assistant is instructed to answer only from retrieved document context.

If the answer is not present inside uploaded documents, the model responds:

I do not have enough information from the uploaded documents.

This significantly reduces hallucinations and improves groundedness.
