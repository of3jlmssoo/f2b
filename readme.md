https://kubernetes.io/docs/tasks/access-application-cluster/connecting-frontend-backend/

kubectl apply -f back-dep.yaml
kubectl describe deployment backend

kubectl apply -f back-svc.yaml


nginx-conf
Note: The nginx configuration is baked into the container image. A better way to do this would be to use a ConfigMap, so that you can change the configuration more easily.

minikube tunnel --cleanup

kubectl apply -f front-dep.yaml,front-svc.yaml

kubectl get service frontend --watch

curl http://${EXTERNAL_IP} 

