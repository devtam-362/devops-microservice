```
kubectl create secret generic keycloak-secret \
  --from-literal=KEYCLOAK_ADMIN=admin \
  --from-literal=KEYCLOAK_ADMIN_PASSWORD=admin \
  -n uat
```
```
microk8s kubectl apply -f keycloak-deployment.yaml
```

```
microk8s kubectl apply -f keycloak-service.yaml
```