Brainlox Course Assistant API
Flask RESTful API for Brainlox course assistant with web scraping, vector database storage, and RAG-based chat capabilities.

Extracts data from Brainlox Technical Courses
Creates embeddings and stores them in a vector database
Provides a RESTful API for chatting about Brainlox courses
Features
Web scraping to extract course information from Brainlox
Vector database storage using Chroma DB
RAG (Retrieval Augmented Generation) system using LangChain
RESTful API endpoints for:
Health checking
Data refreshing
Conversation handling
Requirements
See requirements.txt for all dependencies.

Setup
Clone the Repository
git clone <repository_url>
cd brainlox-course-assistant-api
Create a Virtual Environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
Install Dependencies
pip install -r requirements.txt
Create a .env File
Create a .env file in the project root and add your API key:

API_KEY=your_groq_api_key_here
Running the API
python app.py
The API will be available at: http://localhost:5000/api

API Endpoints
Health Check
GET /api/health
Checks the status and initialization state of the API.

Refresh Course Data
POST /api/refresh
Clears the vector store and reloads course data from Brainlox.

Chat
POST /api/chat
Sends a message to the assistant.

Request Body:

{
  "message": "What Python courses do you offer?",
  "conversation_history": []  // Optional array of previous messages
}
Response:

{
  "status": "success",
  "answer": "We offer several Python courses...",
  "conversation_history": [
    {"role": "user", "content": "What Python courses do you offer?"},
    {"role": "assistant", "content": "We offer several Python courses..."}
  ]
}
Implementation Notes
The system uses BeautifulSoup for web scraping with multiple CSS selectors for robust extraction.
Embeddings are created using Hugging Face's sentence-transformers model.
Document chunking is done with RecursiveCharacterTextSplitter.
The RAG system uses LangGraph for orchestration.
The LLM used is Llama 3 8B provided through Groq.
Author:Sanchita Devkar
License: MIT License
Version: 1.0.0
