# Prometheus
![Architecture](/Images/Prometheus_logo.png)
# Table of Contents
- [Quick Overview](#quick-overview)
- [Features](#features)
- [Architecture](#architecture)
- [Prometheus Installation & Configuration on Linux](#prometheus-linux)
- [Prometheus on Docker](#prometheus-on-docker)
- [Access Prometheus](#access-prometheus)
## Quick Overview

- `Prometheus` is an open-source monitoring and alerting tool.  
- Collects metrics, stores them in a time-series database
- Supports flexible query language (`PromQL`)  
- Integrates with Visualization tools `Grafana` for dashboards and alerting.  
- Popular in `DevOps` for system and application monitoring.  


## Features
- **Autonomous single servers, no distributed storage**:  
  - Operates independently *'Single Server'*
  - Ensuring simplicity and resilience.  
- **Pull-based time series collection over HTTP**:  
  - Fetches metrics from targets using HTTP '*/metrics*'
- **Target discovery via service discovery or static config**:  
   - Dynamically through service discovery
   - Predefined static configurations.  

## Architecture
1. ``Prometheus Server``
   - Collects and stores metrics by scraping configured targets.

2. ``Time Series Database (TSDB)`` 
   - Stores metrics in a time-series format with labels for categorization.

3. ``Exporters``
   - External services that expose metrics for Prometheus to scrape (e.g., Node Exporter).

4. ``Scraping``  
   - Prometheus periodically collects metrics from targets, with dynamic discovery.

5. ``Alertmanager``  
   - Manages alerts and sends notifications (e.g., email, Slack).

6. ``PromQL``
   - Query language for searching and manipulating metrics.

7. ``Visualization``
   - Basic UI for metrics and integration with **Grafana** for advanced visualizations.

8. ``Service Discovery``  
   - Automatically finds services to scrape in dynamic environments (e.g., Kubernetes).

![Architecture](/Images/architecture.png)

## Prometheus Linux

### Follow This Guide  

For detailed instructions, You can follow this guide:  
[*Prometheus Installation on Linux (Ubuntu)*](https://medium.com/@abdullah.eid.2604/prometheus-installation-on-linux-ubuntu-c4497e5154f6)

### Installation 
```bash
sudo wget https://github.com/prometheus/prometheus/releases/download/v2.47.0/prometheus-2.47.0.linux-amd64.tar.gz
sudo tar vxf prometheus*.tar.gz
sudo groupadd --system prometheus
sudo useradd -s /sbin/nologin --system -g prometheus prometheus
sudo mkdir /etc/prometheus
sudo mkdir /var/lib/prometheus
cd prometheus*/

#Move the Binary Files
sudo mv prometheus /usr/local/bin
sudo mv promtool /usr/local/bin
#Move other Files
sudo mv console* /etc/prometheus
sudo mv prometheus.yml /etc/prometheus

sudo chown prometheus:prometheus /usr/local/bin/prometheus
sudo chown prometheus:prometheus /usr/local/bin/promtool
sudo chown prometheus:prometheus /etc/prometheus
sudo chown -R prometheus:prometheus /etc/prometheus/consoles
sudo chown -R prometheus:prometheus /etc/prometheus/console_libraries
sudo chown -R prometheus:prometheus /var/lib/prometheus
```


### Configuration

``` bash
# You can copy the provided config or edit it

# Path to Prometheus internal config /etc/prometheus/prometheus.yml
sudo cp /Linux/prometheus.yml /etc/prometheus/prometheus.yml
# Path to Prometheus Service config /etc/systemd/system/prometheus.service
sudo cp /Linux/prometheus.service /etc/systemd/system/prometheus.service

sudo systemctl daemon-reload
sudo systemctl enable prometheus
sudo systemctl start prometheus
sudo systemctl status prometheus
```


## Prometheus on Docker

### Dockerfile Explanation

1. **Base Image**:  
   `FROM prom/prometheus:latest` uses the official Prometheus image as the base for the container.

2. **Working Directory**:  
   `WORKDIR /etc/prometheus` sets the working directory inside the container to `/etc/prometheus`.

3. **Copy Config File**:  
   `COPY prometheus.yml /etc/prometheus/prometheus.yml` copies your custom Prometheus configuration into the container.
   `COPY alert_rules.yml /etc/prometheus/alert_rules.yml` copies your alert_rules configuration into the container.

4. **Expose Port**:  
   `EXPOSE 9090` makes Prometheus' web UI accessible on port 9090.

5. **CMD**:  
   `CMD ["/bin/prometheus", "--config.file=/etc/prometheus/prometheus.yml"]` runs Prometheus with the specified configuration file.

This Dockerfile sets up Prometheus with your custom settings and exposes the UI on port 9090.

### Build image & Run Container
``` bash
docker build -t custom-prometheus .
docker run -d -p 9090:9090 --name prometheus myprometheuscontainer
```

## Access Prometheus

- You can access the Prometheus Dashboard at <mark>Machine-IP:9090</mark>
