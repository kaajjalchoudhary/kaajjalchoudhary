## Hi, I'm Kajal 👋

I'm a data engineer working on the data side of AI. I turn messy raw data into clean, reliable datasets
for analytics **and** for AI systems: RAG ingestion, embedding pipelines, vector indexes and the data
quality that decides whether an LLM answers well. I build pipelines that are tested, reproducible and easy to rerun,
across orchestration, batch, streaming and analytics engineering.

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

| Project | What it does | Stack |
|---|---|---|
| [**RAG Ingestion Pipeline**](https://github.com/kaajjalchoudhary/rag-ingestion-pipeline) | Cleans, PII-redacts, chunks and deduplicates documents, then keeps a vector index in sync incrementally: content-hash skips, embeddings cached per chunk hash and model, deletes propagated. Tests prove a second run is a no-op and a one-paragraph edit re-embeds one chunk | Python · Embeddings · SQLite |
| [**CDC Streaming into Delta Lake**](https://github.com/kaajjalchoudhary/cdc-streaming-lakehouse) | Debezium-style change events from Kafka applied to Delta Lake by Spark Structured Streaming, exactly once: LSN-ordered MERGE, soft deletes, idempotent bronze appends, dead letters and checkpoint restarts. Tests prove the Delta table matches the source row for row through a real broker | Kafka · Spark Streaming · Delta Lake |
| [**Iceberg Write-Audit-Publish**](https://github.com/kaajjalchoudhary/iceberg-wap-lakehouse) | Smart-meter pipeline where every batch is merged into an Iceberg branch, audited there and only then fast-forwarded to `main`; a firmware-bug delivery is rejected and its re-delivery published. MERGE with merge-on-read, schema and partition evolution, compaction | PySpark · Apache Iceberg · pytest |
| [**Spark + Delta Lake Lakehouse**](https://github.com/kaajjalchoudhary/spark-delta-lakehouse) | Medallion (bronze/silver/gold) lakehouse for a ride-hailing feed with idempotent daily batches, MERGE upserts for late and corrected events, a reusable SCD Type 2 merge, point-in-time joins, a quarantine table and quality gates that stop bad runs | PySpark · Delta Lake · pytest |
| [**Climate & Air-Quality ELT**](https://github.com/kaajjalchoudhary/climate-elt-airflow) | Airflow 3 DAG that pulls hourly weather and air-quality data for six cities from a public API into a replayable landing zone, with dynamic task mapping, idempotent daily loads and data quality gates | Airflow · DuckDB · Python |
| [**NYC Taxi Batch Pipeline**](https://github.com/kaajjalchoudhary/Data-Engineering) | Cleans and enriches NYC taxi trips, gates every run with data quality checks, and publishes a partitioned trip table plus daily, hourly, zone and payment aggregates | PySpark · Parquet · pytest |
| [**Real-time E-commerce Streaming**](https://github.com/kaajjalchoudhary/realtime-ecommerce-streaming) | Consumes clickstream events from Kafka into event-time tumbling windows with per-partition watermarks, routes bad messages to a dead-letter topic, and upserts funnel metrics into Postgres | Kafka · PostgreSQL · Docker |
| [**Retail Analytics Warehouse**](https://github.com/kaajjalchoudhary/retail-analytics-dbt) | Models messy store extracts into a tested star schema with staging, marts and an incremental model, backed by 39 data tests | dbt · DuckDB · SQL |
| [**SQL Patterns for Data Engineers**](https://github.com/kaajjalchoudhary/sql-patterns-for-data-engineers) | Nineteen SQL patterns that keep coming up in pipelines (dedupe to latest, gaps and islands, sessionization, SCD Type 2, snapshot diff, as-of joins, merge intervals, orphan records, period-over-period growth and more), each with sample data and an expected result checked in CI | SQL · DuckDB |

Every project has CI that runs the tests plus an end-to-end run of the pipeline on every push.

### 🌱 Currently exploring

- Embedding pipelines at scale: streaming document changes from Kafka into a vector store (pgvector)
- Evaluating RAG retrieval with golden question sets (recall@k, chunking strategy comparisons)
- Data quality for LLM training and fine-tuning data (dedup, PII, contamination checks)
- Streaming into Iceberg (Kafka to Iceberg with Flink or Spark)
- Cloud data platforms
