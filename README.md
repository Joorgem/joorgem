# Jorge Molina

**Senior Data Engineer** — Databricks · PySpark · Delta Lake · Snowflake

Production data platforms: ingestion, transformation, and the reliability layer around them. Currently at CI&T; previously Globant and Mobyan (Santander Group). Around five years building pipelines other teams depend on.

**Open to Senior Data Engineer roles**, remote or hybrid — [contato@jorgemolina.dev](mailto:contato@jorgemolina.dev)

## In the open

**[open-payments-lakehouse](https://github.com/Joorgem/open-payments-lakehouse)** — a lakehouse over real, messy Brazilian government data (Receita Federal's CNPJ registry). The PySpark/Delta core is tested locally and in CI and deployed to Databricks Free Edition with its actual limits documented rather than glossed over: 144M rows in the Estabelecimentos table alone, behind a blocking data-quality gate with quarantine. Design decisions live as ADRs and real runs are captured verbatim — including the incidents that cost real job runs.

**Four open PRs in Apache Spark**, all from that ingestion. Reading the registry surfaced defects in Spark's file and CSV readers; each was reproduced and measured before any wording was proposed. Filed as SPARK-58457, SPARK-58458 and SPARK-58518.

[**#57769**](https://github.com/apache/spark/pull/57769) is the one worth reading, and it is not a documentation change. `DataSource.checkAndGlobPathIfNecessary` returned its entire input list once per path that merely *looked* like a glob, so a read with globbing disabled duplicated rows in silence — three files, five rows. `G*(G+n)+n` predicted the observed count across five configurations, which is what turns a symptom into a diagnosis. The regression test was pushed **without** the fix first and confirmed to fail on `master` — 2 failures out of 21,347 tests, both of them it — before the one-expression fix went in. Latent since 2020: every test that introduced the branch reads a single path, the one case that comes back correct.

The other three are the same corner of the CSV reader — [#57608](https://github.com/apache/spark/pull/57608) on what `multiLine=false` does to a quoted line break, [#57658](https://github.com/apache/spark/pull/57658) on two false claims about `PERMISSIVE` mode in the CSV *and* JSON docs, [#57671](https://github.com/apache/spark/pull/57671) on the missing test for the split. Reviewed by two Spark committers across two rounds; one of their corrections was checked against the parser rather than taken on trust, and it turned up a further docs defect.

**[A diagnosis rather than a patch](https://github.com/aphonsoar/Receita_Federal_do_Brasil_-_Dados_Publicos_CNPJ/issues/68)** — ten bytes across 337,716,254 lines of Receita Federal data that no Latin codepage can render as text, invisible because the `latin-1` every Python library in that ecosystem reads with maps all 256 byte values and so can never fail.

## Stack

|  |  |
|---|---|
| **Data** | PySpark · Delta Lake · Iceberg · Snowflake · SQL · Kafka · medallion / lakehouse · data contracts |
| **Orchestration** | Airflow · Azure Data Factory · dbt · Databricks Jobs & Asset Bundles |
| **Cloud & IaC** | Azure · AWS · Pulumi · Terraform · Docker · GitHub Actions |
| **Quality & observability** | Great Expectations · Soda · schema-drift detection · blocking DQ gates · quarantine with idempotent replay |
| **Python** | FastAPI · Pytest |

## Also

Full-stack products shipped end to end on the freelance track:

- **[jorgemolina.dev](https://jorgemolina.dev)** — 3D portfolio where sections are planets in a navigable space scene, with an accessible non-3D fallback. State-machine navigation and an object-pooled render loop keep a WebGL-heavy app at ~1.6 MB of JS. ([source](https://github.com/Joorgem/portfolio))
- **[fernandafiuza.com](https://fernandafiuza.com)** — bilingual, video-first site for a movement director, entirely client-managed through a visual CMS.
- **[solto-shop.vercel.app](https://solto-shop.vercel.app)** — e-commerce storefront with a full admin back office.

## Elsewhere

[jorgemolina.dev](https://jorgemolina.dev) · [LinkedIn](https://www.linkedin.com/in/jorge-molinadavid) · contato@jorgemolina.dev
