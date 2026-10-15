# Advanced Feature: Anomaly Detection

This module adds anomaly detection to the NASA log dataset using both
Python analytics and ELK stack capabilities.

## 1. Python-Based Anomaly Detection

### Daily Traffic Z-Score Method
- Compute mean and standard deviation of daily request counts.
- Flag days where:
  Z = (value - mean) / std  > 3

### Status Code Spike Detection
- Track 404 and 501 spikes.
- Identify abnormal error bursts.

### URL Category Volatility
- Compute rolling variance for each category.
- Flag sudden changes in:
  - shuttle
  - images
  - history
  - whats-new.html

### Host Behavior Anomalies
- Detect hosts with:
  - abnormal request volume
  - abnormal error rates
  - abnormal URL access patterns

## 2. ELK-Based Anomaly Detection

### Kibana Machine Learning (Optional)
If the user enables ML in Elastic:
- Create a job on index `nasa-logs`
- Detector: count
- Influencers: host, url_category, response

### Watcher Alerts (Optional)
Create alerts for:
- High 404 rates
- High 501 rates
- Sudden traffic drops
- Sudden traffic spikes

## 3. Known Anomalies in NASA Logs

- Mid-July rise (normal)
- Mid-August spike (real user activity)
- Late-August collapse (logging outage)
