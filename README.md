# Log Analysis Project — Apache Access Logs with ELK + Python

This project demonstrates a complete, end‑to‑end log analysis workflow using an open‑source stack. It ingests Apache access logs, parses them, stores them, analyzes them, and visualizes insights using Elasticsearch, Logstash, Kibana, and Python.

The goal is to show how real operational logs can be transformed into meaningful analytics and dashboards using a reproducible, containerized pipeline designed for efficiency and clarity.

---

## 1. Project Architecture

This project uses the classic ELK pipeline architecture:
```text
    Filebeat → Logstash → Elasticsearch → Kibana
                         ↓
                       Python
```

* **Filebeat**: Ships raw log data efficiently into Logstash.
* **Logstash**: Parses the CSV fields, converts data types, enriches IP addresses with GeoIP data, and sends structured documents into Elasticsearch.
* **Elasticsearch**: Stores the parsed logs and provides a powerful, scalable search and aggregation engine.
* **Kibana**: Visualizes the logs using interactive dashboards, charts, and geographical maps.
* **Python (Pandas + Matplotlib)**: Performs deeper offline analytics such as traffic patterns, error rate analysis, top endpoints, GeoIP distribution, and bandwidth usage statistics.

---

## 2. Dataset

This project uses the NASA Kennedy Space Center HTTP Logs, a well‑known public dataset frequently used in log‑analysis research, anomaly detection, and server traffic studies.

### Dataset Source
The dataset is publicly available on Kaggle:
> [NASA HTTP Access Logs on Kaggle](https://www.kaggle.com/datasets/<your-dataset-link>)

### Why the dataset is not stored in this repository
The full dataset is approximately 31 MB, which exceeds standard GitHub file upload limits without auxiliary tools. Instead of storing the full file directly, this repository provides:
* A direct link to download the full dataset
* An optional sample file for quick local testing and pipeline verification
* A fully containerized pipeline that functions seamlessly with either the sample or full dataset

This design choice keeps the repository lightweight, performant, and completely avoids the complexity of Git LFS.

---

## 3. Repository Structure
```txt
    log-analysis-apache-elk/
    ├── data/
    │   └── sample_apache_logs.csv        # optional small sample dataset
    ├── filebeat/
    │   └── filebeat.yml                  # configuration for shipping logs to Logstash
    ├── logstash/
    │   └── pipeline.conf                 # CSV parsing and GeoIP filter rules
    ├── elasticsearch/
    │   └── index_template.json           # explicit field mappings and index settings
    ├── analytics/
    │   └── analysis.ipynb                # comprehensive Python Jupyter notebook
    ├── dashboards/
    │   └── kibana.ndjson                 # pre-built exported Kibana dashboards
    ├── docker-compose.yml                # orchestration for the full ELK stack
    └── README.md                         # project documentation
```

Each dedicated folder encapsulates one specific component of the modular pipeline, making the overall project exceptionally easy to navigate, maintain, and reproduce across different environments.

---

## 4. CSV Log Format

The dataset utilized in this project follows a clean comma-separated structure containing the following core attributes:

    host,time,method,url,response,bytes

### Field Meanings and Descriptions
* **host** — The client IP address initiating the HTTP request.
* **time** — The exact timestamp marking when the request was received.
* **method** — The HTTP request method utilized (e.g., GET, POST, PUT, DELETE).
* **url** — The specific requested resource path on the server.
* **response** — The HTTP status code returned by the server (e.g., 200, 404, 500).
* **bytes** — The total size of the server response payload measured in bytes.

These essential fields provide sufficient data granularity for comprehensive traffic analysis, error tracking, endpoint popularity ranking, GeoIP mapping, bandwidth monitoring, and security‑oriented investigations such as identifying scanning behavior or sudden status code spikes.

---

## 5. How to Run the ELK Stack

### Prerequisites
* Docker engine installed and running
* Docker Compose utility
* The dataset downloaded from Kaggle

### Execution Steps
1. Place the acquired dataset file into the `data/` directory.
2. Initialize and start the complete ELK stack containers:
   `docker-compose up`
3. Access the Kibana web interface in your browser:
   `http://localhost:5601`
4. Import the pre-configured dashboards from the `dashboards/kibana.ndjson` file.
5. Launch and execute the Python notebook located in `analytics/analysis.ipynb` for advanced statistical evaluation.

---

## 6. Python Analytics

The accompanying Python Jupyter notebook extends the telemetry capabilities by performing:
* Advanced time‑series traffic analysis over custom windows
* Comprehensive status code distribution breakdowns
* Identification of top requested URLs and high-frequency client IPs
* Statistical bandwidth and bytes distribution evaluations
* Integrated GeoIP visualization maps
* Error clustering and endpoint popularity rankings

This offline analysis layer complements Kibana perfectly by providing flexible custom visualizations, data science libraries, and rigorous statistical metrics.

---

## 7. Future Improvements

* Implement advanced user‑agent string parsing for device and browser analytics
* Integrate HTTP referrer header analysis to track traffic origin pathways
* Build automated anomaly detection rules for traffic spikes and malicious scanning patterns
* Incorporate machine‑learning models for automated traffic classification
* Introduce a secondary dataset such as SANS anonymized web logs for cross-comparison
* Develop comparative dashboards to analyze behavioral shifts across different log corpuses

---

## 8. License

This project leverages public domain log data and industry-standard open‑source tools. All original configuration files and custom scripts in this repository are released under the terms of the MIT License.
