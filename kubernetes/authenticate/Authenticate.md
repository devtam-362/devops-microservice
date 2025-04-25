microk8s kubectl delete -n uat configmap application-config
microk8s kubectl create configmap application-config --from-file=./resources/application.properties -n uat

microk8s kubectl delete -n uat configmap keycloak-config
microk8s kubectl create configmap keycloak-config --from-file=./resources/config/authenticate/KeycloakConfig.json -n uat