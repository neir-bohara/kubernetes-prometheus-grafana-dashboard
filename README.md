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
# Kubernetes/Views/Global (ID: 15757)

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

## Kubernetes/Views/Namespaces (ID: 15758)

- Namespace view of Kubernetes cluster
- View unusual resources usage in k8s namespace
- View unusual number of resource types in k8s namespace
- Check the pods state & pods replicas
- Monitor the persistent volumes capacity of the nodes by namespace

- Namespace: CPU, RAM & Network utilization
- Real, Requests & Limits resources usage of k8s namespace
- Kubernetes resources count by type in your namespace
- Pods state, number of containers per pods & replicas availability
- Persistent volumes capacity & inodes in your namespace


![Alt text](k8s-views-namespaces.png?raw=true "k8s-views-namespaces")

## Kubernetes/Views/Nodes (ID: 15759)

- Detailed view of your Kubernetes nodes
- View unusual resources usage in k8s nodes
- Ability to find affected pods on a faulty node
- Get operating system metrics from k8s nodes

- CPU & RAM usage of nodes
- Pods count & Pods list on each node by namespace
- Detailed CPU, RAM & Network usage of k8s nodes
- System Load, Context Switches & Interrupts, File Descriptor &Time Sync
- Persistent volumes information of workloads attached to nodes
- Local node storage capacity, inodes, IOs & errors


![Alt text](k8s-views-nodes.png?raw=true "k8s-views-nodes")


