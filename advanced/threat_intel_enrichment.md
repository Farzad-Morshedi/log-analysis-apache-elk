# Advanced Feature: Threat Intelligence Enrichment

This module adds optional threat intelligence lookups.

## 1. Logstash Threat Intel Lookup (Optional)

Use Logstash plugins:
- threatintel
- http filter

Enrich fields:
- host reputation
- known malicious IPs
- TOR exit nodes
- botnet indicators

## 2. Python Threat Intel

Integrate with:
- AbuseIPDB API
- AlienVault OTX
- GreyNoise

Workflow:
- Extract unique hosts
- Query threat intel APIs
- Add reputation scores

## 3. Kibana Visualization

Add dashboard panels:
- Malicious hosts
- Suspicious activity
- Reputation breakdown

## 4. Notes

NASA logs from 1995 contain no malicious activity.
This module is for demonstration only.
