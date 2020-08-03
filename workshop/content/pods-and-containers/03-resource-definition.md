For more detailed information about the pod, you can run:

```execute
kubectl describe pod blog
```

This combines information from a couple of sources.

The primary source of information is the resource definition in the Kubernetes cluster originally created by running the `kubectl run` command.

A second source of information is the list of events recorded by the Kubernetes cluster related to this workload.

To view the raw resource definition for the pod, you can run:

```execute
kubectl get pod blog -o yaml
```

This provides a lot of detail as when a resource is created, Kubernetes will fill in additional details and will also use it to track the state of the deployment.

To see what the original resource definition was when it was being created, you can re-run the `kubectl run` command, but provide the ``-o yaml --dry-run`` options:

```execute
kubectl run blog --generator=run-pod/v1 --image=quay.io/eduk8s-labs/app-k8s-fundamentals-frontend:latest --port=8080 -o yaml --dry-run
```

The type for the resource is `Pod` and the output should be similar to:

```
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: blog
  name: blog
spec:
  containers:
  - image: quay.io/eduk8s-labs/app-k8s-fundamentals-frontend:latest
    name: blog
    ports:
    - containerPort: 8080
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}
```
