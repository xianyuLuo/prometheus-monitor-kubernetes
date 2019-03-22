## Prometheus + Kube-state-metrics监控kubernetes集群说明

### 创建namespace
    创建namespace：kubectl apply -f ./prometheus-namespace.yaml

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


### 详情架构

   [http://xianyuluo.com/post/prometheus%E7%9B%91%E6%8E%A7k8s%E4%B8%80%E7%9B%91%E6%8E%A7%E6%A1%86%E6%9E%B6%E8%B0%83%E7%A0%94/](http://xianyuluo.com/post/prometheus%E7%9B%91%E6%8E%A7k8s%E4%B8%80%E7%9B%91%E6%8E%A7%E6%A1%86%E6%9E%B6%E8%B0%83%E7%A0%94/)
