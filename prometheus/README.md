# kubernetes prometheus Setup

Complete prometheus monitoring stack setup on Kubernetes.

You can find the full tutorial from here https://devopscube.com/setup-prometheus-monitoring-on-kubernetes/

Idea of this repo to understand all the components involved in prometheus setup.


Required packages to complete:
alertmanager
exporters
grafana
prometheus
prometheus-operator
kube-state-metrics
prometheus-node-exporter


CRDs created by this chart are not removed by default and should be manually cleaned up:

kubectl delete crd prometheuses.monitoring.coreos.com
kubectl delete crd prometheusrules.monitoring.coreos.com
kubectl delete crd servicemonitors.monitoring.coreos.com
kubectl delete crd podmonitors.monitoring.coreos.com
kubectl delete crd alertmanagers.monitoring.coreos.com
kubectl delete crd thanosrulers.monitoring.coreos.com



Get Repo Info:

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

Install Chart
# Helm

helm install prometheus prometheus-community/kube-prometheus-stack



kubectl expose deploy prometheus-grafana --type=LoadBalancer --name=prometheus-grafana1 -n monitoring

kubectl expose deploy prometheus-grafana --type=NodePort --name=prometheus-grafana1 -n monitoring

kubectl -n monitoring get secret prometheus-grafana -o jsonpath='{.data.admin-password}' | base64 --decode

kubectl -n monitoring get secret prometheus-grafana -o jsonpath='{.data.admin-user}' | base64 --decode

