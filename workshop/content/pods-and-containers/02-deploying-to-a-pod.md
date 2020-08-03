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

If this is the first time the container image has been used in a deployment to a node in the Kubernetes cluster, it may take longer to start up the pod as it will be necessary to pull the container image down from the remote image registry. During this time the status for the pod will show `ContainerCreating`. Once the deployment has completed, the status will show as `Running`.

Additional fields including the IP address for the pod, and the name of the node on which the pod is running, can be viewed by running:

```execute
kubectl get pod blog -o wide
```

This will generate output similar to:

```
NAME   READY   STATUS    RESTARTS   AGE   IP            NODE       NOMINATED NODE   READINESS GATES
blog   1/1     Running   0          30s   172.17.0.10   minikube   <none>           <none>
```

To extract just the IP address for the pod, you can run:

{% raw %}
```execute
kubectl get pod blog -o template --template {{.status.podIP}}
```
{% endraw %}

This IP address is only accessible from within the Kubernetes cluster.

As this workshop environment is running inside of the same Kubernetes cluster as the pod is deployed, you can verify access to the application using the IP address by running:

{% raw %}
```execute
curl http://`kubectl get pod blog -o template --template {{.status.podIP}}`:8080
```
{% endraw %}
