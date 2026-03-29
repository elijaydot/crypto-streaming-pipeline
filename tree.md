crypto-streaming-pipeline/
│
├── .cassandraWorkbench/           ← local Cassandra extension workspace data
├── .cassandraWorkbench.jsonc      ← Cassandra extension settings
├── .env                           ← environment variables for local stack
├── .gitignore                     ← root ignore rules for local/dev artifacts
├── crypto-streaming-pipeline.code-workspace
├── docker-compose.yaml            ← multi-service local pipeline orchestration
├── image.png                      ← architecture / project screenshot
├── README.md                      ← setup and project overview
├── tree.md                        ← annotated repository structure
│
├── cassandra/
│   ├── config/                    ← reserved for Cassandra config overrides
│   └── init/
│       └── schema.cql             ← keyspace and table bootstrap script
│
├── duckdb/
│   └── data/
│       ├── crypto_history.duckdb  ← persisted DuckDB database file
│       └── crypto_history.duckdb.wal
│                                  ← DuckDB write-ahead log
│
├── flink/
│   ├── .dockerignore
│   ├── Dockerfile                 ← custom PyFlink image
│   ├── requirements.txt           ← Python dependencies for Flink job image
│   ├── conf/
│   │   └── flink-conf.yaml        ← Flink runtime and Prometheus reporter config
│   └── jobs/
│       ├── .gitkeep               ← keeps jobs directory tracked
│       ├── crypto_job.py          ← main streaming pipeline job
│       ├── sinks.py               ← output writers for downstream storage
│       └── transformations.py     ← stream cleaning and enrichment logic
│
├── grafana/
│   ├── config/
│   │   └── grafana.ini            ← Grafana server configuration
│   └── provisioning/
│       ├── dashboards/
│       │   ├── crypto.json        ← provisioned crypto monitoring dashboard
│       │   └── dashboard.yml      ← dashboard provisioning manifest
│       └── datasources/
│           └── prometheus.yml     ← Prometheus datasource provisioning
│
├── kestra/
│   ├── config/                    ← reserved for Kestra config files
│   └── flows/
│       ├── flink_job_flow.yml     ← submit / manage the Flink job
│       └── producer_flow.yml      ← run or schedule the producer workflow
│
├── producer/
│   ├── .dockerignore
│   ├── Dockerfile                 ← producer container image
│   ├── fetcher.py                 ← fetches crypto market data
│   ├── main.py                    ← producer service entry point
│   ├── producer.py                ← Redpanda publishing logic
│   ├── requirements.txt           ← producer Python dependencies
│   └── schemas.py                 ← message / payload schema definitions
│
└── prometheus/
    └── config/
        └── prometheus.yml         ← scrape targets and metrics collection config


