# Vamsi A.

**Backend Engineer · Distributed Systems**

I build high-volume, event-driven transaction systems — 1M+ daily records under sub-200 ms SLAs across financial services and healthcare. Most of the interesting work sits in the unglamorous parts: Kafka consumer semantics, idempotency and ledger integrity, and dragging batch pipelines into real time without a big-bang cutover.

Software Engineer at Goldman Sachs. Previously Elevance Health and eBay.

---

### What I work on

- **Event-driven systems** — Kafka, Flink, effectively-once delivery, replay-safe consumers, dead-letter recovery
- **Correctness under load** — idempotent processing, write-ahead tracking, deduplicating consumers, versioned event schemas and API contracts for downstream teams
- **Batch → real-time migrations** — decomposing legacy monoliths into Spring Boot services with incremental cutover plans
- **Reliability** — SLIs/SLOs, failure injection, backpressure and load shedding, lag-aware autoscaling

### Stack

**Languages** — Java · Go · Python · Kotlin · SQL
**Backend** — Spring Boot · FastAPI · Node.js · REST / OpenAPI
**Data & streaming** — Kafka · Flink · PostgreSQL (pgvector) · S3
**Infra** — Kubernetes · Docker · Helm · Terraform · Argo CD · Azure (AKS, Azure DevOps) · GitHub Actions
**Observability** — Prometheus · Grafana

---

### Selected work

**[Distributed Log Ingestion & Query Platform](https://github.com/vamsi-ar/log-platform)** · Go, Kafka, Kubernetes, S3, Prometheus

Log platform with hot/cold tiered storage: an indexed in-memory hot store (≤6h) that a compactor drains into gzip, date-partitioned S3 objects, fronted by a single query API that fans out across tiers and merges results. p95 holds at 1 ms on the hot tier, flat from baseline through a 10× write burst. Idempotent producers (`acks=all`, `min.insync.replicas=2`), queue-depth backpressure that sheds with HTTP 503, and HPA autoscaling on Kafka consumer lag — validated by a failure-injection harness that restarts brokers under sustained writes with no acknowledged write lost.

**[Lens — Real-Time Multimodal AI Vision Assistant](https://github.com/vamsi-ar/lens)** · Python, FastAPI, Kotlin/Compose, pgvector

Camera + voice in, spoken answer out, on phone and smart glasses. A Kotlin/Compose Android client and FastAPI backend orchestrate Whisper STT, a streaming vision LLM, and neural TTS into one pipeline that begins speaking before the model finishes generating. Median response latency down 47% (8.8s → 4.7s) and time-to-first-audio to 1.7s, through per-stage instrumentation, an 82M-parameter local TTS on Apple GPU, and first-token request hedging to clip LLM tail latency. Includes a visual memory system — "where did I leave my keys?" — with CLIP embeddings in pgvector, hybrid similarity + recency retrieval, exposed to the model as an agentic tool.

---

M.S. Computer Science, Sacred Heart University · B.Tech Computer Science, GNA University

**Reach me** — vamsi.a.swe@gmail.com · [LinkedIn](https://www.linkedin.com/in/vamsi-arumalla-5510741a5)
