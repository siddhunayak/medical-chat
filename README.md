# Memory-Augmented Retrieval Chatbot using LLMs

## Overview
This project implements a **memory-augmented retrieval-based chatbot** using **LangChain**, **Hugging Face LLMs**, and **FAISS**. The chatbot efficiently processes **PDF documents**, stores embeddings in a **vector database**, and retrieves relevant context to generate **accurate and contextual responses** using a **large language model (LLM)**.

## Features
- 📄 **PDF Document Processing**: Extracts text from PDFs using `PyPDFLoader`.
- 🔍 **Efficient Text Chunking**: Splits documents into **manageable chunks** with `RecursiveCharacterTextSplitter`.
- 🧠 **Vector Database Storage**: Stores embeddings using `FAISS` for fast retrieval.
- 🤖 **LLM Integration**: Uses **Mistral-7B-Instruct-v0.3** via Hugging Face Inference API.
- 🎤 **Interactive Chatbot UI**: Built with **Streamlit** for real-time user queries.
- ⚡ **Optimized Retrieval Pipeline**: Custom prompt engineering and dynamic retrieval settings.

## Project Structure
```
├── create_memory_for_llm.py      # Loads PDFs, extracts text, and stores embeddings in FAISS
├── create_memory_with_llm.py     # Loads FAISS and LLM, retrieves relevant chunks, and answers queries
├── medi.py                       # Streamlit-based chatbot for user interaction
├── vectorstore/                  # Directory for storing FAISS vector database
└── README.md                     # Project documentation
```

## Installation
### 1. Clone the Repository
```bash
git clone https://github.com/siddhunayak/memory-chatbot.git
cd memory-chatbot
```

### 2. Create a Virtual Environment & Install Dependencies
```bash
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
pip install -r requirements.txt
```

### 3. Set Up Hugging Face Token
Create a `.env` file and add:
```bash
HF_TOKEN=your_huggingface_api_key
```
Or set it directly in the environment:
```bash
export HF_TOKEN=your_huggingface_api_key  # On Windows use `set HF_TOKEN=your_huggingface_api_key`
```

## Usage
### 1. Generate Embeddings from PDF Files
Ensure your PDFs are in the `data/` directory, then run:
```bash
python create_memory_for_llm.py
```

### 2. Run the Chatbot in CLI
```bash
python create_memory_with_llm.py
```

### 3. Launch the Chatbot UI
```bash
streamlit run medi.py
```

## Customization
### Modify the Retrieval Pipeline
- Adjust chunking size in `create_memory_for_llm.py`:
```python
text_splitter = RecursiveCharacterTextSplitter(chunk_size=500, chunk_overlap=50)
```
- Modify the prompt template in `create_memory_with_llm.py`:
```python
CUSTOM_PROMPT_TEMPLATE = """
Use the provided context to answer the question accurately.
Context: {context}
Question: {question}
"""
```

## Technologies Used
- **LangChain** (for retrieval-based LLM interaction)
- **FAISS** (for fast vector-based search)
- **Hugging Face Transformers** (for embedding generation and LLM inference)
- **Streamlit** (for chatbot UI)
- **Python** (with Pandas, NumPy, and other dependencies)
## Interface Preview  
Here is a preview of the chatbot interface:  

![Chatbot Interface](/images/chatbot.png)  
## License
This project is open-source under the **MIT License**.

