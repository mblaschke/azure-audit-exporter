Azure Audit Exporter
====================

[![license](https://img.shields.io/github/license/webdevops/azure-audit-exporter.svg)](https://github.com/webdevops/azure-audit-exporter/blob/master/LICENSE)
[![Docker](https://img.shields.io/badge/docker-webdevops%2Fazure--audit--exporter-blue.svg?longCache=true&style=flat&logo=docker)](https://hub.docker.com/r/webdevops/azure-audit-exporter/)
[![Docker Build Status](https://img.shields.io/docker/build/webdevops/azure-audit-exporter.svg)](https://hub.docker.com/r/webdevops/azure-audit-exporter/)

Prometheus exporter for Azure Audit informations.

Configuration
-------------

Normally no configuration is needed but can be customized using environment variables.

| Environment variable              | DefaultValue                | Description                                                       |
|-----------------------------------|-----------------------------|-------------------------------------------------------------------|
| `AZURE_SUBSCRIPTION_ID`           | `empty`                     | Azure Subscription IDs (empty for auto lookup)                    |
| `AZURE_LOCATION`                  | `westeurope`, `northeurope` | Azure location for usage statitics                                |
| `SCRAPE_TIME`                     | `5m`                        | Time (time.Duration) between Azure API collections                |
| `SERVER_BIND`                     | `:8080`                     | IP/Port binding                                                   |
| `COLLECT_SUBSCRIPTION`            | `false`                     | Collect `azureaudit_subscription_info` (if azure_resourcemanager_exporter is not used) |
| `COLLECT_RESOURCEGROUP`           | `false`                     | Collect `azureaudit_resourcegroup_info` (if azure_resourcemanager_exporter is not used) |

for Azure API authentication (using ENV vars) see https://github.com/Azure/azure-sdk-for-go#authentication

Metrics
-------

| Metric                                  | Description                                                                               |
|-----------------------------------------|-------------------------------------------------------------------------------------------|
| `azurerm_subscription_info`             | Azure Subscription details (ID, name, ...; disabled by default)                           |
| `azurerm_resourcegroup_info`            | Azure ResourceGroup details (subscriptionID, name, various tags ...; disabled by default) |
| `azurerm_securitycenter_compliance`     | Azure SecurityCenter compliance status                                                    |
| `azurerm_advisor_recommendation`        | Azure Adisor recommendations (eg. security findings)                                      |

