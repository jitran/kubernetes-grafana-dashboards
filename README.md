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
  * Update Prometheus helm chart values.yaml:
    * Set `controller.stats.enabled: true` in your Prometheus helm chart
    * Add the following to `controller.service.annotation`:
      ```
      prometheus.io/port: '10254'
      prometheus.io/scrape: 'true'
      ```
    * Upgrade Prometheus release with the new values
  * Update Grafana helm chart values.yaml:
    * Add grafana-worldmap-panel to `server.installPlugins`
    * Upgrade Grafana release with the new values
  * Download the json file, replace `[1m]` with `[5m]`, and import the updated json file
* [Kubernetes Cluster Monitoring (via Prometheus)](https://grafana.com/dashboards/315) - excellent dashboard that requires Kubernetes 1.7.3+ and cAdvisor to be installed
  * Update Prometheus helm chart values.yaml:
    * Update the `scrape_configs` per the dashboard instructions
    * Upgrade Prometheus release with the new values
  * Download the json file, replace `^/dev/[sv]da9$` with `^/dev/.*$`, and import the updated json file
* [Kubernetes Deployment Metrics](https://grafana.com/dashboards/741) - requires Kubernetes 1.7.3+ and cAdvisor to be installed


**Note: The https://prometheus-server/targets page provides health stats of your Prometheus Scrape Targets. Additional scrape_configs settings are available [here](https://github.com/prometheus/prometheus/blob/master/documentation/examples/prometheus-kubernetes.yml)**
