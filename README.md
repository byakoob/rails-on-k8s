# README

This is an application that always responds with “hello world” to ANY web requests. Basic Documentation here at <a href="https://guides.rubyonrails.org/getting_started.html" target="_blank">Getting Started with Rails!</a>


### How To Test with Docker:

    - $docker build -t <docker_id>/<REPOSITORY>:<TAG> .

    - $docker run -p 3000:3000 <docker_id>/<REPOSITORY>:<TAG>

    - You can now see your website by visiting http://localhost:3000.

### How to Test with Kubernetes:
This assumes you are using minikube or you have a cluster to deploy the manifests. 

```
kubectl apply -f k8s/deployment.yaml
deployment.apps/hello configured

kubectl apply -f k8s/service.yaml 
service/rails-app-service created

⇒ kubectl get deploy
NAME    READY   UP-TO-DATE   AVAILABLE   AGE
hello   2/2     2            2           12s

⇒ kubectl get svc
NAME                TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
kubernetes          ClusterIP   10.96.0.1       <none>        443/TCP    22m
rails-app-service   ClusterIP   10.103.159.58   <none>        3000/TCP   10s

```

Now we can <a href="https://kubernetes.io/docs/tasks/access-application-cluster/port-forward-access-application-cluster/" target="_blank">Use Port Forwarding to Access Applications in a Cluster!</a>:

 

```
kubectl port-forward service/rails-app-service 3000:3000
Forwarding from 127.0.0.1:3000 -> 3000
Forwarding from [::1]:3000 -> 3000
Handling connection for 3000

```

View our rails app through the browser. 

http://localhost:3000

http://localhost:3000/xyzs
