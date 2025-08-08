# devops--daily-
this is public repository for daily practice devops things
1. Grafana – The Dashboard & Visualization Layer
What it is:
Grafana is a data visualization and analytics tool.
It doesn’t store data itself (except for small settings/configuration), it connects to data sources like Loki, Prometheus, Tempo, Elasticsearch, etc.

Main role:
Show data in dashboards, charts, tables, graphs.

Key features:

Real-time monitoring dashboards

Supports many data sources

Alerts (email, Slack, etc.)

Role-based access

Example:
If Loki stores logs, Grafana can query Loki and display those logs in a searchable table.

2. Loki – The Log Aggregator
What it is:
Loki is a log database built by Grafana Labs.

Purpose:
Store, index, and query logs efficiently (optimized for cost and speed).

How it works:

Similar to Elasticsearch for logs, but cheaper and simpler.

Only indexes labels (metadata), not full log text → makes it more efficient.

Uses LogQL (Log Query Language) to search logs.

Example:
Application containers output logs → Loki collects them → Grafana shows them.

3. Tempo – The Distributed Tracing Backend
What it is:
Tempo is a tracing system (like Jaeger, Zipkin) for distributed systems.

Purpose:
Store traces — a trace shows the path a single request takes across multiple services.

Why important:
In microservices, a user request may travel through many services. Tempo helps you:

See each step

Measure time spent in each service

Identify slow or failing components

Example:
A request to buy something → hits API Gateway → goes to Product Service → Payment Service → Notification Service. Tempo records this full chain.

4. OpenTelemetry – The Data Collector & Standard
What it is:
An open-source standard & toolkit for collecting:

Metrics

Logs

Traces

Purpose:
To instrument applications and send telemetry data to backends (like Tempo, Loki, Prometheus, etc.).

How it works:

SDKs & agents you add to your application

Collects telemetry data

Sends to backend storage

Example:
You add OpenTelemetry to your Python service → It sends trace data to Tempo, logs to Loki, metrics to Prometheus.

How They Work Together
Think of it like a pipeline:

OpenTelemetry
→ Collects telemetry data (logs, metrics, traces) from your app.

Loki
→ Stores logs.

Tempo
→ Stores traces.

Grafana
→ Visualizes logs (from Loki), traces (from Tempo), and metrics (from Prometheus or others).

Quick Analogy:

OpenTelemetry – Postman who collects letters (data) from your house.

Loki – The filing cabinet for logs.

Tempo – The detective who shows the full journey of a request.

Grafana – The display board where you see all the information neatly arranged.
