# Opstree-Prometheus
A repository to learn and understand Prometheus & Grafana. In this repository we have multiple sub-folder each sub-folder focussing on one aspect of Prometheus & Grafana

## Simple
This is the first step of learning prometheus.

Setup details: In this setup we are spinning up a prometheus server that is monitoring itself.
```
  cd simple
  make run
```
File to look at:
  * prometheus.yml: Configuration file of prometheus server

URL to validate setup:
Prometheus: http://localhost:9090/

## Managing multiple nodes
Once you become comfortable with prometheus setup the next step is to monitor other nodes in the infrastructure.

Setup details: In this setup we are spinning up a prometheus server and 4 nodes that would be monitored by the prometheus server
```
  cd node-exporter
  make run-all
```
File to look at:
  * prometheus.yml: Configuration file of prometheus server specially adding specific targets.

URL to validate setup:
  - Prometheus UI: http://localhost:9090/graph
  - Prometheus targets: http://localhost:9090/targets

## Going beyond infrastructure
Prometheus is not only limited to monitoring infrastructure, prometheus supports huge number of exporters, here you will learn how we are integrating MySQL you can do it for some other application as well. For more details regarding exporters refer link below

Reference: https://prometheus.io/docs/instrumenting/exporters/

Setup details: In this setup we are spinning up a prometheus server and 1 database server that would be monitored by the prometheus server
```
  cd db
  make run-all
```
File to look at:
  * prometheus.yml: Configuration file of prometheus server specially adding specific targets.

URL to validate setup:
  - Prometheus UI: http://localhost:9090/graph
  - Prometheus targets: http://localhost:9090/targets

## Prometheus is not only about collecting data
A monitoring system becomes complete only when it has alerting in place the best thing is that prometheus has made alerting rules & alerting very loosely coupled. In this section you will learn how we are defining alerting rules not how to create alerts out of them.
Reference: https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/

Setup details: In this setup we are spinning up a prometheus server with 4 nodes and 1 database server that would be monitored by the prometheus server, along with node & database rules
```
  cd alerting
  make run-all
```
File to look at:
  * prometheus.yml: Configuration file of prometheus server.
  * db_rules.yml: Contains db rules definitions.
  * node_rules.yml: Contains node rules definitions.

URL to validate setup:
  - Prometheus UI: http://localhost:9090/graph
  - Prometheus targets: http://localhost:9090/targets
  - Prometheus Rules: http://localhost:9090/rules
  - Prometheus Alerts: http://localhost:9090/alerts

## Powerful Alertmanager
Alertmanager brings a lot of value addition especially in terms of silencing, inhibition, aggregation and sending out notifications via several methods such as email, PagerDuty and HipChat...

Reference: https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/https://prometheus.io/docs/alerting/overview/

Setup details: In this setup we are spinning up a prometheus server with 4 nodes and 1 database server that would be monitored by the prometheus server, along with node & database rules. In addition to that AlertManager is taking care of the responsibility to passing the alerts to Slack
```
  cd alertmanager
  make run-all
```
File to look at:
  * prometheus.yml: Configuration file of prometheus server.
  * db_rules.yml: Contains db rules definitions.
  * node_rules.yml: Contains node rules definitions.
  * alertmanagerconfig/config.yml: Configuration file for Alertmanager.

URL to validate setup:
  - Prometheus UI: http://localhost:9090/graph
  - Prometheus targets: http://localhost:9090/targets
  - Prometheus Rules: http://localhost:9090/rules
  - Prometheus Alerts: http://localhost:9090/alerts
  - Slack notification

## Beautiful Analytics and Monitoring
Grafana brings a powerful display of various data that you have collected using the dashboard feature.

Reference: http://docs.grafana.org/

Setup details: In this setup we are spinning up a prometheus server with 4 nodes and 1 database server that would be monitored by the prometheus server, along with node & database rules. In addition to that Grafana would be available to see various metrics
```
  cd grafana
  make run-all
```
File to look at:
  * prometheus.yml: Configuration file of prometheus server.
  * db_rules.yml: Contains db rules definitions.
  * node_rules.yml: Contains node rules definitions.
  * dashboards/*.json: Grafana Dashboards configuration files.

URL to validate setup:
  - Prometheus UI: http://localhost:9090/graph
  - Prometheus targets: http://localhost:9090/targets
  - Prometheus Rules: http://localhost:9090/rules
  - Prometheus Alerts: http://localhost:9090/alerts
  - Grafana UI : http://localhost:3000
