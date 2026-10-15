# Advanced Feature: GeoIP Analysis

This module expands GeoIP insights beyond basic Kibana dashboards.

## 1. Python GeoIP Heatmap

Using the geoip.location field:
- Convert to latitude/longitude pairs
- Plot using:
  - Folium
  - Basemap
  - Plotly scatter_geo

## 2. Country-Level Aggregation

Group by:
- geoip.country_name
- geoip.continent_name

Compute:
- Total requests
- Error rates
- Top URLs per country

## 3. ISP / Organization Insights

Using hostnames:
- Identify AOL, Prodigy, Motorola, TI, NASA internal
- Map traffic by organization

## 4. Kibana Maps Enhancements

Add layers:
- Country boundaries
- Heat intensity
- Host density
