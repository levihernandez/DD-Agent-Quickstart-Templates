# Agent Configurations

Current templates are based on the version `Agent (v7.31.1)`. Newer versions may bring newer features not covered in the examples below:

## Enable: Logs

Activate log collection. 

> file: `/etc/datadog-agent/datadog.yaml`

```yaml
api_key: <your-dd-api-key
tags: ["env:prod","service:shipping","version:0.0.1","environment:prod-shipping"]
env: prod
# enable log collection
logs_enabled: true
```

**NOTE:** to enable integration logs or create a custom log collection see [Agent Integrations](agent_integrations.md)


## Enable: Logs, APM

Activate Log collection & APM tracing

> file: `/etc/datadog-agent/datadog.yaml`

```yaml
api_key: <your-dd-api-key
tags: ["env:prod","service:shipping","version:0.0.1","environment:prod-shipping"]
env: prod
# enable log collection
logs_enabled: true
# enable APM tracing
apm_config:
  enabled: true
```

## Enable: Logs, APM, Live Process

Activate Log collection, APM tracing, Live Process

> file: `/etc/datadog-agent/datadog.yaml`

```yaml
api_key: <your-dd-api-key
tags: ["env:prod","service:shipping","version:0.0.1","environment:prod-shipping"]
env: prod
# enable log collection
logs_enabled: true
# enable APM tracing
apm_config:
  enabled: true
# enable Live Process collection
process_config:
  enabled: "true"
```

## Enable: Logs, APM, Live Process, NPM

Activate Log collection, Application Performance Monitor tracing, Live Process, Network Performance Monitor

> file: `/etc/datadog-agent/datadog.yaml`

```yaml
api_key: <your-dd-api-key
tags: ["env:prod","service:shipping","version:0.0.1","environment:prod-shipping"]
env: prod
# enable log collection
logs_enabled: true
# enable APM tracing
apm_config:
  enabled: true
# enable Live Process collection
process_config:
  enabled: "true"
```



## Enable: Logs, APM, Live Process, NPM, Security
