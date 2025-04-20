1. install secrets

openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt -subj "/CN=auth.localtest.me/O=Keycloak"
kubectl create secret tls auth-tls-secret --cert=path/to/tls.crt --key=path/to/tls.key --namespace=<namespace-của-bạn>

microk8s kubectl apply -f keycloak-prod.yaml