# Legal Document RAG Search API

## Project Overview

This project implements a Retrieval-Augmented Generation (RAG) search API for legal documents in Nepal. Currently it made for english converted nepali 'ACTS' and aims to be flexible in the near future. It leverages advanced natural language processing techniques to enable semantic search and context-aware querying of legal texts.

## Key Features

- Hybrid embedding search (BERT + TF-IDF)
- Reranker
- Semantic retrieval of legal document sections
- FastAPI-based backend
- Qdrant vector database for efficient document retrieval
- Support for multiple legal acts and collections

## Prerequisites

- Python 3.8+
- Docker
- pip (Python package manager)

## Technology Stack

- FastAPI
- PyTorch
- Transformers
- Scikit-learn
- Qdrant
- NumPy

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/pantshaswat/Legal-RAG.git
cd Legal-RAG
```

### 2. Set Up Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Start Qdrant Vector Database

Run Qdrant using Docker:

```bash
docker run -p 6333:6333 -p 6334:6334 \
    -v $(pwd)/qdrant_storage:/qdrant/storage:z \
    qdrant/qdrant
```

### 5. Gemini/Gorq api key configuration

Set your gemini api or Groq api key in the .env file.

## Running the Application

### Development Server

```bash
uvicorn main:app --reload
```
or
#### Using fast Api
```bash
pip install "fastapi[standard]"
cd app
fastapi dev main.py
```
The API will be available at `http://localhost:8000`

The swagger documentation at `http://localhost:8000/docs`

### API Endpoints

- `/api/v1/available-files`: gives available file names along with their description
- `/api/v1/evaluate`: Evaluate retrieval performance using MRR and MAP.
- `/api/v1/document/{collection_name}`: Delete a document and its collection.
- `/api/v1/test`: Store embeddings for a specific legal act
- `/api/v1/query`: Perform semantic search on legal documents


## Project Structure

```
legal-rag-nepal/
│
├── app/
│   ├── api/
│   ├── services/
│   |── vectorizers
|   |── main.py
|   └── ...
├── data/
│   |── processed/
│   |    └── json/
│   |        └── Finance/
|   └── raw/
│       └── Finance/
├── models/
├── qdrant_storage
├── requirements.txt
└── README.md
```

## Data Preparation

- Prepare legal documents as JSON files
- Works on English converted nepali acts, using file app/act_chunker.py
- Place JSON files in `data/processed/json/` directory
- Ensure each document follows the specified JSON structure

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

Distributed under the MIT License.
## Contact

Shaswat Pant - pantshaswat@gmail.com

Project Link: [https://github.com/pantshaswat/Legal-RAG](https://github.com/pantshaswat/Legal-RAG)