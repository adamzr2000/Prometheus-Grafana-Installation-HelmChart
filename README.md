# How to install Prometheus and Grafana with Helm Chart
This repo explains how to install [Prometheus](https://prometheus.io/) and [Grafana](https://grafana.com/grafana/dashboards/10856-k8-cluster/) , using Helm, for monitoring your Kubernetes cluster.

## Installation
1. Add the repository to Helm:
```
helm repo add prom-repo https://prometheus-community.github.io/helm-charts
```
```
helm repo update
```
2. Install the chart setting a custom *values.yaml* file to expose the service outside your cluster:
```
helm install monitoring prom-repo/kube-prometheus-stack -n monitoring --create-namespace --values=values.yaml
```
- Uninstall the chart:
```
helm uninstall monitoring -n monitoring
```


## Access
```
kubectl get svc -n monitoring -o wide
```
ManagerNodeIpAddress:GrafanaServiceNodePort


## Other options
- Default installation:
```
helm install monitoring prom-repo/kube-prometheus-stack
```
- Save the default values of the chart in a yaml file:
```
helm show values prom-repo/kube-prometheus-stack > values.yaml
```
- Upgrade the chart:
```
helm upgrade monitoring prom-repo/kube-prometheus-stack --values=values.yaml
```
- Set custom parameters manually:
```
helm install monitoring prom-repo/kube-prometheus-stack -n monitoring --create-namespace --set grafana.adminPassword=admin --set grafana.service.type="NodePort" --set grafana.service.nodePort=30001
```
