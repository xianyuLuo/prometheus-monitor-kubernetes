## Prometheus + Kube-state-metrics + Grafana监控kubernetes集群说明

### 创建namespace
 * 创建namespace：kubectl apply -f ./prometheus-server-namespace.yaml

### 部署alertmanager
    需要修改alertmanager/alertmanager-config-configmap.yaml，定义告警方式
 * 创建alertmanager-configmap：kubectl apply -f ./alertmanager/alertmanager-config-configmap.yaml
 * 创建alertmanager-dep： kubectl apply -f ./alertmanager/alertmanager-dep.yaml
 * 创建alertmanager-svc： kubectl apply -f ./alertmanager/alertmanager-svc.yaml

### 部署prometheus-server
    需要修改prometheus-server/prometheus-server-config-configmap.yaml的scrape_configs，定义好prometheus的数据源
 * 创建rbac权限：kubectl apply -f ./prometheus-server/prometheus-server-rbac.yaml
 * 创建configmap作为prometheus-server配置文件：kubectl apply -f ./prometheus-server/prometheus-server-config-configmap.yaml
 * 创建config,map作为prometheus-server的rule文件：kubectl apply -f ./prometheus-server/prometheus-server-rule-configmap.yaml
 * 部署prometheus-server-dep：kubectl apply -f ./prometheus-server/prometheus-server-dep.yaml
 * 部署prometheus-server-svc：kubectl apply -f ./prometheus-server/prometheus-server-svc.yaml
