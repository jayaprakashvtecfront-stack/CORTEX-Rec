# CORTEX-Rec
This project builds an end-to-end recommendation system for shopping data, using a two-stage design with fast candidate generation followed by expressive ranking. It mirrors production RecSys architectures while remaining feasible to run on a local laptop environment.

An End-to-End Hybrid Retrieval-and-Ranking Recommendation System

CORTEX-Rec is a practical, end-to-end recommendation system designed around modern
industry architectures while remaining feasible to implement and run on a single
developer’s laptop. It mirrors how production recommender systems are built,
deployed, and evaluated.

The system follows a two-stage recommendation system design:
fast candidate retrieval to reduce the search space, followed by a deep ranking
stage to score and order items.

---------------------------------------------------------------------

KEY FEATURES

Hybrid Candidate Generation
- Vector-based retrieval using FAISS
- Graph-based collaborative signals using LightGCN-style embeddings

Deep Ranking Model
- Neural ranking over user history, item features, and interaction signals
- Designed for relevance, latency, and engineering simplicity

Multimodal Item Representation (Optional)
- Text embeddings from product titles and descriptions
- Image embeddings using pretrained CNNs
- Fusion network for unified item embeddings

LLM-Based Enrichment (Optional)
- Lightweight metadata extraction from item text
- Session intent summarization for cold-start robustness

Production-Oriented MLOps
- Reproducible pipelines
- Versioned artifacts and models
- Offline evaluation and reporting
- Containerized inference services
- Minimal-cost AWS integration

---------------------------------------------------------------------

SYSTEM ARCHITECTURE

User Request
 -> Candidate Generation
    -> Vector Retrieval (FAISS)
    -> Graph Retrieval (LightGCN-style)
 -> Candidate Union
 -> Deep Ranking Model
 -> Top-K Recommendations

The system is split into offline training pipelines and online inference services,
reflecting real-world recommender system workflows.

---------------------------------------------------------------------

OFFLINE TRAINING PIPELINE

- Data ingestion and schema validation
- Feature engineering for users and items
- Optional embedding computation (text, image, graph)
- Ranker training using implicit feedback
- Offline evaluation (Recall@K, NDCG@K, AUC)
- Versioned artifact packaging (models, indexes, metadata)

All pipelines are configuration-driven and reproducible.

---------------------------------------------------------------------

ONLINE INFERENCE

Online inference is served via containerized APIs.

For each request:
1. Load the latest released artifacts
2. Retrieve candidate items
3. Rank candidates
4. Return Top-K recommendations with lightweight explanations

The design balances latency, cost, and maintainability.

---------------------------------------------------------------------

EVALUATION

Candidate Generation Metrics
- Recall@K

Ranking Metrics
- NDCG@K
- AUC

Additional Diagnostics
- Coverage
- Diversity
- Popularity bias analysis

Evaluation follows standard industry recommendation system practices.

---------------------------------------------------------------------

MINIMAL-COST AWS INTEGRATION

AWS services are used only where they add practical value.

- S3 for versioned model and artifact storage
- ECR for container image storage
- Lambda (optional) for a lightweight demo inference endpoint

This setup provides production realism while keeping cloud costs minimal.

---------------------------------------------------------------------

PROJECT GOALS

- Build an end-to-end recommender system, not just a model
- Apply modern machine learning methods used in real systems
- Emphasize engineering, MLOps, and system design
- Keep the system understandable, extendable, and maintainable

---------------------------------------------------------------------

TARGET AUDIENCE

- Recommendation system engineers
- Machine learning engineers
- Data scientists transitioning to ML engineering
- Students learning production recommender systems
- Portfolio and interview preparation
- Experimentation with hybrid recommendation architectures

---------------------------------------------------------------------

FUTURE EXTENSIONS

- Online A/B testing simulation
- Real-time feature updates
- Advanced reranking constraints
- Monitoring and drift detection
- Scaling to larger public datasets

---------------------------------------------------------------------
LICENSE

Apache 2.0
