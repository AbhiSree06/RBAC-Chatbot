# RBAC-Based RAG Chatbot (FastAPI + Streamlit + Hugging Face)

This project is a **Role-Based Access Control (RBAC) powered Retrieval-Augmented Generation (RAG) chatbot**, built using:

- **FastAPI** → Backend API  
- **Streamlit** → Web UI  
- **Sentence Transformers** → Embeddings  
- **Vector Store** → Semantic search  
- **Hugging Face Inference API** → LLM (Mistral-7B-Instruct)  
- **JWT Authentication** → Secure access  
- **RBAC** → Role-based permissions  
- **Session Management** → Persistent user login  

---

## **High-Level System Architecture**

###  Components

1. **Frontend (Streamlit)**
   - User login page  
   - Chat interface  
   - Sends queries to FastAPI backend  
   - Stores session locally  
   - Displays answers and retrieved sources  

2. **Backend (FastAPI)**
   - `/auth/login` → JWT authentication  
   - `/chat` → Secure RAG endpoint  
   - Validates JWT on every request  
   - Extracts user role from token  

3. **RAG Pipeline**
   - Converts user query into embeddings  
   - Searches vector database for relevant chunks  
   - Builds structured prompt  
   - Sends prompt to Hugging Face LLM  
   - Returns human-readable response + sources  

4. **LLM Layer (Hugging Face)**
   - Uses: `mistralai/Mistral-7B-Instruct-v0.2`
   - Called via `huggingface_hub.InferenceClient`
   - Avoids unreliable direct API calls  

5. **Vector Store**
   - Stores document chunks + embeddings  
   - Supports semantic similarity search  

6. **RBAC (Role-Based Access Control)**
   - Different roles (e.g., ENGINEERING, HR, ADMIN)
   - Controls which actions a user can perform  


