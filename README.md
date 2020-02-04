# k8s_example

- Docker Desktop - Preferences - Kubernetes - Enable Kubernetes - On

- kubectl cluster-info
```
Kubernetes master is running at https://kubernetes.docker.internal:6443
KubeDNS is running at https://kubernetes.docker.internal:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
local:k8s_example $

```

- kubectl apply -f pod.yaml
```
pod/nginx created
```

- kubectl get pods
```
NAME    READY   STATUS    RESTARTS   AGE
nginx   1/1     Running   0          2m5s
```

- kubectl apply -f deployment.yaml
```
deployment.apps/nginx-deployment created
```

- kubectl get pods
```
NAME                                READY   STATUS    RESTARTS   AGE
nginx                               1/1     Running   0          7m26s
nginx-deployment-554d546bdd-7j59q   1/1     Running   0          81s
nginx-deployment-554d546bdd-pm7b5   1/1     Running   0          81s
nginx-deployment-554d546bdd-vh6kx   1/1     Running   0          81s
```
- kubectl apply -f service.yaml
```
service/nginx-service created
```

- kubectl get service
```
NAME            TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
kubernetes      ClusterIP      10.96.0.1       <none>        443/TCP          52m
nginx-service   LoadBalancer   10.98.255.210   localhost     8080:31408/TCP   41s
```
- curl http://localhost:8080/

- kubectl delete pod nginx
```
pod "nginx" deleted
```
- kubectl get pods
```
NAME                                READY   STATUS    RESTARTS   AGE
nginx-deployment-554d546bdd-7j59q   1/1     Running   0          57m
nginx-deployment-554d546bdd-pm7b5   1/1     Running   0          57m
nginx-deployment-554d546bdd-vh6kx   1/1     Running   0          57m
```

- kubectl delete deployment nginx-deployment
```
deployment.extensions "nginx-deployment" deleted
```

- kubectl get pods
```
No resources found.
```

クラスタ
マニュフェスト:
  リソース
    Pod:1つ以上のコンテナ
      コンテナ
    Deployment
    Service
Cluster IP
External IP

オブジェクト
