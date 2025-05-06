# Monitoring and Observability

## Monitoring Platforms

### Prometheus Ecosystem
- [Prometheus](https://prometheus.io/) - Time series database and monitoring system
- [Thanos](https://thanos.io/) - Highly available Prometheus setup with long-term storage
- [Cortex](https://cortexmetrics.io/) - Horizontally scalable, highly available Prometheus
- [VictoriaMetrics](https://victoriametrics.com/) - Fast, cost-effective time series database
- [Mimir](https://grafana.com/oss/mimir/) - Grafana's Prometheus-compatible metric solution

### Visualization
- [Grafana](https://grafana.com/) - Observability dashboards and visualization
- [Kibana](https://www.elastic.co/kibana/) - Analytics and visualization platform for Elasticsearch
- [Chronograf](https://www.influxdata.com/time-series-platform/chronograf/) - InfluxDB visualization

### Log Aggregation
- [Loki](https://grafana.com/oss/loki/) - Horizontally-scalable, highly-available log aggregation system
- [Elasticsearch](https://www.elastic.co/elasticsearch/) - Distributed search and analytics engine
- [Fluentd](https://www.fluentd.org/) - Open source data collector for unified logging
- [Vector](https://vector.dev/) - High-performance observability data pipeline

### Tracing
- [Jaeger](https://www.jaegertracing.io/) - End-to-end distributed tracing
- [Zipkin](https://zipkin.io/) - Distributed tracing system
- [Tempo](https://grafana.com/oss/tempo/) - High-scale, minimal-dependency distributed tracing
- [OpenTelemetry](https://opentelemetry.io/) - Observability framework and toolkit

## Prometheus Configuration

### Installation Options
- Helm charts
  ```bash
  helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
  helm install prometheus prometheus-community/prometheus
  ```
- Operator
  ```bash
  kubectl apply -f https://github.com/prometheus-operator/prometheus-operator/releases/download/v0.59.1/bundle.yaml
  ```
- Docker
  ```bash
  docker run -p 9090:9090 prom/prometheus
  ```

### Key Components
- **Prometheus Server**: Time series database and query engine
- **Alertmanager**: Handles alerts and routing
- **Pushgateway**: Allows ephemeral jobs to expose metrics
- **Exporters**: Convert metrics from various systems to Prometheus format
- **ServiceMonitor/PodMonitor**: Custom resources for service discovery

### Common Exporters
- [Node Exporter](https://github.com/prometheus/node_exporter) - Hardware and OS metrics
- [Blackbox Exporter](https://github.com/prometheus/blackbox_exporter) - Probing endpoints
- [MySQL Exporter](https://github.com/prometheus/mysqld_exporter) - MySQL server metrics
- [Redis Exporter](https://github.com/oliver006/redis_exporter) - Redis metrics
- [Nginx Exporter](https://github.com/nginxinc/nginx-prometheus-exporter) - Nginx metrics

### PromQL Examples
```promql
# CPU usage by node
sum by (instance) (rate(node_cpu_seconds_total{mode!="idle"}[5m]))

# Memory usage
node_memory_MemTotal_bytes - node_memory_MemAvailable_bytes

# HTTP request rate
sum(rate(http_requests_total[5m])) by (status_code)

# 99th percentile response time
histogram_quantile(0.99, sum(rate(http_request_duration_seconds_bucket[5m])) by (le))
```

## VictoriaMetrics

### Features
- Single-node and cluster versions
- High performance time series database
- Prometheus-compatible API
- Lower resource usage than Prometheus
- Long-term storage capabilities

### Installation
```bash
# Single-node
docker run -p 8428:8428 victoriametrics/victoria-metrics

# Kubernetes via Helm
helm repo add vm https://victoriametrics.github.io/helm-charts/
helm install victoria-metrics vm/victoria-metrics
```

### Migration from Prometheus
1. Configure Prometheus remote_write to VictoriaMetrics
   ```yaml
   remote_write:
     - url: http://victoria-metrics:8428/api/v1/write
   ```
2. Update Grafana data sources to point to VictoriaMetrics
3. Test queries to ensure compatibility

## Loki

### Overview
- Log aggregation system inspired by Prometheus
- Designed for cost-efficiency and simplicity
- Optimized for Kubernetes environments
- Uses label-based indexing instead of full-text indexing

### Installation
```bash
helm repo add grafana https://grafana.github.io/helm-charts
helm install loki grafana/loki-stack
```

### Components
- **Loki**: Backend for storing and querying logs
- **Promtail**: Agent that ships logs to Loki
- **Grafana**: Visualization for Loki logs

### LogQL Examples
```logql
# Basic log query with label filters
{app="nginx"} |= "error"

# Extract fields with regex
{app="nginx"} | regexp "status=(?P<status>\\d+)"

# Count errors by status code
sum by (status) (count_over_time({app="nginx"} | regexp "status=(?P<status>\\d+)" [5m]))
```

## Best Practices

### Alerting
- Create meaningful alert descriptions with runbooks
- Set appropriate thresholds to avoid alert fatigue
- Implement proper alerting severity levels
- Configure multiple notification channels

### Metric Naming
- Use consistent naming conventions
- Follow Prometheus naming best practices
- Include relevant labels for filtering
- Avoid high cardinality labels

### Dashboard Design
- Create hierarchy of dashboards (overview → detail)
- Use consistent visualization for similar metrics
- Include legends and documentation panels
- Design for different screen sizes

### Performance Optimization
- Use recording rules for complex queries
- Implement appropriate retention policies
- Configure proper scrape intervals
- Use federation for large-scale deployments

## References
- [Prometheus Documentation](https://prometheus.io/docs/introduction/overview/)
- [Grafana Documentation](https://grafana.com/docs/)
- [VictoriaMetrics Documentation](https://docs.victoriametrics.com/)
- [Loki Documentation](https://grafana.com/docs/loki/latest/)
- [OpenTelemetry Documentation](https://opentelemetry.io/docs/) 