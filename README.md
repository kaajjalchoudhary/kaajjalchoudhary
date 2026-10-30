## Hi, I'm Kajal 👋

I'm a data engineer who likes turning messy raw data into clean, reliable, analytics-ready datasets.
I build pipelines that are tested, reproducible and easy to rerun, across orchestration, batch,
streaming and analytics engineering.

### 🔧 Tech I work with

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=postgresql&logoColor=white)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-E25A1C?style=flat&logo=apachespark&logoColor=white)
![Apache Airflow](https://img.shields.io/badge/Apache%20Airflow-017CEE?style=flat&logo=apacheairflow&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-231F20?style=flat&logo=apachekafka&logoColor=white)
![Delta Lake](https://img.shields.io/badge/Delta%20Lake-00ADD4?style=flat&logo=delta&logoColor=white)
![dbt](https://img.shields.io/badge/dbt-FF694B?style=flat&logo=dbt&logoColor=white)
![DuckDB](https://img.shields.io/badge/DuckDB-FFF000?style=flat&logo=duckdb&logoColor=black)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat&logo=githubactions&logoColor=white)

### 🧰 Open source

**[datasniff](https://github.com/kaajjalchoudhary/datasniff)**: know your data file before you load it. One command profiles any CSV, Parquet or JSON file, flags data quality problems (duplicates, nulls, PII, dirty values) and generates a dbt `schema.yml` with tests plus `CREATE TABLE` DDL for Postgres, BigQuery, Snowflake or DuckDB. Also available as a GitHub Action.

```bash
pip install git+https://github.com/kaajjalchoudhary/datasniff.git
datasniff orders.csv
```

### 🚀 Featured projects

| Project | What it does | Stack |
|---|---|---|
| [**Spark + Delta Lake Lakehouse**](https://github.com/kaajjalchoudhary/spark-delta-lakehouse) | Medallion (bronze/silver/gold) lakehouse for a ride-hailing feed with idempotent daily batches, MERGE upserts for late and corrected events, a reusable SCD Type 2 merge, point-in-time joins, a quarantine table and quality gates that stop bad runs | PySpark · Delta Lake · pytest |
| [**Climate & Air-Quality ELT**](https://github.com/kaajjalchoudhary/climate-elt-airflow) | Airflow 3 DAG that pulls hourly weather and air-quality data for six cities from a public API into a replayable landing zone, with dynamic task mapping, idempotent daily loads and data quality gates | Airflow · DuckDB · Python |
| [**NYC Taxi Batch Pipeline**](https://github.com/kaajjalchoudhary/Data-Engineering) | Cleans and enriches NYC taxi trips, gates every run with data quality checks, and publishes a partitioned trip table plus daily, hourly, zone and payment aggregates | PySpark · Parquet · pytest |
| [**Real-time E-commerce Streaming**](https://github.com/kaajjalchoudhary/realtime-ecommerce-streaming) | Consumes clickstream events from Kafka into event-time tumbling windows with per-partition watermarks, routes bad messages to a dead-letter topic, and upserts funnel metrics into Postgres | Kafka · PostgreSQL · Docker |
| [**Retail Analytics Warehouse**](https://github.com/kaajjalchoudhary/retail-analytics-dbt) | Models messy store extracts into a tested star schema with staging, marts and an incremental model, backed by 39 data tests | dbt · DuckDB · SQL |
| [**SQL Patterns for Data Engineers**](https://github.com/kaajjalchoudhary/sql-patterns-for-data-engineers) | Six SQL patterns that keep coming up in pipelines (dedupe to latest, gaps and islands, sessionization, running totals, top N per group, SCD Type 2), each with sample data and an expected result checked in CI | SQL · DuckDB |

Every project has CI that runs the tests plus an end-to-end run of the pipeline on every push.

### 🌱 Currently exploring

- Apache Iceberg, and how it compares with Delta Lake
- Cloud data platforms

