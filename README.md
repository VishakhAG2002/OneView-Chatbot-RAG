# HPE OneView RAG Chatbot

A Retrieval-Augmented Generation (RAG) chatbot designed to simplify access to official HPE OneView documentation through natural language interaction.
The system enables users to ask specific technical or operational questions and receive accurate, context-grounded answers derived directly from HPE OneView documentation. This eliminates the need to manually navigate large and complex documentation sets.

## Executive Summary

HPE OneView documentation is comprehensive but often requires significant effort to navigate when users need precise, task-specific information.
This project introduces a conversational interface that allows users to retrieve exact answers using simple prompts. Instead of searching across multiple documents, users can directly ask questions such as:

* "How to add Active Directory in OneView?"
* "How to change cryptography mode to FIPS?"
* "Steps to perform backup restore operation."

The system retrieves relevant content and generates a concise, source-backed response, significantly reducing time to resolution. Currently, we have ingested only few documents like user guide- with more documentation fed to the RAG- we can ask wider range o OneView questions.

## Objective

The primary objective of this project was:
To eliminate the need for tedious manual documentation navigation and enable users to obtain precise, relevant answers from HPE OneView documentation using a single natural language prompt.

## Goals and Outcomes

### 1. Enable natural language interaction with documentation
Status: Achieved
Users can query the system conversationally and receive structured answers.

### 2. Reduce dependency on manual documentation search
Status: Achieved
The system shifts the experience from document-first to prompt-first interaction.

### 3. Provide accurate, context-grounded responses
Status: Achieved
All answers are generated using retrieved documentation content, reducing hallucination.

### 4. Include source citations for trust and verification
Status: Achieved
Each response includes references to source documents and pages.

### 5. Deliver a fast and responsive user experience
Status: Achieved
Low-latency response generation using optimized models ensures quick interactions.

### 6. Maintain conversational context for follow-up queries
Status: Achieved
The system supports short multi-turn conversations using recent chat history.

### 7. Support multiple documentation sources (PDF + Web)
Status: Achieved
The system ingests both PDF documents and web-based API references.

### 8. Build a lightweight and deployable architecture
Status: Achieved
The solution is optimized for deployment with minimal infrastructure overhead.

### 9. Ensure scalability of the retrieval pipeline
Status: Achieved (for current scope)
The architecture supports extension to larger document sets with minimal changes.

### 10. Provide an intuitive and clean user interface
Status: Achieved
The frontend offers a simple, focused chat-based interaction model.

## Overall Outcome
The primary goal of simplifying access to HPE OneView documentation has been successfully achieved.
Users no longer need to navigate extensive documentation manually. Instead, they can directly obtain precise answers through a single prompt, significantly improving efficiency and usability.

## Key Capabilities

* Natural language question answering over HPE OneView documentation
* Retrieval-Augmented Generation for accurate and grounded responses
* Semantic search using vector embeddings
* Source citation and traceability
* Conversational interface with context awareness
* Support for both PDF and web-based documentation
* Lightweight full-stack implementation

## How It Works

1. Documentation is collected from PDFs and web sources
2. Content is extracted, cleaned, and split into chunks
3. Each chunk is converted into vector embeddings
4. Embeddings are stored in a vector database
5. User queries are embedded and matched against stored content
6. Relevant chunks are retrieved and passed to the language model
7. The model generates a grounded response with source references

## System Architecture

The system follows a modular architecture with clear separation of concerns:

* Presentation Layer: Web-based chat interface
* API Layer: FastAPI backend
* RAG Engine: Retrieval and response generation
* Vector Store: ChromaDB
* Language Model: Gemini 2.5 Flash Lite

## Technology Stack

### Backend

* Python 3.11
* FastAPI
* Uvicorn
* Pydantic

### AI and Retrieval

* ONNX MiniLM-L6-v2 (Embeddings)
* ChromaDB (Vector Database)
* Gemini 2.5 Flash Lite (LLM)

### Frontend

* HTML
* CSS
* Vanilla JavaScript
* marked.js

### Deployment

* Render

## Project Structure

hpe-rag-chatbot/
├── config.py
├── embeddings.py
├── ingest.py
├── pdf_processor.py
├── web_scraper.py
├── rag_engine.py
├── server.py
├── chroma_db/
├── pdfs/
└── static/
    ├── index.html
    ├── css/styles.css
    └── js/app.js

## Setup Instructions

### 1. Clone the repository
git clone <repository-url>
cd hpe-rag-chatbot

### 2. Install dependencies
pip install -r requirements.txt

### 3. Configure environment variables
Create a `.env` file and add:
GOOGLE_API_KEY=your_api_key_here

### 4. Run ingestion pipeline
python ingest.py

### 5. Start the application
bash start.sh

### 6. Access the application
[http://localhost:8000](http://localhost:8000)

## API Endpoints

POST /api/chat — Submit a query
GET /api/health — Check system status
GET /api/stats — View document statistics

## Future Enhancements

* Streaming responses for improved user experience
* Hybrid search (keyword + vector search)
* Re-ranking models for improved retrieval precision
* OCR and structured data extraction
* Authentication and role-based access control
* Cloud-based vector database integration
* Evaluation metrics for response quality
* Admin interface for document management
* Feeding extensive OneView documentation to Rag, to enable chatbot to answer wider range of questions

## Conclusion

This project demonstrates a practical and effective approach to transforming how users interact with HPE OneView documentation.By replacing manual document navigation with prompt-based interaction, the system significantly reduces effort and improves efficiency. The core objective of enabling users to obtain precise, context-grounded answers through a single prompt has been successfully achieved. The solution provides a strong foundation for further development into a production-grade documentation intelligence system.
