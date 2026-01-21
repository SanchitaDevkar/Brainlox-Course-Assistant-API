Brainlox Course Assistant API
Overview

The Brainlox Course Assistant API is a Flask-based RESTful application that enables users to interact with Brainlox technical course content through a conversational interface.
It uses web scraping, vector databases, and Retrieval Augmented Generation (RAG) to provide accurate, context-aware responses.

Key Capabilities

Extracts course information from Brainlox technical courses

Converts course data into vector embeddings

Stores embeddings in a vector database for semantic search

Provides a conversational API powered by RAG

Supports chat with conversation history

Features
Web Scraping

Scrapes Brainlox course data using BeautifulSoup

Uses multiple CSS selectors for robust extraction

Vector Database

Stores embeddings using ChromaDB

Enables fast similarity-based retrieval

RAG (Retrieval Augmented Generation)

Combines retrieved documents with LLM responses

Uses LangChain and LangGraph for orchestration

RESTful API

Provides endpoints for:

Health checking

Refreshing course data

Conversational interaction

Technology Stack

Backend Framework: Flask

Web Scraping: BeautifulSoup

Embeddings: Hugging Face sentence-transformers

Vector Store: ChromaDB

RAG Framework: LangChain, LangGraph

LLM: LLaMA 3 8B (via Groq API)

Project Structure
Brainlox-Course-Assistant-API
├── app.py
├── requirements.txt
├── .env
├── chroma_db/
├── image/
├── README.md

Setup Instructions
1. Clone the Repository
git clone <repository_url>
cd brainlox-course-assistant-api

2. Create a Virtual Environment
python -m venv venv

3. Activate the Virtual Environment

Windows

venv\Scripts\activate


Linux / macOS

source venv/bin/activate

4. Install Dependencies
pip install -r requirements.txt

5. Create Environment Variables

Create a .env file in the project root:

API_KEY=your_groq_api_key_here

Running the Application
python app.py


The API will be available at:

http://localhost:5000/api

API Endpoints
1. Health Check

GET /api/health

Checks whether the API is running and initialized.

Response Example:

{
  "status": "ok"
}

2. Refresh Course Data

POST /api/refresh

Clears the existing vector store and reloads course data from Brainlox.

3. Chat with Assistant

POST /api/chat

Send a query to the assistant and receive a context-aware response.

Request Body:

{
  "message": "What Python courses do you offer?",
  "conversation_history": []
}


Response Example:

{
  "status": "success",
  "answer": "We offer several Python courses...",
  "conversation_history": [
    {
      "role": "user",
      "content": "What Python courses do you offer?"
    },
    {
      "role": "assistant",
      "content": "We offer several Python courses..."
    }
  ]
}

Implementation Details

Course content is chunked using RecursiveCharacterTextSplitter

Embeddings are generated using Hugging Face sentence-transformers

Semantic retrieval is handled via ChromaDB

LangGraph manages the RAG workflow

Groq’s LLaMA 3 8B model generates final responses

Author

Sanchita Devkar

License

MIT License

Version

1.0.0
