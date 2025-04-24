
# Tạo Istio Gateway
```
microk8s.kubectl apply -f dashboard-gateway.yaml
```
# Tạo Istio VirtualService
```
microk8s.kubectl apply -f dashboard-virtualservice.yaml
```
# Xác định Địa chỉ IP của Istio Ingress Gateway
```
microk8s.kubectl get svc istio-ingressgateway -n istio-
```


## Cách 1: Token của ServiceAccount 'default' trong kube-system
```
SECRET_NAME_DEFAULT=$(microk8s.kubectl get secrets -n kube-system | grep default-token | head -n 1 | awk '{print $1}')
if [ -n "$SECRET_NAME_DEFAULT" ]; then
  echo "Default SA Token:"
  microk8s.kubectl describe secret ${SECRET_NAME_DEFAULT} -n kube-system | grep -E '^token' | awk '{print $2}'
else
  echo "Default SA Secret not found, trying to create temporary token..."
  microk8s.kubectl create token default -n kube-system --duration=8h
fi

echo "----- OR -----"
```
## Cách 2: Token của ServiceAccount 'kubernetes-dashboard'
```
SECRET_NAME_DASHBOARD=$(microk8s.kubectl get secrets -n kube-system | grep kubernetes-dashboard-token | head -n 1 | awk '{print $1}')
if [ -n "$SECRET_NAME_DASHBOARD" ]; then
  echo "Dashboard SA Token:"
  microk8s.kubectl describe secret ${SECRET_NAME_DASHBOARD} -n kube-system | grep -E '^token' | awk '{print $2}'
else
  echo "Dashboard SA Secret not found, trying to create temporary token..."
  microk8s.kubectl create token kubernetes-dashboard -n kube-system --duration=8h
fi
```