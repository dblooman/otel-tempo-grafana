# OTEL Tempo Grafana Stack

This repository provides a simple setup for a tracing and monitoring stack using Grafana, Prometheus, Tempo, and the OpenTelemetry Collector. It uses Docker Compose to run all services together.

## Services Overview

- **Tempo**: A distributed tracing backend, configured in [grafana/tempo.yaml](grafana/tempo.yaml).

  - Listens on port `3200` for Tempo queries.
  - Also exposes ports for Jaeger, OTLP, etc.

- **Prometheus**: Time series database for monitoring metrics.

  - Configured in [grafana/prometheus.yaml](grafana/prometheus.yaml) to scrape targets including Tempo itself.
  - Exposes its UI on port `9090`.

- **Grafana**: Dashboarding solution for visualizing metrics and traces.

  - Uses [grafana/grafana-datasources.yaml](grafana/grafana-datasources.yaml) to provision data sources for Prometheus and Tempo.
  - Available on port `3000`.
  - Anonymous access is enabled with Admin role.

- **OpenTelemetry Collector**: Collects telemetry data and exports them to Tempo and Prometheus.
  - Configured in [grafana/otel-collector-config.yaml](grafana/otel-collector-config.yaml).

## Getting Started

1. **Clone the Repository**

   ```sh
   git clone <repository_url>
   cd otel-tempo-grafana
   ```

2. **Start the Services**

   ```sh
    docker-compose up -d
   ```

3. **Access the Services**
   - Grafana: [http://localhost:3000](http://localhost:3000)
     - Username: `admin`
     - Password: `admin`
   - Prometheus: [http://localhost:9090](http://localhost:9090)
   - Tempo: [http://localhost:3200](http://localhost:3200)
