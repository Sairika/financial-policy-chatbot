# Financial Policy Chatbot

AI-powered chatbot for answering questions about financial policy documents using Retrieval-Augmented Generation (RAG).

## Overview

This project implements a chatbot system that can answer questions about financial policy documents. It was developed as part of the AI Developer Assessment for Join Venture AI. The system uses vector similarity search to find relevant document sections and provides contextual answers with source attribution.

## Features

- PDF document processing and text extraction
- Vector-based semantic search using sentence transformers
- Conversational memory to maintain context
- Source tracking with page number references
- RAG (Retrieval-Augmented Generation) implementation

## Project Structure

```
financial-policy-chatbot/
├── README.md
├── requirements.txt
├── Financial_Rag_Based_Project.ipynb    # Main implementation notebook
├── Policy-file.pdf                  # Financial policy document
└── database/                            # Vector database storage
```

## Requirements

Based on the implemented notebook:

```
langchain==0.1.16
langchain-ibm==0.1.4
langchain-community
huggingface==0.0.1
huggingface-hub==0.23.4
sentence-transformers==2.5.1
chromadb
pypdf
wget==3.2
transformers
torch
```

## Implementation Details

The system uses:
- **Document Processing**: PyPDFLoader for PDF text extraction
- **Text Splitting**: CharacterTextSplitter with chunk_size=1500
- **Embeddings**: sentence-transformers/all-MiniLM-L6-v2 model
- **Vector Store**: ChromaDB for document storage and retrieval
- **Language Model**: meta-llama/Llama-3.1-8B-Instruct with 4-bit quantization
- **Memory**: ConversationBufferMemory for maintaining chat context

## How to Run

1. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

2. **Open the notebook**:
   ```bash
   jupyter notebook Financial_Rag_Based_Project.ipynb
   ```

3. **Run the cells sequentially**:
   - Install and import required packages
   - Load and process the PDF document
   - Create embeddings and vector database
   - Initialize the language model
   - Set up RAG chains (RetrievalQA and ConversationalRetrievalChain)
   - Start asking questions

## Usage

The notebook provides two interaction modes:

### 1. Single-turn Q&A (RetrievalQA)
```python
query = "what is debt policy?"
result = qa_retrieval.invoke({"query": query})
print(result["result"])
```

### 2. Conversational Q&A (ConversationalRetrievalChain)
```python
result = qa_conversational.invoke({
    "question": "What are the strategic priorities?", 
    "chat_history": chat_history
})
```

### Interactive Mode
The notebook includes an interactive `qa()` function for continuous chat:
```python
qa()  # Start interactive session
```

## Sample Questions

Based on the Policy-file.pdf content:
- "What is debt policy?"
- "What is the purpose of the financial policy objectives and strategies statement?"
- "What are the strategic priorities related to the Budget?"
- "Are general government borrowings increasing?"

## Technical Notes

- The system processes PDF documents into chunks of 1500 characters
- Uses CUDA for GPU acceleration (falls back to CPU if unavailable)
- Implements enhanced prompting for structured responses
- Includes memory management for conversational context
- Provides source document attribution in responses

## Hardware Requirements

- Python 3.8+
- 8GB+ RAM recommended
- GPU with 8GB+ VRAM (for Llama model)
- CUDA support recommended for optimal performance


For questions about this implementation, please contact: hasanmahmudnayeem3027@gmail.com
