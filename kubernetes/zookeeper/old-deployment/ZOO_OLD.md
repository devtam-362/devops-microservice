**Cài đặt ZooKeeper trên Kubernetes**
=====================================

***Bước 1: Tạo ConfigMap từ file `zoo.cfg`***
------------------------------------------

Tạo một ConfigMap từ file `zoo.cfg` trong thư mục `resources` bằng cách chạy lệnh sau:

```bash
kubectl create configmap zookeeper-config --from-file=resources/zoo.cfg
```

Tạo các Persistent Volume (PV) và Persistent Volume Claim (PVC) bằng cách chạy lệnh sau:
```bash
kubectl apply -f deployment/zookeeper-pv-pvc.yaml
```
Tạo một Deployment và Service bằng cách chạy lệnh sau:
```bash
kubectl apply -f deployment/zookeeper-deployment.yaml
```