## Pre-requisites
Install [Kubernetes](https://kubernetes.io) (i.e. kops, minikube, etc)

Install [Helm](https://github.com/kubernetes/helm)

Install [Prometheus](https://github.com/kubernetes/charts/tree/master/stable/prometheus)

Install [Grafana](https://github.com/kubernetes/charts/tree/master/stable/grafana)

## Import Dashboards

* [Prometheus for system metrics](dashboards/prometheus-system_rev1.json) - Load, CPU, RAM, network, process (mod of [159](https://grafana.com/dashboards/159))
* [Nodes](dashboards/nodes_rev1.json) - Overview of the nodes utilisation (mod of [3140](https://grafana.com/dashboards/3140))
* [Kubernetes Resource CPU + Memory Requests](dashboards/resource-requests_rev1.json) - Resource requests vs allocatable in the cluster (mod of [3149](https://grafana.com/dashboards/3149))
  * [Kubernetes Resource CPU Requests](dashboards/resource-cpu-requests.json) - CPU Resource requests vs allocatable in the cluster
  * [Kubernetes Resource Memory Requests](dashboards/resource-memory-requests.json) - Memory Resource requests vs allocatable in the cluster
* [Pod Metrics](dashboards/pod_metrics.json) - Basic pod and container information

## Useful dashboards
* [Nginx Ingress Stats](https://grafana.com/dashboards/3050)
* [Kubernetes cluster monitoring (via Prometheus)](https://grafana.com/dashboards/315) - excellent dashboard that requires Kubernetes 1.7.3+ and cAdvisor to be installed

**Note: The https://prometheus-server/targets page provides health stats of your Prometheus Scrape Targets.**
