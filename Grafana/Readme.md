# Grafana
![Architecture](/Images/Grafana_logo.png)

# Table of Contents
- [Quick Overview](#quick-overview)
- [Features](#features)
- [Grafana Installation & Configuration on Linux](#grafana-linux)
- [Grafana on Docker](#grafana-on-docker)
- [Access Grafana](#access-grafana)

## Quick Overview

- `Grafana` is an open-source analytics and monitoring platform.  
- Visualizes metrics, logs, and traces with customizable dashboards.  
- Supports various data sources like `Prometheus`, `Elasticsearch`, and more.  
- Widely used in `DevOps` for centralized monitoring and alerting.

## Features
- **Powerful Visualization Options**:  
  - Interactive and customizable dashboards.  
  - Supports graphs, tables, heatmaps, and more.  

- **Multiple Data Source Integration**:  
  - Connects to Prometheus, InfluxDB, Elasticsearch, MySQL, etc.  

- **Alerting System**:  
  - Set alerts based on query thresholds.  
  - Receive notifications via email, Slack, or other integrations.  

- **User Management & Sharing**:  
  - Secure user authentication and role-based access.  
  - Easily share dashboards and reports.


- Dashboards pull data using flexible query languages like `PromQL` (Prometheus).

## Grafana Installation & Configuration on Linux
- Follow the official [Grafana Installation Guide](https://grafana.com/docs/grafana/latest/installation/).

### Grafana installation
```bash
# Install needed packages
sudo apt-get install -y apt-transport-https software-properties-common wget
# Import the GPG key:
sudo mkdir -p /etc/apt/keyrings/
wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null
# To add a repository for stable releases, run the following command:
echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
# Updates the list of available packages and up the service
sudo apt-get update
sudo apt-get install grafana
sudo systemctl daemon-reload
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
sudo systemctl status grafana-server
```


## Grafana on Docker
- Use the following command to run Grafana in Docker:  
```bash
docker build -t custom-grafana .
docker run -d -p 3000:3000 --name=grafana custom-grafana
```


## Access Grafana
- This expose the Grafana Dashboard "IP:3000"
- Default Username: admin
- Default Password: admin


