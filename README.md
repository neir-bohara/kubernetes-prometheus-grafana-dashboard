# kubernetes-prometheus-grafana-dashboard
![Alt text](kubernetes-grafana-dashboards-logo.png?raw=true "kubernetes-grafana-dashboards-logo")

## Installation

```terminal
kubectl create namespace monitoring

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

helm update

helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring

helm install grafana grafana/grafana --namespace monitoring
```

## Port forward prometheus for dashboard

```terminal
kubectl port-forward svc/prometheus-kube-prometheus-prometheus -n monitoring 9090:9090
```
## Get your 'admin' user password

```terminal
kubectl get secret --namespace monitoring grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
```
## Port forward grafana for dashboard

```terminal
kubectl port-forward svc/grafana -n monitoring 80:8080
```

## Grafana Dashboards and Description:
# Kubernetes / Views / Global

- Global view of your Kubernetes cluster.
- View unusual resources usage on your cluster, namespaces & nodes
- View unusual number of resource types on Kubernetes cluster
- View misconfigured applications resources (Requests & Limits VS Real)

- Sum of cluster CPU, RAM & Network utilization
- Real, Requests & Limits resources usage of the cluster
- Sum of Kubernetes cluster resources count 
- CPU, RAM & Network utilization by namespace 
- CPU, RAM & Network utilization by node

![Alt text](k8s-views-global.png?raw=true "k8s-views-global")


