# Kajal Choudhary

**AI & Data Engineer** · GenAI · RAG · AI Agents · MCP · Databricks · PySpark · dbt · SQL · Python

Duisburg, Germany · Authorised to work in the EU · [LinkedIn](https://www.linkedin.com/in/kaajal-choudhary)

---

## Summary

AI and data engineer with 9+ years of experience across retail banking, retail, e-commerce and software. I design
and build end-to-end ETL/ELT pipelines on Databricks, PySpark and dbt, and deliver Generative AI on top of that
foundation: retrieval-augmented generation over enterprise data, AI agents with tool calling and the Model Context
Protocol, and LLM integrations with structured outputs. My work centres on the data quality, reconciliation and
governance that regulated environments require and that determine whether an AI system can be trusted.

## Professional experience

| Period | Role | Organisation | Key contributions |
|---|---|---|---|
| 2025 – present | Senior Data Analyst, Data Engineering, BI & AI | DVK Software · Global bank, credit risk programme | End-to-end Databricks/PySpark/dbt ETL pipelines on GCP feeding credit risk data marts; RAG solutions enabling natural-language access to risk datasets and data definitions; MCP-enabled AI agents automating validation, reconciliation and pipeline documentation; AI-assisted development and code review with Claude Code |
| 2023 – 2025 | Senior Data Analyst | TASC Outsourcing · Emirates NBD (retail banking), Dubai | Retail banking ETL pipelines, data models and reporting structures; customer segmentation and A/B testing; source-to-target mappings and data quality validation across Oracle, SQL Server and SAP |
| 2022 – 2023 | ETL & Data Engineering Analyst | Barclays Global Service Centre, Noida | SAS-to-Hadoop migration for financial risk reporting over 100TB+ of data; automated ETL workflows in Python and SAS contributing USD 8M+ in business value and a 40% improvement in SQL performance; Basel III/IV and IFRS-9 requirements translated into technical specifications |
| 2017 – 2022 | Senior Data Analyst / Analytics Engineer | Ahaka Solutions · Adidas (retail), MENA region | Predictive models for customer and campaign performance; automated retail data pipelines and reporting; digital analytics with GA4, Google Ads and Adobe Analytics |

**Education:** B.Tech, Computer Science & Engineering, Manav Rachna International University (2012 – 2016)
**Languages:** English (C1) · Hindi (native) · German (B1) · French (A2)

## Core expertise

**Data engineering**
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white) ![PySpark](https://img.shields.io/badge/PySpark-E25A1C?style=flat-square&logo=apachespark&logoColor=white) ![dbt](https://img.shields.io/badge/dbt-FF694B?style=flat-square&logo=dbt&logoColor=white) ![Apache Airflow](https://img.shields.io/badge/Apache%20Airflow-017CEE?style=flat-square&logo=apacheairflow&logoColor=white) ![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white) ![Delta Lake](https://img.shields.io/badge/Delta%20Lake-00ADD4?style=flat-square&logo=delta&logoColor=white) ![Apache Iceberg](https://img.shields.io/badge/Apache%20Iceberg-3C6EB4?style=flat-square) ![DuckDB](https://img.shields.io/badge/DuckDB-FFF000?style=flat-square&logo=duckdb&logoColor=black) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![Oracle](https://img.shields.io/badge/Oracle-F80000?style=flat-square) ![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?style=flat-square)

**Cloud and platforms**
![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=flat-square&logo=databricks&logoColor=white) ![Google Cloud](https://img.shields.io/badge/Google%20Cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=white) ![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white) ![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white) ![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=flat-square&logo=snowflake&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)

**Generative AI and machine learning**
![RAG](https://img.shields.io/badge/RAG-6E40C9?style=flat-square) ![Embeddings](https://img.shields.io/badge/Embeddings-8250DF?style=flat-square) ![Vector Search](https://img.shields.io/badge/Vector%20Search-0E8A16?style=flat-square) ![AI Agents](https://img.shields.io/badge/AI%20Agents-5A32A3?style=flat-square) ![MCP](https://img.shields.io/badge/MCP-111111?style=flat-square) ![Claude API](https://img.shields.io/badge/Claude%20API-D97757?style=flat-square&logo=anthropic&logoColor=white) ![OpenAI API](https://img.shields.io/badge/OpenAI%20API-412991?style=flat-square&logo=openai&logoColor=white) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)

**BI and reporting**
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat-square&logo=powerbi&logoColor=black) ![Tableau](https://img.shields.io/badge/Tableau-E97627?style=flat-square&logo=tableau&logoColor=white)

## Engineering principles

- **Idempotent by default.** Every job can be rerun or backfilled without duplicates: MERGE upserts, content hashes, checkpoints.
- **Bad data never reaches consumers.** Quality gates, quarantine tables, dead-letter topics and Write-Audit-Publish stop a bad batch before it lands.
- **Incremental, not full rebuilds.** CDC instead of full extracts, and in RAG only changed chunks are re-embedded, with deletes propagated to the index.
- **Proven, not claimed.** Every repository has CI that runs unit tests plus an end-to-end run of the pipeline on every push.
- **AI data needs the same discipline.** PII redaction, dedup and lineage matter as much for an embedding index or a fine-tuning set as for a warehouse table.

## Open-source portfolio

The repositories below are independent projects that demonstrate these practices end to end, from source
systems to an LLM-ready index or a dimensional mart. Each includes automated tests and CI.

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

### Flagship: data engineering for AI

**[rag-ingestion-pipeline](https://github.com/kaajjalchoudhary/rag-ingestion-pipeline)**: many RAG implementations re-embed the entire corpus on every run. This pipeline treats the vector index like any other table: documents are cleaned, PII-redacted, chunked on paragraph and sentence boundaries, deduplicated and synced **incrementally**, so unchanged docs are skipped, an edited paragraph re-embeds one chunk and deleted files leave nothing behind. Pluggable embedders, offline by default, every guarantee tested in CI.

```bash
pip install git+https://github.com/kaajjalchoudhary/rag-ingestion-pipeline.git
ragprep ingest docs/ && ragprep search "refund window"
```

### Tooling

**[datasniff](https://github.com/kaajjalchoudhary/datasniff)**: profiles any CSV, Parquet or JSON file, flags data quality problems (duplicates, nulls, PII, dirty values) and generates a dbt `schema.yml` with tests plus `CREATE TABLE` DDL for Postgres, BigQuery, Snowflake or DuckDB. Also available as a GitHub Action.

```bash
pip install git+https://github.com/kaajjalchoudhary/datasniff.git
datasniff orders.csv
```

### Selected projects

| Area | Project | What it does | Stack |
|---|---|---|---|
| AI data | [**RAG Ingestion Pipeline**](https://github.com/kaajjalchoudhary/rag-ingestion-pipeline) | Cleans, PII-redacts, chunks and deduplicates documents, then keeps a vector index in sync incrementally: content-hash skips, embeddings cached per chunk hash and model, deletes propagated. Tests prove a second run is a no-op and a one-paragraph edit re-embeds one chunk | Python · Embeddings · SQLite |
| Streaming & CDC | [**CDC Streaming into Delta Lake**](https://github.com/kaajjalchoudhary/cdc-streaming-lakehouse) | Debezium-style change events from Kafka applied to Delta Lake by Spark Structured Streaming, exactly once: LSN-ordered MERGE, soft deletes, idempotent bronze appends, dead letters and checkpoint restarts. Tests prove the Delta table matches the source row for row through a real broker | Kafka · Spark Streaming · Delta Lake |
| Lakehouse | [**Iceberg Write-Audit-Publish**](https://github.com/kaajjalchoudhary/iceberg-wap-lakehouse) | Smart-meter pipeline where every batch is merged into an Iceberg branch, audited there and only then fast-forwarded to `main`; a firmware-bug delivery is rejected and its re-delivery published. MERGE with merge-on-read, schema and partition evolution, compaction | PySpark · Apache Iceberg · pytest |
| Lakehouse | [**Spark + Delta Lake Lakehouse**](https://github.com/kaajjalchoudhary/spark-delta-lakehouse) | Medallion (bronze/silver/gold) lakehouse for a ride-hailing feed with idempotent daily batches, MERGE upserts for late and corrected events, a reusable SCD Type 2 merge, point-in-time joins, a quarantine table and quality gates that stop bad runs | PySpark · Delta Lake · pytest |
| Orchestration | [**Climate & Air-Quality ELT**](https://github.com/kaajjalchoudhary/climate-elt-airflow) | Airflow 3 DAG that pulls hourly weather and air-quality data for six cities from a public API into a replayable landing zone, with dynamic task mapping, idempotent daily loads and data quality gates | Airflow · DuckDB · Python |
| Batch | [**NYC Taxi Batch Pipeline**](https://github.com/kaajjalchoudhary/nyc-taxi-batch-pipeline) | Cleans and enriches NYC taxi trips, gates every run with data quality checks, and publishes a partitioned trip table plus daily, hourly, zone and payment aggregates | PySpark · Parquet · pytest |
| Streaming & CDC | [**Real-time E-commerce Streaming**](https://github.com/kaajjalchoudhary/realtime-ecommerce-streaming) | Consumes clickstream events from Kafka into event-time tumbling windows with per-partition watermarks, routes bad messages to a dead-letter topic, and upserts funnel metrics into Postgres | Kafka · PostgreSQL · Docker |
| Analytics engineering | [**Retail Analytics Warehouse**](https://github.com/kaajjalchoudhary/retail-analytics-dbt) | Models messy store extracts into a tested star schema with staging, marts and an incremental model, backed by 39 data tests | dbt · DuckDB · SQL |
| Analytics engineering | [**SQL Patterns for Data Engineers**](https://github.com/kaajjalchoudhary/sql-patterns-for-data-engineers) | Fifty-two SQL patterns that keep coming up in pipelines (dedupe to latest, gaps and islands, sessionization, SCD Type 2, snapshot diff, as-of joins, merge intervals, orphan records, period-over-period growth, recursive hierarchies, source-to-target reconciliation, inventory balances, bill-of-materials explosion, running totals with resets, null profiling and more), each with sample data and an expected result checked in CI | SQL · DuckDB |

Every project has CI that runs the tests plus an end-to-end run of the pipeline on every push.

## Current focus

- Embedding pipelines at scale: streaming document changes from Kafka into a vector store (pgvector)
- Evaluating RAG retrieval with golden question sets (recall@k, chunking strategy comparisons)
- Data quality for LLM training and fine-tuning data (dedup, PII, contamination checks)
- Streaming into Iceberg (Kafka to Iceberg with Flink or Spark)
- Running these pipelines on managed cloud platforms (object storage, managed Spark and Kafka)

## Contact

Open to AI and data engineering opportunities in Germany and the EU. Connect on [LinkedIn](https://www.linkedin.com/in/kaajal-choudhary).
