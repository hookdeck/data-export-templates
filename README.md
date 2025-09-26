# Hookdeck Data Export Templates

This repository contains pre-built dashboard templates for visualizing Hookdeck metrics in popular observability platforms. These templates help you quickly set up comprehensive monitoring dashboards for your webhook infrastructure.

> 📚 For complete details about Hookdeck metrics, including available metrics and export features, see the [Hookdeck Metrics Documentation](https://hookdeck.com/docs/metrics).

## Available Templates

### Datadog Template

**File**: [`datadog/template.json`](datadog/template.json)

A comprehensive Datadog dashboard template with pre-configured panels for:

- Request metrics (total, accepted, rejected)
- Event processing (successful, failed, ignored)
- Delivery attempts and failure rates
- Queue monitoring (pending events, oldest message age)
- Performance metrics (response latency)
- Resource breakdowns (requests per source, attempts per destination)

### Prometheus/Grafana Template

**File**: [`prometheus/template.json`](prometheus/template.json)

A Grafana dashboard template designed for Prometheus data sources with panels for:

- Source request rates and statuses
- Event processing metrics
- Delivery attempt monitoring
- Queue depth by destination
- Response latency averages

## Quick Start

### Datadog Setup

1. **Enable Integration**: Follow the [Datadog export setup instructions](https://hookdeck.com/docs/metrics#exporting-to-datadog)
2. **Import Template**:
   - Download [`datadog/template.json`](datadog/template.json)
   - In Datadog, go to [Dashboards](https://app.datadoghq.com/dashboard/lists) → **New Dashboard** → **Import dashboard JSON**
   - Upload the template file

### Prometheus Setup

1. **Enable Integration**: Follow the [Prometheus export setup instructions](https://hookdeck.com/docs/metrics#exporting-to-prometheus)
2. **Configure Scraping**: Add this job to your `prometheus.yml`:
   ```yaml
   scrape_configs:
     - job_name: "hookdeck"
       scrape_interval: 30s
       metrics_path: "/metrics/prometheus"
       scheme: https
       bearer_token: "YOUR_HOOKDECK_API_KEY"
       static_configs:
         - targets: ["api.hookdeck.com"]
   ```
3. **Import Template**:
   - Download [`prometheus/template.json`](prometheus/template.json)
   - In Grafana: **Dashboards** → **New** → **Import**
   - Upload the JSON file and select your Prometheus data source

## Template Details

Both templates include the core metrics you need to monitor webhook infrastructure health:

- **Queue Monitoring**: Track pending events and backlog depth
- **Error Rates**: Monitor failed requests, events, and delivery attempts
- **Performance**: Observe response latencies and processing rates
- **Resource Usage**: View breakdowns by sources, connections, and destinations

For detailed information about each metric, see the [metrics documentation](https://hookdeck.com/docs/metrics).

## Customization

These templates serve as starting points and can be customized for your specific needs:

- **Filter by Resources**: Modify queries to focus on specific sources or destinations
- **Adjust Time Ranges**: Change aggregation periods and display windows
- **Add Alerts**: Set up notifications based on thresholds
- **Create Variables**: Add dynamic filtering capabilities

## Troubleshooting

**Data not appearing?**

- Verify the integration is enabled in your [project settings](https://dashboard.hookdeck.com/settings/project/integrations)
- Check that your API key has proper permissions
- Ensure metrics are flowing by testing the integration

**Need help?**

- 💬 Contact us via live chat in the Hookdeck dashboard
- 📧 Email us at [info@hookdeck.com](mailto:info@hookdeck.com)
- 📚 Review the [full metrics documentation](https://hookdeck.com/docs/metrics)

## Contributing

To suggest improvements or report issues with these templates, please open an issue in this repository.
