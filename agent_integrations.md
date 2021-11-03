# Agent Integrations

## Enable Integration and/or create Custom Log Collection

### Enble Apache Spark Metrics + Logs

To collect a log, it is necessary to either create a custom log collection or activate an integration log collection. For example, we want to collect logs from Apache Spark, our configuration may look like:

> file: `/etc/datadog-agent/conf.d/spark.d/conf.yaml`

```yaml
init_config:
instances:
    - spark_url: http://192.168.0.10:8080
      spark_cluster_mode: spark_driver_mode
      cluster_name: 192.168.0.10
logs:
  - type: file
    path: /var/log/spark/sparkApiTrace.log
    service: sparkApiTrace
    source: python
    log_processing_rules:
      - type: multi_line
        name: new_log_start_with_date
        pattern: \d{4}\-(0?[1-9]|1[012])\-(0?[1-9]|[12][0-9]|3[01])
  - type: file
    path: /var/log/spark/julian*.log
    service: spark
    source: spark
    log_processing_rules:
      - type: multi_line
        name: new_log_start_with_date
        pattern: \d{4}\-(0?[1-9]|1[012])\-(0?[1-9]|[12][0-9]|3[01])
```

### Create Custom Log Collection

* Create a custom directory within `sudo mkdir -p /etc/datadog-agent/conf.d`
* Create a file within the new custom dir: `sudo touch /etc/datadog-agent/conf.d/my_custom.d/conf.yaml`

> file: `/etc/datadog-agent/conf.d/my_custom.d/conf.yaml`

```yaml
logs:
  - type: file
    path: /var/log/custom/shipping*.log
    service: shipping
    source: java
    log_processing_rules:
      - type: multi_line
        name: new_log_start_with_date
        pattern: \d{4}\-(0?[1-9]|1[012])\-(0?[1-9]|[12][0-9]|3[01])
```
