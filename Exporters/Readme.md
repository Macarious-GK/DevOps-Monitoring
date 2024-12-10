# Exporters
![exporter](/Images/Node_Exporters.png)

# Table of Contents
- [Quick Overview](#quick-overview)
- [Features](#features)
- [Exporter Installation & Configuration on Linux](#node-exporter-installation-on-linux)
- [Access Exporters](#access-exporters)

## Quick Overview

- **Exporters** are tools that expose system and application metrics in a format that can be scraped by Prometheus.  
- They collect metrics from various sources, such as system resources, databases, and applications, and expose them on an HTTP endpoint.  
- Commonly used exporters include **Node Exporter**, **SQL Exporter**, and **Python Exporter**.  

## Features
- **Prometheus Compatibility**:  
  - Exposes metrics in a format that Prometheus can scrape via HTTP.  

- **Versatility**:  
  - Can collect system metrics, database performance metrics, and application-specific metrics.  

- **Wide Range of Exporters**:  
  - Exporters are available for systems, databases, applications, and more.  


## Node Exporter installation
### Linux
For detailed instructions, You can follow this guide:  
[*Node Exporter Installation on Linux (Ubuntu)*](https://medium.com/@abdullah.eid.2604/node-exporter-installation-on-linux-ubuntu-8203d033f69c)

### Python Django
``` bash
pip install django-prometheus
```
- configure the server to expose the data on end point `metrics/`

<!-- ### SQL -->
## Access Exporter
### Node Exporter
- This expose the metrics of the Linux machine on "IP:9100/metrics"


### Python Djanog Exporter
- This expose the metrics of the Djnaog Application on http://IP:8000/metrics/

<!-- ### SQL Exporter -->
