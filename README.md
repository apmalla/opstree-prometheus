# Opstree-Prometheus
A repository for prometheus POC

# Prometheus Setup
To setup prometheus go to the particular directory from which you want to setup promtheus with like [alertmanager](https://github.com/ot-monitoring/opstree-prometheus/tree/abhishek/hands-on/alertmanager), [alerting](https://github.com/ot-monitoring/opstree-prometheus/tree/abhishek/hands-on/alerting), [db](https://github.com/ot-monitoring/opstree-prometheus/tree/abhishek/hands-on/db), [grafana](https://github.com/ot-monitoring/opstree-prometheus/tree/abhishek/hands-on/grafana), [node-exporter](https://github.com/ot-monitoring/opstree-prometheus/tree/abhishek/hands-on/node-exporter), [simple-prometheus](https://github.com/ot-monitoring/opstree-prometheus/tree/abhishek/hands-on/simple) and run the command which is given below:
```
make run-all
```
# Grafana
To setup [grafana](https://github.com/ot-monitoring/opstree-prometheus/tree/abhishek/hands-on/grafana) there is one thing you have to notice that some times docker could not make registry because container is not up. You can add datasource by running:-
```
make register-prometheus
```
