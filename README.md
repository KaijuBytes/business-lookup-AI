# Business Lookup Assistant 🗺️

A simple, local **LLM-powered assistant** for looking up businesses. This project demonstrates a **Retrieval-Augmented Generation (RAG)** system built with **FastAPI** for the backend API, **LangChain** for orchestration, **HuggingFace Embeddings** and **FAISS** for efficient semantic search, and a simple web frontend (`index.html`) for interaction.

The assistant answers user queries by:
1. Embedding the user's input.
2. Performing a semantic search against a pre-indexed vector store (FAISS) of business data.
3. Passing the top-matched business documents to a Large Language Model (LLM) to generate a coherent, natural-language response.

***

## 🚀 Features

- **FastAPI Backend:** Provides a simple, scalable `/lookup` endpoint.
- **Semantic Search:** Uses `sentence-transformers/all-MiniLM-L6-v2` to create embeddings and **FAISS** to quickly find the most relevant businesses for any query (e.g., "vegan cafes near Bondi").
- **RAG System:** Leverages an LLM (e.g., Llama 3 via Ollama or Google Generative AI) to synthesize a human-like response from the retrieved business data.
- **Simple Frontend:** A basic HTML/CSS/JavaScript interface for easy testing.

***

## 🛠️ Setup Instructions

### 1. Prerequisites

You need **Python 3.9+** and **pip** installed on your system.

### 2. Clone the Repository

Use the correct GitHub URL to clone the project and navigate into the directory:

```bash
git clone https://github.com/KaijuBytes/business-lookup-AI
cd business-lookup-AI
```

### 3. Install Dependencies

Install all necessary Python packages, including LangChain components, FAISS, and sentence transformers, from the `requirements.txt` file:

```bash
pip install -r requirements.txt
```

### 4. Set Up Your Environment

This project supports using either a local LLM (like Llama 3 via Ollama) or an API-based LLM (like Google Generative AI):

- **Create a `.env` file:**  
    Create a file named `.env` in the project root directory. If you plan to use the Google Gemini API, add your API key to this file:

    ```
    # .env file content
    GOOGLE_API_KEY="YOUR_GOOGLE_API_KEY_HERE"
    ```

- **Install Ollama (Optional for Local LLM):**  
    If you choose to run the LLM locally, download and install [Ollama](https://ollama.com/). After installation, pull the required model (e.g., Llama 3) in your terminal:

    ```bash
    ollama pull llama3
    ```

### 5. Generate Embeddings and Vector Store

Run the `embedding.py` script to load the business data from `businesses.json`, generate HuggingFace Embeddings, and save the resulting searchable index to the local `faiss_index` directory:

```bash
python embedding.py
```
