# DD-Agent-Quickstart-Templates
Datadog Agent Quickstart Templates 

The Datadog uses a single to collect monitoring data from a host 

## Step1: [Agent Installer](agent_install.md)
- [x] Configure Agent export environment variables
- [x] Customize the Datadog installer command
- [x] Run the command
- [x] enables Infrastructure metrics collection [15 sec interval, can be adjusted]


## Step2: [Agent Configurations](agent_configurations.md)
- [x] enable Log collection [real time]
- [x] enable APM tracing [real time, ]
- [x] enable Live Process collection
- [x] enable NPM collection
- [x] enable Security detection


## Step3: [Agent Integrations](agent_integrations.md) [Optional]
- [x] enable Spark integration and Spark log collection
- [x] create custom log collection
- [ ] create custom JMX collection

## Step4: [Agent Custom Checks](agent_custom_checks.md) [Optional]
- [ ] custom check - http status code check

## Step5: [Application Tracing Configuration](application_tracing_configuration.md), JAVA example.

Supported: Java, Python, Ruby, C++, Go, NodeJS, .NET Framework, .NET Core, PHP

> Java APM example:

- [x] download Datadog agent library
- [x] enable Profiler: Java, Python, Go, Ruby
- [x] enable log injection
- [x] enable tracing sampling rate
- [ ] customize tags
