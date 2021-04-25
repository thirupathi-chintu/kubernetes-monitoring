# kubernetes-monitoring

kubectl create ns monitoring



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


kubectl expose deploy kibana --type=NodePort --name=kibana1 -n logging