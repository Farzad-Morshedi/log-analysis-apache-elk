# 🚀 NASA Web Log Analysis Project

A complete, reproducible ELK + Python log analysis pipeline using the NASA Kennedy Space Center HTTP logs (1995).

This project demonstrates:

* Real log ingestion

* Real parsing

* Real indexing

* Real dashboards

* Real analytics

* Real anomaly detection

* Real reproducibility via Docker

It is designed as a portfolio‑ready SOC / DevOps / Data Engineering project.

## 📦 Project Architecture

```
┌──────────────┐
│  apache log  │
│ nasa_access  │
└───────┬──────┘
        │ Filebeat
        ▼
┌──────────────┐
│   Logstash   │
│ Grok Parser  │
└───────┬──────┘
        │
        ▼
┌──────────────┐
│Elasticsearch │
│   Indexing   │
└───────┬──────┘
        │
        ▼
┌──────────────┐
│    Kibana    │
│  Dashboards  │
└──────────────┘

```

## 📁 Repository Structure

log-analysis-project/
├── data/
│   └── apache_access.log
├── filebeat/
│   └── filebeat.yml
├── logstash/
│   └── pipeline.conf
├── elasticsearch/
│   └── index_template.json
├── analytics/
│   └── analysis.ipynb
├── dashboards/
│   ├── kibana.ndjson
│   └── DASHBOARD_SPECIFICATIONS.md
└── docker-compose.yml

## 🐳 Running the Full ELK Stack

1. Clone the repository:
   git clone https://github.com//log-analysis-project.git
   cd log-analysis-project

2. Start the ELK stack:
   docker-compose up

This launches:

* Elasticsearch

* Kibana

* Logstash

* Filebeat

Filebeat immediately begins shipping the NASA log file into Logstash.

## 🔧 Logstash Pipeline Overview

The Logstash pipeline:

* Parses Apache logs using GROK expressions designed for standard Common Log Format entries.

* Extracts essential metadata fields:

  * host

  * method

  * url

  * url_category

  * response

  * bytes

  * @timestamp

* Enriches network entries with GeoIP data to track client provenance.

* Outputs structured documents into the Elasticsearch index: nasa-logs

Refer to the logstash/pipeline.conf configuration file for complete field mapping definitions and conditional filters.

## 📊 Kibana Dashboards

Dashboards included:

1. Traffic Over Time

   * Daily requests aggregation

   * Hourly requests tracking

2. Status Codes

   * Distribution charts

   * Time series progression

3. URL Categories

   * Category distribution metrics

   * Category time series tracking

4. Hosts

   * Top client hosts ranking

   * Host to status code mapping

5. GeoIP

   * Comprehensive world map of traffic origins

Dashboard specifications are thoroughly documented in dashboards/DASHBOARD_SPECIFICATIONS.md.

The actual dashboards are imported via:
Kibana -> Stack Management -> Saved Objects -> Import -> kibana.ndjson

## 📈 Python Analytics (analysis.ipynb)

The Jupyter notebook performs:

* Top hosts statistical evaluation

* Top URLs tracking and popularity ranking

* URL category breakdown analyses

* Status code error evaluation

* Daily and hourly traffic trend computations

* Anomaly detection algorithms and threshold identification

* Bandwidth utilization and byte-size distribution analysis

* Host to URL correlation modeling

* Host to status code correlation mapping

* Time to URL mapping workflows

* Time to status code mapping calculations

This notebook mirrors the Kibana dashboards while providing deeper statistical depth and advanced exploratory data science routines using Pandas, NumPy, and Matplotlib libraries.

## 🔥 Anomaly Detection Summary

The historical NASA logs contain three major operational anomalies:

1. Mid‑July rise: Normal organic traffic growth reflecting early internet adoption.

2. Mid‑August spike: Real user activity surge driven by high-profile NASA space mission events.

3. Late‑August collapse: A significant server logging outage and missing data period.

These anomalies are clearly observable across daily and hourly traffic metrics, status code fluctuations, url categories, host activity patterns, and overall network bandwidth consumption.

## 🌍 GeoIP Insights

The historical dataset reveals telemetry originating from diverse network sectors across the globe:

* Early commercial internet service providers such as AOL and Prodigy

* Leading technology corporations including Motorola and Texas Instruments

* Internal NASA infrastructure nodes and research laboratories

* International academic networks and government institutions

GeoIP mapping illustrates worldwide engagement with space exploration initiatives during the mid-1990s.

## 🛠 Future Improvements

* Threat intelligence feed enrichment pipelines for enhanced security context

* User-agent string classification modules for device and browser tracking

* Machine learning-based anomaly detection models for automated threat hunting

* Automated ELK alerting rules for real-time notification events

* Grafana dashboard integration alternatives for multi-platform telemetry

* Kafka stream ingestion architecture for high-throughput scalability

* Cloud deployment configurations targeting Elastic Cloud and AWS OpenSearch services

## 📜 License

This project utilizes public domain NASA server log data. All custom configuration files, automation scripts, and analytical notebooks in this repository are released under the terms of the MIT License.

## 🎯 Final Notes

This repository is engineered to be fully reproducible across modern containerized environments:

1. Clone the repository to your local machine

2. Execute docker-compose up to initialize the stack

3. Import saved dashboard objects into Kibana

4. Explore ingested log telemetry through pre-built visualizations

5. Execute the analytics notebook for deep-dive statistical research

It serves as a professional portfolio showcase for security operations center (SOC) analysts, DevOps engineers, and data engineering professionals looking to demonstrate full-stack telemetry capabilities.
