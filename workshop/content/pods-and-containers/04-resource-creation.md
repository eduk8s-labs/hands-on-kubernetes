Instead of using the `kubectl run` command, you could instead have started with the raw resource definition and applied it to the cluster to create the deployment.

To illustrate this process, first delete the existing pod deployment by running:

```execute
kubectl delete pod blog
```

Now run the `kubectl run -o yaml --dry-run` command to generate a file containing the raw resource definition.

```execute
kubectl run blog --generator=run-pod/v1 --image=quay.io/eduk8s-labs/app-k8s-fundamentals-frontend:latest --port=8080 -o yaml --dry-run > pod.yaml
```

Verify the contents of the resource file by running:

```execute
cat pod.yaml
```

To create the pod from the raw resource definition, rather than using `kubectl run`, you can use:

```execute
kubectl apply -f pod.yaml
```

Verify the pod was once again created by running:

```execute
kubectl get pod blog
```
