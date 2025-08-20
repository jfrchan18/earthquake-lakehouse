# Earthquake Lakehouse (Databricks • Medallion)

An end-to-end ETL that ingests USGS Earthquake GeoJSON and lands it in **Bronze → Silver → Gold** Delta tables, with a **Databricks SQL** dashboard. No Azure services, no external BI—everything stays inside Databricks.

## Goals
- Scheduled ingestion from public API (no API key)
- Delta tables per Medallion: bronze (raw), silver (clean), gold (serving)
- DBSQL dashboard (counts, magnitude trends, map)

## Stack
Databricks (Workspace, Workflows, SQL), Apache Spark, Delta Lake (OSS), Python (requests), DBFS/Volumes.

## Quick Start (Databricks)
1. **Compute:** Create cluster `c_earthquake_dev` (DBR 14.x LTS, auto-terminate 20–30m).
2. **Catalog/Schemas:**  
   - With Unity Catalog: `earthquake` → `bronze|silver|gold`  
   - Without UC: create DBs `earthquake_bronze|_silver|_gold`
3. **Repo:** Repos → Clone this repo (`earthquake-lakehouse`).
4. **SQL Warehouse:** Create `wh_earthquake_demo` (small, auto-stop).
5. **Workflow:** Create `wf_earthquake_etl` with 3 tasks (A→B→C). (We’ll wire code later.)

## Repo Structure
