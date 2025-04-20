microk8s.kubectl create secret generic mysql-secret \
  --from-literal=MYSQL_ROOT_PASSWORD='33066033' \
  --from-literal=MYSQL_USER=keycloak \
  --from-literal=MYSQL_PASSWORD='33066033' \
  --from-literal=MYSQL_DATABASE=keycloak \
  -n uat

microk8s.kubectl apply -f mysql-pvc.yaml

microk8s.kubectl apply -f mysql-deployment.yaml

microk8s.kubectl apply -f mysql-service.yaml