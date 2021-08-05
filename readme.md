# Prometheus monitoring #

## K8s ##
* create namespace
``` kubectl create ns monitoring ```
* Prometheus Operator
``` kubectl apply -n monitoring -f /kubernetes/prometheus-operator/ ```
* Prometheus cluster monitoring instance
``` kubectl apply -n monitoring -f /kubernetes/prometheus-cluster-monitoring/ ```
* Node-exporter(creates deamon sets)
``` kubectl apply -n monitoring -f /kubernetes/node-exporter/ ```
* Grafana port 3000
``` kubectl apply -n monitoring -f /kubernetes/grafana/ ```
* Port forward to Grafana
``` kubectl -n monitoring port-forward your-grafana-pod-name 3000 ```
* Import Grafana Dashboard Id 1860 for node-exported-all
* APIserver monitoring
``` kubectl apply -n monitoring -f /kubernetes/cluster-monitoring-api-kubelet/apiserver.servicemonitor.yaml ```
* Kubelet monitoring
``` kubectl apply -n monitoring -f /kubernetes/cluster-monitoring-api-kubelet/kubelet.servicemonitor.yaml ```
* Kube-state-metric
``` kubectl apply -n monitoring -f /kubernetes/kube-state-metrics/ ```
* Alert-manager port 9093
``` kubectl apply -n monitoring -f /kubernetes/alertmanager/ ```
* Alert Rule
``` kubectl apply -n monitoring -f /kubernetes/Prometheus-Rules/prometheus-alerts.yaml ```

## Python webapp ##
``` docker-compose build ```
``` docker-compose up ```
* Go to 
``` localhost:3000 for grafana ```
``` localhost:9090 for prometheus ```