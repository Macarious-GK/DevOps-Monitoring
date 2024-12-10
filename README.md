
# DevOps Monitoring with Grafana, Prometheus, and Exporters

This project sets up a monitoring solution using **Grafana**, **Prometheus**, and **exporters** to monitor your systems, services, and applications.

![Monitoring](/Images/devops_monitoring.png)

## Monitoring  Overview
### In a monitoring system, there are three key components:

**`The System Being Monitored`**: 
- This refers to the application or infrastructure that needs to be monitored. It must expose its metrics through a dedicated endpoint (/metrics/) and make them accessible via a specific port. These metrics provide valuable insights into the system's performance and health.

**`The Monitoring Tool`**: 
- This tool acts as the central data collection point, pulling metrics from various exporters. Exporters are lightweight services that retrieve system or application metrics. The monitoring tool aggregates and stores this data, making it available for querying. Additionally, it allows users to define thresholds or values for setting up alerts based on these metrics.

**`The Visualization Tool`**: 
- This component is responsible for presenting the collected data in an understandable and actionable format. Using customizable dashboards, it visualizes the metrics collected by the monitoring tool, helping users to analyze trends, monitor system health, and take informed actions when necessary.
## Tools

- **`Prometheus`**: An open-source monitoring and alerting toolkit designed for reliability and scalability.
- **`Grafana`**: A platform for monitoring and observability, used to visualize metrics collected by Prometheus.
- **`Exporters`**: Tools that expose system and application metrics to Prometheus for monitoring.

## Repo Folder System

```cmd
DevOps-Monitoring/
├── Images/
|── Prometheus/
├   ├── Docker/
|   |── K8s/
|   └── Readme.md
|── Grafana/
|   ├── Docker/
|   |   └── dashboards/
|   |── K8s/
|   └── Readme.md
└── Readme.md
```







<!-- [Heading IDs](#heading-ids)

| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |

| Syntax | Description |
| --- | ---- |
| Header | Title |
| Paragraph | Text |
 -->
<!-- 
```cmd
DevOps-Monitoring/
├── Images/
|── Prometheus/
├   ├── Docker/
|   │   └── dashboards.yaml
|   |── K8s/
|   |   └── datasources.yaml
|   └── Linux/
|       |── prometheus.service
|       └── prometheus.yml   
└── Grafana/
    ├── Docker/
    │   └── dashboards.yaml
    └── K8s/
        └── datasources.yaml
``` -->
