## Prometheus + Kube-state-metrics + Grafana监控kubernetes集群说明

### 创建namespace
    创建namespace：kubectl apply -f ./prometheus-server-namespace.yaml

### 部署alertmanager
 * 创建alertmanager-configmap：kubectl apply -f ./alertmanager/alertmanager-config-configmap.yaml
 * 创建alertmanager-dep： kubectl apply -f ./alertmanager/alertmanager-dep.yaml
 * 创建alertmanager-svc： kubectl apply -f ./alertmanager/alertmanager-svc.yaml

### 部署prometheus-server
 * 创建rbac权限：kubectl apply -f ./prometheus-server/prometheus-server-rbac.yaml
 * 创建configmap作为prometheus-server配置文件：kubectl apply -f ./prometheus-server/prometheus-server-config-configmap.yaml
 * 创建config,map作为prometheus-server的rule文件：kubectl apply -f ./prometheus-server/prometheus-server-rule-configmap.yaml
 * 部署prometheus-server-dep：kubectl apply -f ./prometheus-server/prometheus-server-dep.yaml
 * 部署prometheus-server-svc：kubectl apply -f ./prometheus-server/prometheus-server-svc.yaml

### 详情架构

   [http://xianyuluo.com/post/prometheus%E7%9B%91%E6%8E%A7k8s%E4%B8%80%E7%9B%91%E6%8E%A7%E6%A1%86%E6%9E%B6%E8%B0%83%E7%A0%94/](http://xianyuluo.com/post/prometheus%E7%9B%91%E6%8E%A7k8s%E4%B8%80%E7%9B%91%E6%8E%A7%E6%A1%86%E6%9E%B6%E8%B0%83%E7%A0%94/)