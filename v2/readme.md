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


## v2
confirmation
kubectl apply -f back-dep.yaml,back-svc.yaml,front-dep.yaml,front-svc.yaml

kubectl get service
    NAME         TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
    frontend     LoadBalancer   10.109.12.3     10.109.12.3   80:30729/TCP   31s
    hello        ClusterIP      10.102.150.60   <none>        80/TCP         31s
    kubernetes   ClusterIP      10.96.0.1       <none>        443/TCP        47h
$ curl 10.109.12.3
    {"message":"Hello"}





kubectl create configmap confnginx --from-file=./front-nginx.conf
kubectl describe configmaps  confnginx
kubectl apply -f back-dep.yaml,back-svc.yaml
    backendを先に作る(helloが必要)

kubectl apply -f front-dep2.yaml
kubectl apply -f front-svc.yaml

$ kubectl get service frontend
    NAME       TYPE           CLUSTER-IP      EXTERNAL-IP     PORT(S)        AGE
    frontend   LoadBalancer   10.97.124.188   10.97.124.188   80:30834/TCP   35s
$ curl 10.97.124.188
    {"message":"Hello"}

