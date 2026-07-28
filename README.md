# Jorge Molina

**Senior Data Engineer** — Databricks · PySpark · Delta Lake · Snowflake

Production data platforms: ingestion, transformation, and the reliability layer around them. Currently at CI&T; previously Globant and Mobyan (Santander Group). Around five years building pipelines other teams depend on.

## In the open

**[open-payments-lakehouse](https://github.com/Joorgem/open-payments-lakehouse)** — a lakehouse over real, messy Brazilian government data (Receita Federal's CNPJ registry). The PySpark/Delta core is tested locally and in CI and deployed to Databricks Free Edition with its actual limits documented rather than glossed over: 71.9M rows ingested behind a blocking data-quality gate with quarantine. Design decisions live as ADRs and real runs are captured verbatim — including three incidents that cost real job runs.

**[apache/spark#57608](https://github.com/apache/spark/pull/57608)** *(open)* — documents what Spark's CSV reader does when `multiLine` is left at its default and a quoted value contains a line break: the record splits silently, and because the split *adds* a row while the bad fragment is separately rejected, a row-count reconciliation can pass over corrupt data. Found while ingesting the CNPJ registry, then verified across all three parse modes before proposing any wording.

## Stack

|  |  |
|---|---|
| **Data** | PySpark · Delta Lake · Iceberg · Snowflake · SQL · Kafka · medallion / lakehouse · data contracts |
| **Orchestration** | Airflow · Azure Data Factory · dbt · Databricks Jobs & Asset Bundles |
| **Cloud & IaC** | Azure · AWS · Pulumi · Terraform · Docker · GitHub Actions |
| **Python** | FastAPI · Pytest |
| **Quality** | Great Expectations · Soda · schema-drift detection · Playwright |

## Also

Full-stack products shipped end to end on the freelance track:

- **[jorgemolina.dev](https://jorgemolina.dev)** — 3D portfolio where sections are planets in a navigable space scene, with an accessible non-3D fallback. State-machine navigation and an object-pooled render loop keep a WebGL-heavy app at ~1.6 MB of JS. ([source](https://github.com/Joorgem/portfolio))
- **[fernandafiuza.com](https://fernandafiuza.com)** — bilingual, video-first site for a movement director, entirely client-managed through a visual CMS.
- **[solto-shop.vercel.app](https://solto-shop.vercel.app)** — e-commerce storefront with a full admin back office.

## Elsewhere

[jorgemolina.dev](https://jorgemolina.dev) · [LinkedIn](https://www.linkedin.com/in/jorge-molinadavid) · contato@jorgemolina.dev
