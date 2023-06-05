# How to install Prometheus and Grafana with Helm Chart
This repo explains how to install [Prometheus](https://prometheus.io/) and [Grafana](https://grafana.com/grafana/dashboards/10856-k8-cluster/) , using Helm, for monitoring your Kubernetes cluster.

## Installation
1. Add the repository to Helm
```
helm repo add prom-repo https://prometheus-community.github.io/helm-charts
```
```
helm repo update
```
2. Install the chart setting a custom *values.yaml* file to expose the service of Grafana DashBoard outside your cluster:
```
helm install monitoring prom-repo/kube-prometheus-stack --values=values.yaml
```

## Access
http://IP-address-of-your-manager-node:30001

## Other options
```
helm install monitoring prom-repo/kube-prometheus-stack
```
```
helm show values prom-repo/kube-prometheus-stack > values.yaml
```
```
helm upgrade monitoring prom-repo/kube-prometheus-stack --values=values.yaml
```
