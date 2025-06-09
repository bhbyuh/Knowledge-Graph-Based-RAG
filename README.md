# Graph RAG with Neo4j Knowledge Graph

Retrieval-Augmented Generation (RAG) has shown remarkable results in many NLP applications — but traditional RAG often fails in scenarios requiring multi-hop reasoning or connecting scattered facts across documents.

This project implements a **Graph RAG** system built on top of a **Knowledge Graph** using **Neo4j**, enabling structured and explainable reasoning over text.

---

## Motivation

Traditional RAG systems retrieve top-k chunks based on similarity — but they can struggle with:
- Multi-hop questions across documents
- Connecting disparate facts
- Traceable reasoning paths

**Graph RAG** addresses this by:
- Extracting structured triplets from raw text
- Building a Knowledge Graph (KG) in Neo4j
- Retrieving relevant subgraphs (communities) instead of flat chunks
- Passing connected context to an LLM for generation

---

## How It Works

1. **Text Preprocessing**  
   Raw documents are split and parsed to extract (subject, predicate, object) triplets using NLP techniques.

2. **Graph Construction**  
   The triplets are stored in Neo4j, forming a semantic graph of entities and relationships.

3. **Query Handling**  
   On user query, graph traversal is performed to fetch connected nodes (community) relevant to the query intent.

4. **Answer Generation**  
   The retrieved subgraph context is passed to an LLM (OpenAI) for generating the final answer.

---

## Tech Stack

- **Python**  
- **Neo4j** (Graph database)
- **Langchain / OpenAI** (for generation)
- **spaCy / transformers** (for NLP triplet extraction)
