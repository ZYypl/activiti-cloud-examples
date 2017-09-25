## Kubernetes option

Steps to run:

First install minikube - https://github.com/kubernetes/minikube
Go to this directory.
minikube start
minikube dashboard
kubectl create -f infrastructure.yml
kubectl create -f runtime-bundle.yml (but get infrastructure running first)

To find entrypoint IP look at the dashboard IP or do 'minikube service entrypoint'. Use this IP and port 30080 in Postman and demo-ui-client for all gateway URLs (i.e. all but SSO).

The IP from the minikube service entrypoint should be added in the etc/hosts file as mapped to activiti-cloud-sso-idm-kub.

For SSO also change activiti-cloud-sso-idm to activiti-cloud-sso-idm-kub and port from 8180 to 30081 in keycloak.json in the demo UI client.

To stop infra do kubectl delete -f infrastructure.yml

To use a locally-built version of an image set imagePullPolicy: Never in yml file and run eval $(minikube docker-env) before building. Note minikube docker deamon may be different version so builds within it may not work the same.