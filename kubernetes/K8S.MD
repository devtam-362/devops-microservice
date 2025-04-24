# Cài đặt istio

```
microk8s enable dns storage istio
microk8s.kubectl wait --for=condition=available deployment --all -n istio-system --timeout=5m
```


# cài dashboard
## Kiểm tra trạng thái MicroK8s
```
microk8s status --wait-ready
```

## Kích hoạt DNS nếu chưa có (Dashboard cần DNS để hoạt động)
```
microk8s enable dns
```

## Kích hoạt addon
```
microk8s enable dashboard
```

## Kiểm tra trạng thái
```
microk8s.kubectl get pods -n kube-system | grep kubernetes-dashboard

microk8s.kubectl wait --for=condition=available deployment --all -n istio-system --timeout=5m

```

