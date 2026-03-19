# GraphRAG System Design

This document presents the system design of my GraphRAG architecture, including service separation, cloud deployment, and load-balancing strategy. It is continuously updated as the system evolves.

---

## Version 1

### Cloud Service Separation

![](./image/Cloud%20Service%20Separation.png)

Separated the core backend business logic into two dedicated services: **Graph Search Service** and **Graph Build Service**.

Introduced an **API Gateway** as the unified entry point for the frontend, and an **LLM Gateway** to manage interactions with external AI models.

### Cloud Deployment Architecture

![](./image/Cloud%20Deploy%20Architecture.png)

Designed the cloud deployment architecture with a **replicated search layer** and a **separate build path**.

User requests are routed through an **API Gateway** and **Load Balancer** to multiple **Search Service** replicas, while the **Build Service** handles graph-construction workflows independently.

Shared infrastructure is centralized through **Redis Cloud**, **Aura Neo4j Graph Database**, and **Google Cloud Storage** for SEC file storage and parsing.