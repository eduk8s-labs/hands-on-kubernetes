To deploy an application to Kubernetes the application must be packaged up as a container image. The container image must be hosted on an image registry which is accessible from the Kubernetes cluster.

To launch an application on Kubernetes from a container image you can use the `kubectl run` command:

```execute
kubectl run blog --generator=run-pod/v1 --image=quay.io/eduk8s-labs/app-k8s-fundamentals-frontend:latest --port=8080
```

To verify that the `pod` for the application is running, run:

```execute
kubectl get pod blog
```

This will generate output similar to:

```
NAME   READY   STATUS    RESTARTS   AGE
blog   1/1     Running   0          5s
```

Additional fields providing the IP address for the pod, and the name of the node on which the pod is running can be viewed by running:

```execute
kubectl get pod blog -o wide
```

This will generate output similar to:

```
NAME   READY   STATUS    RESTARTS   AGE   IP            NODE       NOMINATED NODE   READINESS GATES
blog   1/1     Running   0          30s   172.17.0.10   minikube   <none>           <none>
```

For even more detailed information about the pod, you can run:

```execute
kubectl describe pod blog
```
