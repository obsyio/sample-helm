# Sample Helm Repository for Testing

This is a sample repository structure that demonstrates how users would organize their Helm charts with dependencies on upstream charts.

## Repository Structure

```
charts/
├── web-application/          # Example: Web app with database and cache
├── microservices-platform/   # Example: Multi-service platform
└── monitoring-stack/         # Example: Monitoring and observability
```

## Use Cases Covered

1. **web-application**: Simple app with common dependencies (PostgreSQL, Redis)
2. **microservices-platform**: Complex setup with multiple services
3. **monitoring-stack**: Observability tools (OpenTelemetry, Prometheus)

## Testing Scenarios

### Scenario 1: Detection
```bash
# System should detect all Chart.yaml files
# System should extract all dependencies
# Expected: 10+ dependencies across 3 charts
```

### Scenario 2: Update Checking
```bash
# For each dependency, check if updates are available
# Compare current version vs. latest from upstream
```

### Scenario 3: Policy Application
```bash
# postgresql: latest-1 policy → should suggest 2nd latest version
# redis: minor-only policy → should only suggest minor updates
# opentelemetry-collector: latest policy → should suggest latest
```

### Scenario 4: PR Creation
```bash
# Generate PR to update Chart.yaml with new versions
# Include release notes and changelog
```

## How to Use

1. **Connect this repo** to your CloudWave organization
2. **Run chart detection** - should find 3 charts
3. **Extract dependencies** - should find all upstream chart references
4. **Configure update policies** for each dependency
5. **Monitor for updates** - background job checks upstream releases
6. **Receive notifications** when updates are available
7. **Create PR** to update versions

## Upstream Chart Repositories

This sample uses charts from:
- Bitnami: https://charts.bitnami.com/bitnami
- OpenTelemetry: https://open-telemetry.github.io/opentelemetry-helm-charts
- Prometheus Community: https://prometheus-community.github.io/helm-charts
- Grafana: https://grafana.github.io/helm-charts
- NGINX: https://kubernetes.github.io/ingress-nginx
