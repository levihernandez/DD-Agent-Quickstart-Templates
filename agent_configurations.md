# Agent Configurations

Current templates are based on the version `Agent (v7.31.1)`. Newer versions may bring newer features not covered in the examples below:

## Enable: Logs

Activate log collection. 

> file: `/etc/datadog-agent/datadog.yaml`

```yaml
api_key: <your-dd-api-key
tags: ["env:prod","service:shipping","version:0.0.1","environment:prod-shipping"]
env: prod
logs_enabled: true
```



## Enable: Logs, APM

## Enable: Logs, APM, Live Process

## Enable: Logs, APM, Live Process, NPM

## Enable: Logs, APM, Live Process, NPM, Security
