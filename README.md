## Hi, I'm Kajal 👋

### Data Engineer · Data platforms for AI and analytics

I build the data layer that AI systems and analytics depend on: ingestion, CDC and streaming, lakehouse
tables, and the RAG pipelines that turn documents into a vector index an LLM can trust. My focus is the
unglamorous part that decides whether a model answers well: **clean, deduplicated, PII-safe, incrementally
updated data, with tests that prove it.**

```text
batch · streaming · CDC · lakehouse (Delta, Iceberg) · dbt · Airflow · RAG ingestion · embeddings · data quality
```

### 🏗️ How my projects fit together

Taken together, my repositories cover the path from a source system to an LLM-ready index or a BI mart.
Every stage below is implemented and tested in one of the projects further down.

```mermaid
flowchart LR
    A[Operational DB] -->|Debezium-style CDC| K[Kafka]
    C[Clickstream] --> K
    API[Public APIs] -->|Airflow 3| L[Landing zone]
    K -->|Spark Structured Streaming| BR[Bronze]
    L --> BR
    BR --> SI[Silver: cleaned, deduped, SCD2]
    SI -->|Write-Audit-Publish| GO[Gold / Iceberg main]
    GO -->|dbt| M[Star schema marts]
    D[Documents] -->|clean, PII-redact, chunk, dedupe| E[Incremental embeddings]
    E --> V[Vector index]
    V --> LLM[RAG / LLM apps]
    Q{{Quality gates and tests at every hop}} -.-> SI
    Q -.-> GO
    Q -.-> E
```

### 🧭 How I build pipelines

- **Idempotent by default.** Every job can be rerun or backfilled without duplicates: MERGE upserts, content hashes, checkpoints.
- **Bad data never reaches consumers.** Quality gates, quarantine tables, dead-letter topics and Write-Audit-Publish stop a bad batch before it lands.
- **Incremental, not full rebuilds.** CDC instead of full extracts, and in RAG only changed chunks are re-embedded, with deletes propagated to the index.
- **Proven, not claimed.** Each repo has CI that runs unit tests plus an end-to-end run of the pipeline on every push.
- **AI data needs the same discipline.** PII redaction, dedup and lineage matter as much for an embedding index or a fine-tuning set as for a warehouse table.

### 🔧 Tech I work with

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=postgresql&logoColor=white)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-E25A1C?style=flat&logo=apachespark&logoColor=white)
![Apache Airflow](https://img.shields.io/badge/Apache%20Airflow-017CEE?style=flat&logo=apacheairflow&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-231F20?style=flat&logo=apachekafka&logoColor=white)
![Delta Lake](https://img.shields.io/badge/Delta%20Lake-00ADD4?style=flat&logo=delta&logoColor=white)
![Apache Iceberg](https://img.shields.io/badge/Apache%20Iceberg-3C6EB4?style=flat&logoColor=white)
![dbt](https://img.shields.io/badge/dbt-FF694B?style=flat&logo=dbt&logoColor=white)
![DuckDB](https://img.shields.io/badge/DuckDB-FFF000?style=flat&logo=duckdb&logoColor=black)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat&logo=githubactions&logoColor=white)

**AI / ML data:**
![RAG](https://img.shields.io/badge/RAG-6E40C9?style=flat)
![Embeddings](https://img.shields.io/badge/Embeddings-8250DF?style=flat)
![Vector Search](https://img.shields.io/badge/Vector%20Search-0E8A16?style=flat)
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD21E?style=flat&logo=huggingface&logoColor=black)

### 🤖 Data engineering for AI

**[rag-ingestion-pipeline](https://github.com/kaajjalchoudhary/rag-ingestion-pipeline)**: most RAG demos re-embed everything on every run. This treats the vector index like any other table: documents are cleaned, PII-redacted, chunked on paragraph and sentence boundaries, deduplicated and synced **incrementally**, so unchanged docs are skipped, an edited paragraph re-embeds one chunk and deleted files leave nothing behind. Pluggable embedders, offline by default, every guarantee tested in CI.

```bash
pip install git+https://github.com/kaajjalchoudhary/rag-ingestion-pipeline.git
ragprep ingest docs/ && ragprep search "refund window"
```

### 🧰 Open source

**[datasniff](https://github.com/kaajjalchoudhary/datasniff)**: know your data file before you load it. One command profiles any CSV, Parquet or JSON file, flags data quality problems (duplicates, nulls, PII, dirty values) and generates a dbt `schema.yml` with tests plus `CREATE TABLE` DDL for Postgres, BigQuery, Snowflake or DuckDB. Also available as a GitHub Action.

```bash
pip install git+https://github.com/kaajjalchoudhary/datasniff.git
datasniff orders.csv
```

### 🚀 Featured projects


| Area | Project | What it does | Stack |
|---|---|---|---|
| 🤖 AI data | [**RAG Ingestion Pipeline**](https://github.com/kaajjalchoudhary/rag-ingestion-pipeline) | Cleans, PII-redacts, chunks and deduplicates documents, then keeps a vector index in sync incrementally: content-hash skips, embeddings cached per chunk hash and model, deletes propagated. Tests prove a second run is a no-op and a one-paragraph edit re-embeds one chunk | Python · Embeddings · SQLite |
| ⚡ Streaming & CDC | [**CDC Streaming into Delta Lake**](https://github.com/kaajjalchoudhary/cdc-streaming-lakehouse) | Debezium-style change events from Kafka applied to Delta Lake by Spark Structured Streaming, exactly once: LSN-ordered MERGE, soft deletes, idempotent bronze appends, dead letters and checkpoint restarts. Tests prove the Delta table matches the source row for row through a real broker | Kafka · Spark Streaming · Delta Lake |
| 🧊 Lakehouse | [**Iceberg Write-Audit-Publish**](https://github.com/kaajjalchoudhary/iceberg-wap-lakehouse) | Smart-meter pipeline where every batch is merged into an Iceberg branch, audited there and only then fast-forwarded to `main`; a firmware-bug delivery is rejected and its re-delivery published. MERGE with merge-on-read, schema and partition evolution, compaction | PySpark · Apache Iceberg · pytest |
| 🧊 Lakehouse | [**Spark + Delta Lake Lakehouse**](https://github.com/kaajjalchoudhary/spark-delta-lakehouse) | Medallion (bronze/silver/gold) lakehouse for a ride-hailing feed with idempotent daily batches, MERGE upserts for late and corrected events, a reusable SCD Type 2 merge, point-in-time joins, a quarantine table and quality gates that stop bad runs | PySpark · Delta Lake · pytest |
| 🗓️ Orchestration | [**Climate & Air-Quality ELT**](https://github.com/kaajjalchoudhary/climate-elt-airflow) | Airflow 3 DAG that pulls hourly weather and air-quality data for six cities from a public API into a replayable landing zone, with dynamic task mapping, idempotent daily loads and data quality gates | Airflow · DuckDB · Python |
| 📦 Batch | [**NYC Taxi Batch Pipeline**](https://github.com/kaajjalchoudhary/nyc-taxi-batch-pipeline) | Cleans and enriches NYC taxi trips, gates every run with data quality checks, and publishes a partitioned trip table plus daily, hourly, zone and payment aggregates | PySpark · Parquet · pytest |
| ⚡ Streaming & CDC | [**Real-time E-commerce Streaming**](https://github.com/kaajjalchoudhary/realtime-ecommerce-streaming) | Consumes clickstream events from Kafka into event-time tumbling windows with per-partition watermarks, routes bad messages to a dead-letter topic, and upserts funnel metrics into Postgres | Kafka · PostgreSQL · Docker |
| 📊 Analytics engineering | [**Retail Analytics Warehouse**](https://github.com/kaajjalchoudhary/retail-analytics-dbt) | Models messy store extracts into a tested star schema with staging, marts and an incremental model, backed by 39 data tests | dbt · DuckDB · SQL |
| 📊 Analytics engineering | [**SQL Patterns for Data Engineers**](https://github.com/kaajjalchoudhary/sql-patterns-for-data-engineers) | Thirty-six SQL patterns that keep coming up in pipelines (dedupe to latest, gaps and islands, sessionization, SCD Type 2, snapshot diff, as-of joins, merge intervals, orphan records, period-over-period growth, recursive hierarchies, source-to-target reconciliation and more), each with sample data and an expected result checked in CI | SQL · DuckDB |

Every project has CI that runs the tests plus an end-to-end run of the pipeline on every push.

### 🌱 Currently exploring

- Embedding pipelines at scale: streaming document changes from Kafka into a vector store (pgvector)
- Evaluating RAG retrieval with golden question sets (recall@k, chunking strategy comparisons)
- Data quality for LLM training and fine-tuning data (dedup, PII, contamination checks)
- Streaming into Iceberg (Kafka to Iceberg with Flink or Spark)
- Running these pipelines on managed cloud platforms (object storage, managed Spark and Kafka)
