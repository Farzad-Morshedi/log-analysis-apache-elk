# Kibana Dashboard Specifications (Step 4)

This document defines all dashboards that will be created once the ELK stack is running. These specifications allow any user to reproduce the dashboards inside Kibana.

---

## Dashboard 1 — Traffic Over Time

### Visualizations
1. **Daily Requests (Line Chart)**
   - Data view: `nasa-logs-parsed`
   - X-axis: `@timestamp` (Daily interval)
   - Y-axis: Count
   - Name: Daily Requests

2. **Hourly Requests (Line Chart)**
   - Data view: `nasa-logs-parsed`
   - X-axis: `@timestamp` (Hourly interval)
   - Y-axis: Count
   - Name: Hourly Requests

### Dashboard Composition
- Add: Daily Requests
- Add: Hourly Requests
- Dashboard name: Traffic Over Time

---

## Dashboard 2 — Status Codes

### Visualizations
1. **Status Code Distribution (Bar Chart)**
   - X-axis: Terms → `response`
   - Y-axis: Count
   - Name: Status Code Distribution

2. **Status Codes Over Time (Line Chart)**
   - X-axis: `@timestamp`
   - Split series: Terms → `response`
   - Name: Status Codes Over Time

### Dashboard Composition
- Add both visualizations
- Dashboard name: Status Codes

---

## Dashboard 3 — URL Categories

### Visualizations
1. **URL Categories (Bar Chart)**
   - X-axis: Terms → `url_category`
   - Y-axis: Count
   - Name: URL Categories

2. **URL Categories Over Time (Line Chart)**
   - X-axis: `@timestamp`
   - Split series: Terms → `url_category`
   - Name: URL Categories Over Time

### Dashboard Composition
- Add both visualizations
- Dashboard name: URL Categories

---

## Dashboard 4 — Top Hosts

### Visualizations
1. **Top Hosts (Table)**
   - Columns: `host`, Count
   - Name: Top Hosts

2. **Host Status Codes (Stacked Bar)**
   - X-axis: Terms → `host`
   - Split series: Terms → `response`
   - Name: Host Status Codes

### Dashboard Composition
- Add both visualizations
- Dashboard name: Hosts

---

## Dashboard 5 — GeoIP Map

### Visualizations
1. **GeoIP World Map**
   - Visualization type: Maps → Document Layer
   - Field: `geoip.location`
   - Metric: Count
   - Name: GeoIP World Map

### Dashboard Composition
- Add GeoIP World Map
- Dashboard name: GeoIP

---

## Import Instructions (for end users)

After running `docker-compose up`:
1. Open Kibana in your browser.
2. Navigate to **Stack Management** → **Saved Objects**.
3. Click **Import**.
4. Select the exported `kibana.ndjson` file.
5. The completed dashboards will appear under **Analytics** → **Dashboard**.
