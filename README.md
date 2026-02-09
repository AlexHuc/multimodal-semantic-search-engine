# Multimodal Semantic Search Engine

**Production-ready multimodal search system using vision-language embeddings and vector similarity.**

![](./imgs/multimodal_semantic_search_arhitecture.png)

---

## Overview

This project implements an **end-to-end multimodal semantic search platform** that allows users to:

- Search images using natural language  
- Find visually similar assets  
- Retrieve semantically related content  
- Power creative workflows (design, media, e-commerce)

The system uses **vision-language models (CLIP / SigLIP)** to encode both text and images into a shared embedding space and performs similarity search using a vector database.

This type of system is commonly used in:

- Creative AI tools  
- Digital asset management  
- E-commerce product discovery  
- Content recommendation engines  

---

## Business Problem

Modern organizations manage millions of product images from e-commerce platforms.

Traditional keyword search fails because:

- Images often have inconsistent or missing tags  
- Products with similar appearance may have different names  
- Manual labeling is expensive and error-prone  

### Example

A user searches:

> “black leather backpack”

But the product title is:

> “urban commuter bag”

Result → relevant items may not be retrieved.

---

## Solution

Build a **multimodal semantic retrieval system** that:

1. Encodes images and text into embeddings  
2. Stores embeddings in a vector database  
3. Performs nearest-neighbor search  
4. Returns semantically relevant results  

Core capabilities:

- Text → Image search  
- Image → Image similarity  
- Hybrid semantic retrieval  
- Low-latency inference API  

---

## System Architecture

```
User Query (Text or Image)
        |
        v
Embedding Service (CLIP / SigLIP)
        |
        v
Vector Database (Qdrant)
        |
        v
Similarity Search (Top-K)
        |
        v
Results API (FastAPI)
```

---

## Tech Stack

### Machine Learning

- PyTorch  
- HuggingFace Transformers  
- CLIP / SigLIP vision-language models  
- Sentence Transformers (optional)  

### Backend

- FastAPI  
- Python 3.11  

### Vector Storage

- Qdrant (vector database)  
- Approximate Nearest Neighbor search  

### Infrastructure

- Docker  
- Docker Compose  
- Kubernetes (optional production deployment)  

### Observability

- Prometheus (metrics)  
- Grafana (dashboard)  
- Structured logging  

---

## Features

- Multimodal embeddings (image + text)  
- Batch indexing pipeline  
- Real-time semantic search API  
- GPU-accelerated inference  
- Scalable vector similarity search  
- REST endpoints for integration with products  

---

## Repository Structure

```
multimodal-semantic-search-engine/
│
├── shopee-product-matching-data/
│   ├──  train_images/
│   ├──  test_images/
│   ├──  train.csv
│   ├──  test.csv
│   └──  sample_submission.csv
│
├── apps/
│   ├── api/
│   │   ├── main.py
│   │   ├── routes/
│   │   └── schemas/
│   │
│   ├── embedding-service/
│   │   ├── model_loader.py
│   │   ├── inference.py
│   │   └── utils.py
│
├── pipelines/
│   ├── data_ingestion.py
│   ├── image_preprocessing.py
│   ├── embedding_generation.py
│   └── indexing_qdrant.py
│
├── infrastructure/
│   ├── docker/
│   ├── kubernetes/
│   └── monitoring/
│
├── configs/
│   ├── model_config.yaml
│   ├── app_config.yaml
│
├── tests/
│
├── notebooks/
│   └── experimentation.ipynb
│
├── docker-compose.yml
├── requirements.txt
└── README.md
```

---

## Data Pipeline

1. Ingest raw images and product information  
2. Preprocess images (resize, normalize)  
3. Generate embeddings using CLIP  
4. Store embeddings in Qdrant  
5. Index metadata  

Supports:

- Batch indexing  
- Incremental updates  
- Re-indexing  

---

## Dataset

We use the **Shopee Product Matching dataset**, which provides:

- Product images and associated product IDs  
- CSV files for training and test sets  
- Suitable for image-to-image similarity and product matching tasks  

**Dataset URL:** [Shopee Product Matching on Kaggle](https://www.kaggle.com/competitions/shopee-product-matching/data)

---

## API Endpoints

### Search by Text

```
POST /search/text
```

Input:

```
{
  "query": "black leather backpack",
  "top_k": 5
}
```

---

### Search by Image

```
POST /search/image
```

Returns visually similar items.

---

### Health Check

```
GET /health
```

---

## Requirements

### Hardware

Recommended:

- NVIDIA GPU (8GB+ VRAM)  
- 16GB RAM  

Minimum:

- CPU inference supported (slower)  

---

### Software

- Python 3.11  
- Docker  
- CUDA (for GPU acceleration)  

---

## Installation

```
git clone https://github.com/yourusername/multimodal-search-engine.git
cd multimodal-search-engine
```

Create environment:

```
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

---

## Running Locally

```
docker-compose up --build
```

This launches:

- API service  
- Embedding service  
- Qdrant vector DB  

---

## Index Sample Dataset

```
python pipelines/embedding_generation.py
python pipelines/indexing_qdrant.py
```

---

## Deployment

### Docker

Each component is containerized:

- API service  
- Embedding service  
- Vector DB  

---

### Kubernetes (Production)

Includes:

- Horizontal pod autoscaling  
- GPU node support  
- Rolling deployments  
- Service mesh compatible  

Deployment:

```
kubectl apply -f infrastructure/kubernetes/
```

---

## Performance Considerations

- Batch embedding generation  
- ANN indexing for fast retrieval  
- GPU inference optimization  
- Caching frequent queries  
- Async API endpoints  

---

## Future Improvements

- Add multimodal RAG (retrieval-augmented generation)  
- Integrate diffusion-based image editing  
- Implement user feedback loop  
- Online learning for ranking  
- Feature store integration  

---

## Use Cases

- E-commerce product similarity search  
- Visual recommendation systems  
- Creative asset discovery  
- Marketing and catalog management  

---

## Why This Project Matters

This system demonstrates:

- Multimodal AI engineering  
- Production ML pipelines  
- Embedding-based retrieval  
- Scalable inference services  
- Real-world e-commerce impact  

It reflects how modern AI products are built:

> **Models + Infrastructure + APIs + Observability**

---

# License

This dataset is free for research use. Redistribution of images may be restricted please check the Kaggle competition rules.
