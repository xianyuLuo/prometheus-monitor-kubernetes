## 一键部署
kubectl apply -f ./prometheus-namespace.yaml

kubectl apply -f ./prometheus/prometheus-rbac.yaml

kubectl apply -f ./prometheus/prometheus-config-configmap.yaml

kubectl apply -f ./prometheus/prometheus-dep.yaml

kubectl apply -f ./prometheus/prometheus-svc.yaml

kubectl apply -f ./kube-state-metrics/kube-state-metrics-rbac.yaml

kubectl apply -f ./kube-state-metrics/kube-state-metrics-dep.yaml

kubectl apply -f ./kube-state-metrics/kube-state-metrics-svc.yaml

kubectl get -n prometheus pod

## Prometheus + Kube-state-metrics监控kubernetes集群说明

### 创建namespace
 * 创建namespace：kubectl apply -f ./prometheus-namespace.yaml

### 部署prometheus
 * 创建rbac权限：kubectl apply -f ./prometheus/prometheus-rbac.yaml
 * 创建configmap作为prometheus配置文件：kubectl apply -f ./prometheus/prometheus-config-configmap.yaml
 * 部署prometheus-dep：kubectl apply -f ./prometheus/prometheus-dep.yaml
 * 部署prometheus-svc：kubectl apply -f ./prometheus/prometheus-svc.yaml

  > 部署promethues之后，就可以采集pod、container的cpu、mem、network等指标。但是不能监控daemonset、deployment等应用的状态，如果需要监控这些，还要部署 kube-state-metrics


### 部署kube-state-metrics
 * 创建rbac权限：kubectl apply -f ./kube-state-metrics/kube-state-metrics-rbac.yaml
 * 部署kube-state-metrics-dep：kubectl apply -f ./kube-state-metrics/kube-state-metrics-dep.yaml
 * 部署kube-state-metrics-svc：kubectl apply -f ./kube-state-metrics/kube-state-metrics-svc.yaml


