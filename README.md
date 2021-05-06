# k8s-prometheus
```shell
# 创建etcd证书
kubectl create secret generic etcd-certs --from-file=/etc/kubernetes/pki/etcd/healthcheck-client.crt --from-file=/etc/kubernetes/pki/etcd/healthcheck-client.key --from-file=/etc/kubernetes/pki/etcd/ca.crt -n kube-system
# node节点上创建prometheus数据目录
mkdir -p /data/prometheus
chown -R 65534:65534 /data/prometheus
# 下载所需yaml
git clone https://github.com/ofriend-jinxin/k8s-prometheus.git
cd k8s-prometheus
# 修改配置
sed -i s"/xxxxxx-xx/k8s-node01/" pv.yaml
sed -i  s"/xx-xx-xx-xx/192.168.101.12/" cg.yaml
# apply
kubectl apply -f kube-stats-metrics
kubectl apply -f .
```
