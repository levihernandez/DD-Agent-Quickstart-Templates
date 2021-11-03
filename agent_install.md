# Agent Install

- [x] Obtain your API Key located in your [Datadog Account APIs](https://app.datadoghq.com/account/settings#api) section

Configure the export variables, copy and paste them into your host:

```shell
export DD_API_KEY=<your-dd-api-key>
export DD_TAGS="env:<dev|prod>","service:<service-name>","version:<version-number>","environment:<dev|prod-shipping>"
export DD_SITE="datadoghq.com"
export HOSTNAME=$(hostname -s)

DD_AGENT_MAJOR_VERSION=7 DD_API_KEY=${DD_API_KEY} DD_HOST_TAGS=${DD_TAGS} DD_HOSTNAME=${HOSTNAME} DD_SITE=${DD_SITE} bash -c "$(curl -L https://s3.amazonaws.com/dd-agent/scripts/install_script.sh)"
```


- [x] Check Agent status: `sudo datadog-agent status`
- [x] Check Integration status: `sudo datadog-agent check oracle`
- [x] Restart Agent: `sudo systemctl restart datadog-agent`
- [x] Stop Agent: `sudo systemctl stop datadog-agent`
- [x] Start Agent: `sudo systemctl start datadog-agent`
- [ ] Troubleshoot: Create a flare for Datadog Support `sudo datadog-agent flare`
