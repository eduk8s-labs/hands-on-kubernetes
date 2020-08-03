By default a pod has a restart policy of `Always`. This means that if for some reason the application were to crash, or otherwise exit, the application container would be restarted automatically.

To see this process in action run the command:

```execute-1
kubectl get pods -w
```

This sets up a watcher on the state of pods in the namespace.

In the other terminal now run:

```execute-2
kubectl exec blog -- kill 1
```

Although a pod ensures the application keeps running, it doesn't by provide any assistance when it comes to scaling up an application to multiple instances. To do this, you would need to create a new pod by way of a separate pod rsource definition, with different name.
